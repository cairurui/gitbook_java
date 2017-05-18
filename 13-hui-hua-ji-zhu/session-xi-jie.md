4.4 Sesson细节

* 1）String getId()  ： 得到session编号 (相当于key)

* 2）两个getSession方法：

	* getSession(true) / getSession()  : 创建或得到session对象。没有匹配的session编号，自动创												建新的session对象。
	* getSession(false):              得到session对象。没有匹配的session编号，返回null
	

* 3）void setMaxInactiveInterval(int interval)  ： 设置session的有效时间
	* session对象销毁时间：
	
			3.1 默认情况30分服务器自动回收
			3.2 修改session回收时间
			3.3 全局修改session有效时间
			
				<!-- 修改session全局有效时间:分钟 -->
				<session-config>
					<session-timeout>1</session-timeout>
				</session-config>
			
			3.4.手动销毁session对象
				
				void invalidate()     ： 销毁session对象
				

* 4）如何避免浏览器的JSESSIONID的cookie随着浏览器关闭而丢失的问题

			
	// 手动发送一个硬盘保存的cookie给浏览器
	 
	Cookie c = new Cookie("JSESSIONID",session.getId());
	c.setMaxAge(60*60);
	response.addCookie(c);



总结：
* 1）会话管理： 浏览器和服务器会话过程中的产生的会话数据的管理。

* 2）Cookie技术：

	* new Cookie("name","value")
	* response.addCookie(coookie)
	* request.getCookies()
	
* 3）Session技术

	* request.getSession();
	* setAttrbute("name","会话数据");
	* getAttribute("会话数据")



