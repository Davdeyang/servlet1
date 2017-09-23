# servlet1
HttpServletRequest

HttpServletRequest接口最常用的方法就是获得请求中的参数，这些参数一般是客户端表单中的数据。同时，HttpServletRequest接口可以获取由客户端传送的名称，也可以获取产生请求并且接收请求的服务器端主机名及IP地址，还可以获取客户端正在使用的通信协议等信息。下表是接口HttpServletRequest的常用方法。

说明：HttpServletRequest接口提供了很多的方法。

接口HttpServletRequest的常用方法

方    法

说    明

getAttributeNames()

返回当前请求的所有属性的名字集合

getAttribute(String name)

返回name指定的属性值

getCookies()

返回客户端发送的Cookie

getsession()

返回和客户端相关的session，如果没有给客户端分配session，则返回null

getsession(boolean create)

返回和客户端相关的session，如果没有给客户端分配session，则创建一个session并返回

getParameter(String name)

获取请求中的参数，该参数是由name指定的

getParameterValues(String name)

返回请求中的参数值，该参数值是由name指定的

getCharacterEncoding()

返回请求的字符编码方式

getContentLength()

返回请求体的有效长度

getInputStream()

获取请求的输入流中的数据

getMethod()

获取发送请求的方式，如get、post

getParameterNames()

获取请求中所有参数的名字

getProtocol()

获取请求所使用的协议名称

getReader()

获取请求体的数据流

getRemoteAddr()

获取客户端的IP地址

getRemoteHost()

获取客户端的名字

getServerName()

返回接受请求的服务器的名字

getServerPath()

获取请求的文件的路径

 

HttpServletResponse
在Servlet中，当服务器响应客户端的一个请求时，就要用到HttpServletResponse接口。设置响应的类型可以使用setContentType()方法。发送字符数据，可以使用getWriter()返回一个对象。下表是接口HttpServletResponse的常用方法。

接口HttpServletResponse的常用方法

       方    法

说    明

addCookie(Cookie cookie)

将指定的Cookie加入到当前的响应中

addHeader(String name,String value)

将指定的名字和值加入到响应的头信息中

containsHeader(String name)

返回一个布尔值，判断响应的头部是否被设置

encodeURL(String url)

编码指定的URL

sendError(int sc)

使用指定状态码发送一个错误到客户端

sendRedirect(String location)

发送一个临时的响应到客户端

setDateHeader(String name,long date)

将给出的名字和日期设置响应的头部

setHeader(String name,String value)

将给出的名字和值设置响应的头部

setStatus(int sc)

给当前响应设置状态码

setContentType(String ContentType)

设置响应的MIME类型



2、一些区别细节
一、ServletRequest
 
代表一个HTTP请求，请求在内存中是一个对象，这个对象是一个容器，可以存放请求参数和属性。
 
1、请求对象何时被创建，当通过URL访问一个JSP或者Servlet的时候，也就是当调用Servlet的service()、doPut()、doPost()、doXxx()方法时候的时候，执行Servlet的web服服务器就自动创建一个ServletRequest和ServletResponse的对象，传递给服务方法作为参数。
 
2、请求对象由Servlet容器自动产生，这个对象中自动封装了请求中get和post方式提交的参数，以及请求容器中的属性值，还有http头等等。当Servlet或者JSP得到这个请求对象的时候，就知道这个请求时从哪里发出的，请求什么资源，带什么参数等等。
 
3、ServletRequest的层次结构
javax.servlet.ServletRequest 
  javax.servlet.http.HttpServletRequest
 
4、通过请求对象，可以获得Session对象和客户端的Cookie。
 
5、请求需要指定URL，浏览器根据URL生成HTTP请求并发送给服务器，请求的URL有一定的规范：

二、ServletResponse
 
也是由容器自动创建的，代表Servlet对客户端请求的响应，响应的内容一般是HTML，而HTML仅仅是响应内容的一部分。请求中如果还包含其他资源会依次获取，如页面中含有图片，会进行第二个http请求用来获得图片内容。
相应对象有以下功能：
1、向客户端写入Cookie
2、重写URL
3、获取输出流对象，向客户端写入文本或者二进制数据
4、设置响应客户端浏览器的字符编码类型
5、设置客户端浏览器的MIME类型。
