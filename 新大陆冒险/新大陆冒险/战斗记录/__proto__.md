- 隐式原型
- 在对象上找不到的话，就会去[[__proto__]]隐式原型上找
- 所有的对象都拥有[[__proto__]]属性
- 它指向对象构造函数的[[prototype]]属性
	```JS
	let obj = {}
	obj.__proto__ === Object.prototype // true
	
	function Test(){}
	var test = new Test()
	test.__proto__ == Test.prototype // true
	```
- 所有的函数都同时拥有[[__proto__]]和[[prototype]]属性
- 函数的[[__proto__]]指向自己的函数实现
- 函数的[[prototype]]是一个对象
- 所有函数的[[prototype]]也有[[__proto__]]，指向[[Object]].[[prototype]]
	```JS
	function func() {}
	func.prototype.__proto__ === Object.prototype // true
	```
- [[Object]].[[prototype]].[[__proto__]]指向null
	```JS
	Object.prototype.__proto__ // null
	```
- ![[Pasted image 20220509101248.png]]