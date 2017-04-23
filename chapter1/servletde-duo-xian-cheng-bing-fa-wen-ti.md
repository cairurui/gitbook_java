1. servlet对象在tomcat服务器是单实例多线程的。

	因为servlet是多线程的，所以当多个servlet的线程同时访问了servlet的共享数据，如成员变量，可能会引发线程安全问题。
		
	解决办法：
		1）把使用到共享数据的代码块进行同步（使用synchronized关键字进行同步）
		2）建议在servlet类中尽量不要使用成员变量。如果确实要使用成员，必须同步。而且尽量缩小同步代码块的范围。（哪里使用到了成员变量，就同步哪里！！），以避免因为同步而导致并发效率降低。

	Servlet学习：
	
		HttpServletRequest  请求对象：获取请求信息
		HttpServletResponse 响应对象： 设置响应对象
		ServletConfig对象    servlet配置对象
		ServletContext对象； servlet的上下文对象
				