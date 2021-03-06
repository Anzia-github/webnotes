- 含义
	- 改变[[this]]指向
	- 不过不是在调用时生效
	- 而是返回一个新函数
- 例子
	```JS
	  let name = 'Jack'
	  const obj = {name: 'Tom'}
	  function sayHi() {console.log('Hi! ' + this.name)}
	  
	  const newFunc = sayHi.bind(obj)
	  newFunc() // Hi! Tom
	```
- 实现步骤
	- 判断调用对象是否为函数，即使我们是定义在函数的原型上的，但是可能出现使用 call 等方式调用的情况
	- 保存当前函数的引用，获取其余传入参数值
	- 创建一个函数返回
	- 函数内部使用 apply 来绑定函数调用，需要判断函数作为构造函数的情况，这个时候需要传入当前函数的 this 给 apply 调用，其余情况都传入指定的上下文对象
- 手写实现
	```JS
		Function.prototype.myBind = function(context) {
	    // 判断调用对象是否为函数
	    if (typeof this !== "function") {
	        throw new TypeError("Error");
	    }
	    // 获取参数
	    var args = [...arguments].slice(1),
	        fn = this;
	    return function Fn() {
	        // 根据调用方式，传入不同绑定值
	        return fn.apply(
	            this instanceof Fn ? this : context,
	            args.concat(...arguments)
	        );
	    };
	};
	```