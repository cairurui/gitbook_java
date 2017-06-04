### EL作用
jsp的核心语法： jsp表达式 <%=%>和 jsp脚本<%  %>。
以后开发jsp的原则： ** 尽量在jsp页面中少写甚至不写java代码 **。

使用EL表达式替换掉jsp表达式

EL表达式作用： 向浏览器输出** 域对象 **中的变量值或表达式计算的结果！！！

语法： ${变量或表达式}


	
### EL语法

1）输出基本数据类型变量

	1.1 从四个域获取
		${name}
	1.2 指定域获取
		${pageScope.name}
        域范围： pageScoep / requestScope / sessionScope / applicationScope
        
		String name = "rose";  
		//放入域中
		//pageContext.setAttribute("name",name);
		pageContext.setAttribute("name",name,PageContext.REQUEST_SCOPE); 
		%>
		<%=name %>
		<br/>
		<%--
		1)从四个域自动搜索
		--%>
		EL表达式： ${name }
		<%--
		${name } 等价于
		<%=pageContext.findAttribute("name")%>
		--%>
		<%--
		2） 从指定的域中获取数据
		--%>
		EL表达式： ${pageScope.name }
		<%--
		${pageScope.name } 等价于
		<%= pageContext.getAttribute("name",PageContext.PAGE_SCOPE)%>
		
		--%>



2）输出对象的属性值

	<%--使用EL获取对象 --%>
	使用EL获取对象: ${student.name} - ${student.age } </br>
	<%--
	${student.name} 等价于     （点相对于调用getXX（）方法）
	<%=((Student)pageContext.findAttribute("student")).getName()%>
	--%>
				
3）输出集合对象

	<%--使用EL获取List对象 --%>
	${list[0].name } - ${list[0].age }<br/>
	${list[1].name } - ${list[1].age }<br/>
	${list[2].name } - ${list[2].age }
	<%--
	list[0]等价于       (中括号相对于调用get(参数)方法)
	((List)pageContext.findAttribute("list")).get(0)
	--%>
	<hr/>
	<%--使用EL获取Map对象 --%>
	${map['100'].name } -  ${map['100'].age }<br/>
	${map['101'].name } -  ${map['101'].age }<br/>
	${map['102'].name } -  ${map['102'].age }<br/>

4）EL表达式计算

	<%--
		1)算术表达式
		+  -  *  /
	--%>
	${10+5 }<br/>
	${10*5 }
	
	
	<%--
	2)比较运算
		>  <  >=  <=  ==   !=
	--%>
	${10>5 }<br/>
	${10<5 }<br/>
	${10!=10 }
	
	
	<%--
	3)逻辑运算
		&&  ||  !
	--%>
	${true && false }<br/>
	${true || false }<br/>
	${!false }<br/>
	
	
	<%--
	4)判空
	null 或 空字符串:  empty
	--%>
	<%
	//String name = "eric";
	//String name = null;
	String name = "";
	pageContext.setAttribute("name",name);
	%>
	判断null： ${name==null }<br/>
	判断空字符： ${name=="" }<br/>
	判空：  ${name==null || name=="" }
	另一种判空写法： ${empty name }

		
![](/assets/无标题.png)			
				