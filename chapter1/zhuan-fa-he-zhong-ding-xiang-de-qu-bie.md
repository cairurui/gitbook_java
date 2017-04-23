1. 转发
	 a）地址栏不会改变
	 b）转发只能转发到当前web应用内的资源
	 c）可以在转发过程中，可以把数据保存到request域对象中

	```
	RequestDispatcher requestDispatcher = getServletContext().getRequestDispatcher("/MyHtml.html");
	requestDispatcher.forward(req, resp);
	```
	
2. 重定向			
	a）地址栏会改变，变成重定向到地址。
	b）重定向可以跳转到当前web应用，或其他web应用，甚至是外部域名网站。
	c）不能再重定向的过程，把数据保存到request中。
	
	```
	resp.sendRedirect(this.getServletContext().getContextPath()+"/MyHtml.html");
	```
	
结论： 
	* 如果要使用request域对象进行数据共享，只能用转发技术！！！
	* 重定向其过程：浏览器访问A地址，A服务打回给浏览器并告知让其转向B，浏览器再重新访问B地址。
	* 转发器过程：浏览器访问A地址，服务端应该调用B地址的，服务器内部将request和response重新转给B地址。