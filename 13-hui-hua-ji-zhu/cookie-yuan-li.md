### Cookie原理

* 1）服务器创建cookie对象，把会话数据存储到cookie对象中。

	new Cookie("name","value");
	
* 2）	服务器发送cookie信息到浏览器

	response.addCookie(cookie);

	举例： set-cookie: name=xiaocai  (隐藏发送了一个set-cookie名称的响应头)
	
* 3）浏览器得到服务器发送的cookie，然后保存在浏览器端。

* 4）浏览器在下次访问服务器时，会带着cookie信息

	举例： cookie: name=xiaocai  (隐藏带着一个叫cookie名称的请求头)
* 5）服务器接收到浏览器带来的cookie信息

	request.getCookies();
