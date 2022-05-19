- 让当前[[viewport]]的宽度等于设备的宽度，同时不允许用户手动缩放
- 原理
	- 移动端浏览器通常会在一个比移动端屏幕更宽的虚拟窗口中渲染页面
	- 这个虚拟窗口就是viewport
	- 目的是正常展示没有做移动端适配的页面，完整的展示给用户
- 在移动端浏览器中
	- 两种视口
		- 可见视口（设备大小）
		- 视窗视口（网页的宽度）
	- 一般来说
		- 视窗视口 > 可见视口
>`<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- [[viewport]]属性值
![[Pasted image 20220414111431.png]]
