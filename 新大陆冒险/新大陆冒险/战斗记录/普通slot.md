- 含义
	- 是渲染后做替换的工作
	- 父组件渲染完毕后，替换子组件的内容
- 过程
	- 定义[[slot]]组件
		- ![[d5d2edbc5b6145349d6ccecd01cb7a82_tplv-k3u1fbpfcp-zoom-in-crop-mark_1304_0_0_0.webp]]
	- 在模板编译的时候，处理组件中的子节点和[[slot]]标签
		- ![[508c06da3cea4e2cbb2271a565bbcedc_tplv-k3u1fbpfcp-zoom-in-crop-mark_1304_0_0_0.webp]]
	- 在创建元素的时候，用_t()方法方法来替换_v()的内容
		- ![[8acfee0c25a34b23a991fe9b85164394_tplv-k3u1fbpfcp-zoom-in-crop-mark_1304_0_0_0.webp]]