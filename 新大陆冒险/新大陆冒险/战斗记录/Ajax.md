- 含义
	- [[JavaScript]]的异步通信
- 步骤
	- 创建XMLHttpRequest对象，也就是创建一个异步调用对象
	- 创建一个新的[[HTTP]]请求，并指定该[[HTTP]]请求的方法，URL及验证信息
	- 设置响应[[HTTP]]请求状态变化的函数
	- 发送[[HTTP]]请求
	- 获取异步调用返回的数据
	- 使用[[JavaScript]]和[[DOM]]实现局部刷新
- 代码
	- ```JS
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
