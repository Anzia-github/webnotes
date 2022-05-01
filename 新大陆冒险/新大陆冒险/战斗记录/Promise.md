- 含义
	- 是异步编程的一种解决方案
	- [[Promise]]是一个[[构造函数]]，接收一个函数作为参数，返回一个[[Promise]]实例
- 状态
	- [[pending]]
		- 进行中
	- [[resolved]]
		- 已成功
	- [[rejected]]
		- 已失败
- 特点
	- 实例的状态只能由[[pending]]转变[[resolved]]或者[[rejected]]状态，并且状态一经改变，就凝固了，无法再被改变了
	- 状态的改变是通过resolve()和reject()函数来实现的，我们可以在异步操作结束后调用这两个函数改变[[Promise]]实例的状态
	- 它的原型上定义了一个then方法，使用这个then方法可以为两个状态的改变注册[[回调函数]]
	- 这个回调函数属于[[微任务]]，会在本轮[[事件循环]]的末尾执行
- 手写代码
	```JS
	const PENDING = "pending";
	const RESOLVED = "resolved";
	const REJECTED = "rejected";
	function MyPromise(fn) {
	    // 保存初始化状态
	    var self = this;
	    // 初始化状态
	    this.state = PENDING;
	    // 用于保存 resolve 或者 rejected 传入的值
	    this.value = null;
	    // 用于保存 resolve 的回调函数
	    this.resolvedCallbacks = [];
	    // 用于保存 reject 的回调函数
	    this.rejectedCallbacks = [];
	    // 状态转变为 resolved 方法
	    function resolve(value) {
	        // 判断传入元素是否为 Promise 值，如果是，则状态改变必须等待前一个状态改变后再进行改变
	        if (value instanceof MyPromise) {
	            return value.then(resolve, reject);
	        }
	        // 保证代码的执行顺序为本轮事件循环的末尾
	        setTimeout(() => {
	            // 只有状态为 pending 时才能转变，
	            if (self.state === PENDING) {
	                // 修改状态
	                self.state = RESOLVED;
	                // 设置传入的值
	                self.value = value;
	                // 执行回调函数
	                self.resolvedCallbacks.forEach(callback => {
	                    callback(value);
	                });
	            }
	        }, 0);
	    }
	    // 状态转变为 rejected 方法
	    function reject(value) {
	        // 保证代码的执行顺序为本轮事件循环的末尾
	        setTimeout(() => {
	            // 只有状态为 pending 时才能转变
	            if (self.state === PENDING) {
	                // 修改状态
	                self.state = REJECTED;
	                // 设置传入的值
	                self.value = value;
	                // 执行回调函数
	                self.rejectedCallbacks.forEach(callback => {
	                    callback(value);
	                });
	            }
	        }, 0);
	    }
	    // 将两个方法传入函数执行
	    try {
	        fn(resolve, reject);
	    } catch (e) {
	        // 遇到错误时，捕获错误，执行 reject 函数
	        reject(e);
	    }
	}
	MyPromise.prototype.then = function(onResolved, onRejected) {
	    // 首先判断两个参数是否为函数类型，因为这两个参数是可选参数
	    onResolved =
	        typeof onResolved === "function" ?
	        onResolved :
	        function(value) {
	            return value;
	        };
	    onRejected =
	        typeof onRejected === "function" ?
	        onRejected :
	        function(error) {
	            throw error;
	        };
	    // 如果是等待状态，则将函数加入对应列表中
	    if (this.state === PENDING) {
	        this.resolvedCallbacks.push(onResolved);
	        this.rejectedCallbacks.push(onRejected);
	    }
	    // 如果状态已经凝固，则直接执行对应状态的函数
	    if (this.state === RESOLVED) {
	        onResolved(this.value);
	    }
	    if (this.state === REJECTED) {
	        onRejected(this.value);
	    }
	};
	```