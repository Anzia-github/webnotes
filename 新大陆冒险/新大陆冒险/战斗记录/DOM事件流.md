- 事件流
	- 代码
		- ```HTML
			<body>
			    <div>
			        <button>点击这里</button>
			    </div>
			</body>
	- 流程
		- 先[[事件捕获]]后[[事件冒泡]]
		- body -> div -> button -> button -> div -> body
- 事件监听函数
	- `[Object].addEventListener("name_of_event", fnHandler, bCapture); //绑定函数`
	- `[Object].removeEventListener("name_of_event", fnHandler, bCapture); //移除绑定`