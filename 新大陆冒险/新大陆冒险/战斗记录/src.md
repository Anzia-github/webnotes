1. 引用资源，替换当前元素
2. 元素
	- [[img]]
	- [[script]]
	- [[iframe]]
3. 浏览器解析到[[src]]，会暂停其他资源的下载和处理（图片不会），知道将该资源加载、编译、执行完毕
4. 建议把JS脚本放在底部而不是头部的原因