- [[typeof]]
	- 返回一个表示数据类型的字符串
	- 返回结果
		- [[Number]]
		- [[Boolean]]
		- [[String]]
		- [[Object]]
		- undefined
		- [[Function]]
	- 如果是判断一个基本的类型用[[typeof]]就可以了
		- ![[Pasted image 20220427183318.png]]
- [[instanceof]]
	- 判断A是否为B的实例
	- [[instanceof]]检测的是[[原型]]
	- ```JS
	   [] instanceof Array; //true
	   {} instanceof Object; //true
	   new Date() instanceof Date; //true
- [[constructor]]
	- 每一个对象实例都可以通过[[constructor]]对象来访问它的[[构造函数]]
	- 可以通过数据的[[constructor]]是否与其[[构造函数]]相等来判断数据的类型
	- ![[Pasted image 20220427183938.png]]
- [[prototype]]
	- toString是[[Object]]原型对象上的一个方法
	- 该方法默认返回其调用者的具体类型
	- 是toString运行时[[this]]指向的对象类型
	- 基本上所有对象的类型都可以通过这个方法获取到
	- ![[Pasted image 20220427184310.png]]