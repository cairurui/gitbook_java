### Session技术核心

HttpSession类：用于保存会话数据

* 1）创建或得到session对象

	* HttpSession getSession()  
	* HttpSession getSession(boolean create)  
	
	
* 2）设置session对象

	* void setMaxInactiveInterval(int interval)  ： 设置session的有效时间
	* void invalidate()     ： 销毁session对象
	* java.lang.String getId()  ： 得到session编号
	
	
* 3）保存会话数据到session对象

	* void setAttribute(String name, Object value)  ： 保存数据
	* Object getAttribute(String name)  ： 获取数据
	* void removeAttribute(String name) ： 清除数据
	
4.3 Session原理

	问题： 服务器能够识别不同的浏览者！！！
	
	
  前提： 在哪个session域对象保存数据，就必须从哪个域对象取出！！！！
  
	浏览器1：(给s1分配一个唯一的标记：s001,把s001发送给浏览器)
		1）创建session对象，保存会话数据
			HttpSession session = request.getSession();   --保存会话数据 s1
	浏览器1	的新窗口（带着s001的标记到服务器查询，s001->s1,返回s1）	
		1）得到session对象的会话数据
			HttpSession session = request.getSession();   --可以取出  s1

	新的浏览器1：(没有带s001,不能返回s1)
		1）得到session对象的会话数据
			HttpSession session = request.getSession();   --不可以取出  s2

	浏览器2：(没有带s001,不能返回s1)
		1）得到session对象的会话数据
			HttpSession session = request.getSession();  --不可以取出  s3

		
代码解读：
HttpSession session = request.getSession();
			
* 1）第一次访问创建session对象，给session对象分配一个唯一的ID，叫JSESSIONID
	
		new HttpSession();
	
* 2）把JSESSIONID作为Cookie的值发送给浏览器保存

		Cookie cookie = new Cookie("JSESSIONID", sessionID);
				response.addCookie(cookie);
				
* 3）第二次访问的时候，浏览器带着JSESSIONID的cookie访问服务器

* 4）服务器得到JSESSIONID，在服务器的内存中搜索是否存放对应编号的session对象。

		if(找到){
			return map.get(sessionID);
		}
		Map<String,HttpSession>]
		
		<"s001", s1>
		<"s001,"s2>
	

* 5）如果找到对应编号的session对象，直接返回该对象
* 6）如果找不到对应编号的session对象，创建新的session对象，继续走1的流程


** 结论：通过JSESSION的cookie值在服务器找session对象！！！！！ **
	
	
	
	
	
	
	
	
	
	