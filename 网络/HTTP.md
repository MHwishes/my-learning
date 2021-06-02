发送HTTP请求的过程就是构建HTTP请求报文并通过TCP协议中发送到服务器指定端口(HTTP协议80/8080, HTTPS协议443)

## HTTP 请求

请求报文是由三部分组成: **请求行**, **请求报头**和**请求正文**。

#### 请求行

格式如下:
Method Request-URL HTTP-Version CRLF

Eg: GET index.html HTTP/1.1

常用的方法有: GET, POST, PUT, DELETE, OPTIONS, HEAD

#### 请求报头

请求报头允许客户端向服务器传递请求的附加信息和客户端自身的信息。

常见的请求报头有: Accept, Accept-Charset, Accept-Encoding, Accept-Language, Content-Type, Authorization, Cookie, User-Agent等。

Connection设置为Keep-alive用于告诉客户端本次HTTP请求结束之后并不需要关闭TCP连接，这样可以使下次HTTP请求使用相同的TCP通道，节省TCP连接建立的时间。

#### 请求正文

当使用POST, PUT等方法时，通常需要客户端向服务器传递数据。这些数据就储存在请求正文中。在请求包头中有一些与请求正文相关的信息，

## HTTP响应

HTTP响应报文也是由三部分组成: **状态码**, **响应报头**和**响应报文**。

#### 状态码

- 1xx：指示信息–表示请求已接收，继续处理。
- 2xx：成功–表示请求已被成功接收、理解、接受。
- 3xx：重定向–要完成请求必须进行更进一步的操作。
- 4xx：客户端错误–请求有语法错误或请求无法实现。
- 5xx：服务器端错误–服务器未能实现合法的请求。

#### 响应报头

常见的响应报头字段有: Server, Connection...

#### 响应报文

服务器返回给浏览器的文本信息，通常HTML, CSS, JS, 图片等文件就放在这一部分

