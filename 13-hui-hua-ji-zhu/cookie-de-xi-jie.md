* 1）void setPath(java.lang.String uri)   ：设置cookie的有效访问路径。有效路径指的是cookie的有效路径保存在哪里，那么浏览器在有效路径下访问服务器时就会带着cookie信息，否则不带cookie信息。

* 2）void setMaxAge(int expiry) ： 设置cookie的有效时间。（以秒为单位，时间从最后不调用开始计时）

	正整数：表示cookie数据保存浏览器的缓存目录（硬盘中），数值表示保存的时间。
	负整数：表示cookie数据保存浏览器的内存中。浏览器关闭cookie就丢失了！！
	零：表示删除同名的cookie数据
	
* 3）Cookie数据类型只能保存非中文字符串类型的。可以保存多个cookie，但是浏览器一般只允许存放300个Cookie，每个站点最多存放20个Cookie，每个Cookie的大小限制为4KB。