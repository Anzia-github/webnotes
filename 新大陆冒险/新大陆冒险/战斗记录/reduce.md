- 含义
	- 接受一个函数作为累加器
	- 数组中的每个值（从左到右）开始缩减
	- 最终计算为一个值
- 参数
	- 回调函数
	- 传给total的初始值
- 例子
	- 求数组的和
	```JS
	arr.reduce((total, item) => {
		return total + item
	}, 0)
	```