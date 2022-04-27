- ![[Pasted image 20220427152605.png]]
- new一个对象的四个过程
	1. 创建空对象
		- `var obj = {}`
	2. 设置[[原型链]]
	    - 设置新对象的[[constructor]]属性为[[构造函数]]的名称
		    - `obj.constructor = Person`
		- 设置新对象的[[__proto__]]属性指向[[构造函数]]的[[prototype]]对象
			- `obj.__proto__ = Person.prototype`
	1. 改变[[this]]指向
	    - 使用新对象调用函数，函数中的[[this]]指向新实例对象obj
		    - `var result = Person.call(obj)`
	1. 返回值
	    - 如果返回值或者返回一个非对象值，则将新对象返回
	    - 如果返回值是一个新对象的话那么直接返回该对象
	    - ![[Pasted image 20220427182129.png]]