
1. ServletConfig对象: 

    主要是用于加载servlet的初始化参数。在一个web应用可以存在多个ServletConfig对象
   <h2>一个Servlet对应一个ServletConfig对象 </h2> 
   
2. 对象创建和得到

   创建时机： 在创建完servlet对象之后，在调用init方法之前创建。
   得到对象： 直接从有参数的init方法中得到！！！
   
3. servlet的初始化参数配置

```
<servlet>
    <servlet-name>ConfigDemo</servlet-name>
    <servlet-class>com.xiaocai.config.ConfigDemo</servlet-class>
    <!-- 初始参数： 这些参数会在加载web应用的时候，封装到ServletConfig对象中 -->
    <init-param>
    	<param-name>pathA</param-name>
    	<param-value>e:/a.txt</param-value>
    	<param-name>pathB</param-name>
    	<param-value>e:/b.txt</param-value>
    </init-param>
  </servlet>
```


    java.lang.String getInitParameter(java.lang.String name)  根据参数名获取参数值
    java.util.Enumeration getInitParameterNames()    获取所有参数
    ServletContext getServletContext()     得到servlet上下文对象
    java.lang.String getServletName()       得到servlet的名称
    
    
    
    

