- 含义
	- [[ES6]]中新增的一个特性
	- 在模板对象之前架设一层拦截
	- 外部所有的访问都必须先通过这层拦截
- 优点
	- 监听整个对象/数组，返回整个对象/数组
	- 还可以代理动态增加的属性
	- 和[[Object.defineProperty()]]相比，不需要预先劫持属性
- 例子
	```JS
	var obj = new Proxy({}, {
	  get: function (target, key, receiver) {
	    console.log(`getting ${key}!`);
	    return Reflect.get(target, key, receiver);
	  },
	  set: function (target, key, value, receiver) {
	    console.log(`setting ${key}!`);
	    return Reflect.set(target, key, value, receiver);
	  }
	});
	```
![[Pasted image 20220518103351.png]]
- 支持拦截的操作，13种
	- get(target, propKey, receiver)
		- 拦截对象属性的读取，比如proxy.foo和proxy\['foo']
	- set(target, propKey, value, receiver)
		- 拦截对象属性的设置，比如proxy.foo = v或proxy\['foo'] = v，返回一个布尔值
	- has(target, propKey)
		- 拦截propKey in proxy的操作，返回一个布尔值
	- deleteProperty(target, propKey)
		- 拦截delete proxy\[propKey]的操作，返回一个布尔值
	- ownKeys(target)
		- 拦截Object.getOwnPropertyNames(proxy)、Object.getOwnPropertySymbols(proxy)、Object.keys(proxy)、for...in循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而Object.keys()的返回结果仅包括目标对象自身的可遍历属性
	- getOwnPropertyDescriptor(target, propKey)
		- 拦截Object.getOwnPropertyDescriptor(proxy, propKey)，返回属性的描述对象。
	- defineProperty(target, propKey, propDesc)
		- 拦截Object.defineProperty(proxy, propKey, propDesc）、Object.defineProperties(proxy, propDescs)，返回一个布尔值
	- preventExtensions(target)
		- 拦截Object.preventExtensions(proxy)，返回一个布尔值
	- getPrototypeOf(target)
		- 拦截Object.getPrototypeOf(proxy)，返回一个对象
	- isExtensible(target)
		- 拦截Object.isExtensible(proxy)，返回一个布尔值
	- setPrototypeOf(target, proto)
		- 拦截Object.setPrototypeOf(proxy, proto)，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截
	- apply(target, object, args)
		- 拦截 Proxy 实例作为函数调用的操作，比如proxy(...args)、proxy.call(object, ...args)、proxy.apply(...)
	- construct(target, args)
		- 拦截 Proxy 实例作为构造函数调用的操作，比如new proxy(...args)