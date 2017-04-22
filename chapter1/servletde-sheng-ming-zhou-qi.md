1.  构造方法

    构造方法：创建servlet对象。默认情况下，第一次访问servlet对象时。只调用1次。
    
2. init方法（有参）

    init方法（有参）：创建完servlet对象后调用，只调用一次；

    注意：会调用init无参数的方法！
    
3. service方法：
    
    servlet提供服务的方法，每次发出请求的时候调用。

4. destroy方法：

     destroy方法：tomcat服务停止或web应用重新部署，servlet对象销毁，destroy方法被调用。


         



