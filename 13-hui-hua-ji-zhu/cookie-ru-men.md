
* Cookie技术：会话数据保存在浏览器客户端。

* Session技术：会话数据保存在服务器端。

---
### Cookie类：用于存储会话数据

* 1）构造Cookie对象

    Cookie(java.lang.String name, java.lang.String value)
    
* 2）设置cookie

    void setPath(java.lang.String uri)   ：设置cookie的有效访问路径
    void setMaxAge(int expiry) ： 设置cookie的有效时间
    void setValue(java.lang.String newValue) ：设置cookie的值
    
* 3）发送cookie到浏览器端保存

    void response.addCookie(Cookie cookie)  : 发送cookie
    
* 4）服务器接收cookie
    
    Cookie[] request.getCookies()  : 接收cookie


* 5）例子

```
	public void doGet(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		Cookie cookie = new Cookie("name", "xiaocai");
		Cookie cookie2 = new Cookie("age", "25");
		response.addCookie(cookie);
		response.addCookie(cookie2);
	}

    响应头信息：
    Content-Length:0
    Date:Mon, 01 May 2017 15:54:57 GMT
    Server:Apache-Coyote/1.1
    Set-Cookie:name=xiaocai
    Set-Cookie:age=25
```

---

获取

```
    Cookie[] cookies = request.getCookies();
    for (int i = 0; i < cookies.length; i++) {
    	Cookie cookie = cookies[i];
    	String name = cookie.getName();
    	String value = cookie.getValue();
    	System.out.println("name:" + name + "  value:" + value);
    }

    输出信息:
    name:name  value:xiaocai
    name:age  value:25

```