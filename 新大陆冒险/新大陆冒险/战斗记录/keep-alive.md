- \<keep-alive\>
- 含义
	- 是一个抽象组件
	- 自身不会渲染一个[[DOM]]元素
	- 也不会出现在父组件链中
- 使用[[keep-alive]]包裹动态组件时
	- 会缓存不活动的组件实例
	- 而不会销毁
- 用法
	- 在动态组件中应用
	```vue
	<keep-alive :include="whiteList" :exclude="blackList" :max="amount">
		<component :is="currentComponent"></component>
	</keep-alive>
	```
	- 在vue-router中应用
	```vue
	<keep-alive :include="whiteList" :exclude="blackList" :max="amount">
	  <router-view></router-view>
	</keep-alive>
	```
- include
	- 定义缓存白名单
- exclude
	- 定义缓存黑名单