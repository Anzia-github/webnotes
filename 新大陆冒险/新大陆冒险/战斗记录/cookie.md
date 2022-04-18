- 定义
  - 字符串类型的键值对
  - 是网站为了标识用户身份而存储在用户本地终端上的数据
  - 始终在[[同源]]的[[HTTP]]请求中携带
  - 会在浏览器和服务器间来回传递
- 存储大小
  - 4k
- 过期时间
  - 在设置的[[cookie]]时间之前一直有效
  - 即使窗口和浏览器关闭
- 作用域
  - 在所有[[同源]]窗口中都是共享的
- 步骤
  - ![[Pasted image 20220416171542.png]]
- 属性项
  - ![[Pasted image 20220416171725.png]]
- Expires
  - maxAge有3种值
    - 正数
      - 设置值为时长的生命周期，永久有效
    - 负数
      - 时间过期
    - 零
      - 删除[[cookie]]
  - 代码
    - ```JavaScript
      Cookie cookie = new Cookie("mcrwayfun",System.currentTimeMillis()+"");
      // 设置生命周期为MAX_VALUE，永久有效
      cookie.setMaxAge(Integer.MAX_VALUE);
      resp.addCookie(cookie);```
- 修改和删除[[cookie]]
  - 新建一个[[cookie]]覆盖原来的
  - name、path、domain必须和原来相同
  - value、maxAge可以不相同
- 如何在不同的端口间共享[[cookie]]
	- 根据[[同源]]策略
		- [[cookie]]是区分端口的
	- 浏览器实现
		- [[cookie]]区分域，不区分端口
		- 同一个ip下的多个端口下的[[cookie]]是共享的