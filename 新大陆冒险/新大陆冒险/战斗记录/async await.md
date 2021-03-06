- [[async]]返回一个[[Promise]]对象，可以使用then方法添加回调函数
- [[async]]函数执行时，如果遇到[[await]]就会先暂停执行
	- 等到触发的异步操作完成后，恢复[[async]]函数的执行并返回解析值
- [[await]]关键字值在[[async]]函数内有效，否则会报错
- [[await]]针对不同表达式的处理方式
	- Promise 对象
		- await 会暂停执行，等待 Promise 对象 resolve
		- 然后恢复 async 函数的执行并返回解析值
	- 非 Promise 对象
		- 直接返回对应的值
- [[await]]原理
	- [[Promise]]
	- [[事件循环]]
- 用法
	- 使用[[async]]标记函数为[[异步]]函数
	- 使用[[await]]定义[[异步操作]]，获得操作后的结果
		- 就是省略了then操作
- 错误用法
	- 多个[[await]]会打破[[Fetch]]的并行
		- 正确操作
			- 对[[Promise]].all使用[[await]]
			- ![[Pasted image 20220521005335.png]]
	- 在[[forEach]]和map中使用[[await]]
		- 这样结果会立即返回，不会暂停等到所有[[异步]]操作都执行完毕
		- 正确操作
			- 使用普通的for
			- 使用for await
				- ![[Pasted image 20220521005409.png]]
- 没有[[await]]就没法获取结果了，除非这里面使用then