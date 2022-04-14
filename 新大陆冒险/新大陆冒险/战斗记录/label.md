1. [[label]]是用来定义表单控制间关系的
2. 用户选择[[label]]标签时，浏览器会自动将焦点转到和[[label]]相关的表单控件上
3. 有两种绑定方式
	1. id绑定 `<label for='name'>Number:</label> <input id='name' type='text'/>`
	2. 嵌套绑定 `<label><input type='text'/></label>`