- 含义
	- [[JavaScript]]的异步通信
- 步骤
	- 创建XMLHttpRequest对象，也就是创建一个异步调用对象
	- 创建一个新的[[HTTP]]请求，并指定该[[HTTP]]请求的方法，URL及验证信息
	- 设置响应[[HTTP]]请求状态变化的函数
	- 发送[[HTTP]]请求
	- 获取异步调用返回的数据
	- 使用[[JavaScript]]和[[DOM]]实现局部刷新
- 简洁步骤
	- 创建对象
	- 连接对象
	- 发送数据
	- 接受数据
- readyState的五种含义
	- 0
		- 未初始化
		- 还没有调用send()方法
	- 1
		- 载入
		- 已调用send()方法，正在发送请求
	- 2
		- 载入完成
		- send()方法执行完成，已经接受到全部响应内容
	- 3
		- 交互
		- 正在解析响应内容
	- 4
		- 完成
		- 响应内容解析完成，可以在客户端调用了
- 代码
	```JS
	const SERVER_URL = "/server";
	let xhr = new XMLHttpRequest();
	// 创建 Http 请求
	xhr.open("GET", SERVER_URL, true);
	// 设置状态监听函数
	xhr.onreadystatechange = function() {
		if (this.readyState !== 4) return;
		// 当请求成功时
		if (this.status === 200) {
			handle(this.response);
		} else {
			console.error(this.statusText);
		}
	};
	// 设置请求失败时的监听函数
	xhr.onerror = function() {
		console.error(this.statusText);
	};
	// 设置请求头信息
	xhr.responseType = "json";
	xhr.setRequestHeader("Accept", "application/json");
	// 发送 Http 请求
	xhr.send(null);
	```
	
	```JS
	// promise 封装实现：
	function getJSON(url) {
		// 创建一个 promise 对象
		let promise = new Promise(function(resolve, reject) {
			let xhr = new XMLHttpRequest();
			// 新建一个 http 请求
			xhr.open("GET", url, true);
			// 设置状态的监听函数
			xhr.onreadystatechange = function() {
				if (this.readyState !== 4) return;
				// 当请求成功或失败时，改变 promise 的状态
				if (this.status === 200) {
					resolve(this.response);
				} else {
					reject(new Error(this.statusText));
				}
			};
			// 设置错误监听函数
			xhr.onerror = function() {
				reject(new Error(this.statusText));
			};
			// 设置响应的数据类型
			xhr.responseType = "json";
			// 设置请求头信息
			xhr.setRequestHeader("Accept", "application/json");
			// 发送 http 请求
			xhr.send(null);
		});
		return promise;
	}
	```
- 优点
	- 页面无刷新更新数据
	- 异步与服务器通信
	- 前端和后端负载均衡
	- 基于标准被广泛支持
	- 界面与应用分离
- 缺点
	- 干到了Back和History功能
	- 安全问题
		- [[XSS攻击]]
		- SQL注入
	- [[SEO]]较弱
	- 破话程序的异常处理机制
	- 违背URL和资源定位符的初衷
		- 在该URL地址下面看到的和我在这个URL地址下看到的内容是不同的
		- 这个和资源定位的初衷是相背离的
	- 不是很好支持移动设备
	- 客户端变得臃肿
	- 用户禁用了[[JS]]就无法获得数据