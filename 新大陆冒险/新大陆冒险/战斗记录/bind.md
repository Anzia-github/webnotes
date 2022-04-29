- 含义
	- 改变[[this]]指向
	- 不过不是在调用时生效
	- 而是返回一个新函数
- 例子
	- ```JS
	  let name = 'Jack'
	  const obj = {name: 'Tom'}
	  function sayHi() {console.log('Hi! ' + this.name)}
	  
	  const newFunc = sayHi.bind(obj)
	  newFunc() // Hi! Tom