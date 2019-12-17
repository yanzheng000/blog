​	 HttpURLConnection的getHeaderField默认所有header是用iso-8859-1编码的，但是中文实际是用uft8编码。所以就出现了乱码问题。既然知道原因，解决起来就很简单了。
因为是把多字节的编码转换成了单字节的iso-8859-1,所以并不会造成编码信息的丢失。这样我们用

Java代码 [![收藏代码](https://www.iteye.com/images/icon_star.png)](javascript:void())

1. **new** String(disposition.getBytes("ISO-8859-1"),"utf8") 

requestBody = new String(request.getHeader("RBody").getBytes("ISO-8859-1"),"utf8");