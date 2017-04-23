1. servlet的ServletContext对象 

    ServletContext对象 ,叫做Servlet的上下文对象。表示一个当前的web应用环境。<h2>一个web应用中只有一个ServletContext对象。</h2>

    ** 在一个web应用可以存在多个ServletConfig对象（一个Servlet对应一个ServletConfig对象）,但一个web应用中只有一个ServletContext对象。 **

2. 对象创建和得到

    创建时机：加载web应用时创建ServletContext对象。（部署时创建）
    得到对象： 从ServletConfig对象的getServletContext方法得到
    
3. ServletContext对象的核心API(作用)
    
    String getContextPath()   --得到当前web应用的路径
    
    String getInitParameter(String name)  --得到web应用的初始化参数
    Enumeration getInitParameterNames()  
    
    void setAttribute(String name, Object object) --域对象有关的方法
    Object getAttribute(String name)  
    void removeAttribute(String name)  
    
    RequestDispatcher getRequestDispatcher(String path)   --转发（类似于重定向）
    
    String getRealPath(String path)     --得到web应用的资源文件
    InputStream getResourceAsStream(String path)  