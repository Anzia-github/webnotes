- 用法
```JS
fetch("https://jsonplaceholder.typicode.com/posts/1")
	.then((res) => console.log(res))
	.then(() => {...})
	.then(() => {...})
	.catch(err => console.log(err))
```
- 结果是返回一个[[Promise]]对象
- ![[Pasted image 20220520112553.png]]