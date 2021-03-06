- 含义
	- 调用一个对象的方法
	- 用另一个对象替换当前对象
	- 例如
		- B. apply(A, arguments); 即 A 对象应用 B 对象的方法
- 特点
	- 只能传入两个参数
	- 第二个参数以数组的方式传入
- 实现步骤
	- 判断调用对象是否为函数，即使我们是定义在函数的原型上的，但是可能出现使用 call 等方式调用的情况。
	- 判断传入上下文对象是否存在，如果不存在，则设置为 window 。
	- 将函数作为上下文对象的一个属性。
	- 判断参数值是否传入
	- 使用上下文对象来调用这个方法，并保存返回结果。
	- 删除刚才新增的属性
	- 返回结果
- 手写实现
	```JS
	Function.prototype.myApply = function(context) {
	    // 判断调用对象是否为函数
	    if (typeof this !== "function") {
	        throw new TypeError("Error");
	    }
	    let result = null;
	    // 判断 context 是否存在，如果未传入则为 window
	    context = context || window;
	    // 将函数设为对象的方法
	    context.fn = this;
	    // 调用方法
	    if (arguments[1]) {
	        result = context.fn(...arguments[1]);
	    } else {
	        result = context.fn();
	    }
	    // 将属性删除
	    delete context.fn;
	    return result;
	};
	```