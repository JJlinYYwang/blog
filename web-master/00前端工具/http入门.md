### 目录：

##### 一：www 的历史

##### 二：HTTP 简介

##### 三：请求和响应

##### 四：小知识

请求方式对比

常见状态码

URI和URL的区别


### 一：www 的历史

--------------------- 

Tim Berners-Lee（下文中称为李爵士） 在 1989 年至 1992 年间，发明了 WWW（World Wide Web），一种适用于全世界的网络。

主要包含三个概念：

URI，俗称网址

HTTP，两个电脑之间传输内容的协议

HTML，超级文本，主要用来做页面跳转

URL 的作用是能让你访问一个页面，HTTP 的作用是让你能下载这个页面，HTML 的作用是让你能看懂这个页面。

这是一个简单而完美的系统

2009 年李爵士在 TED 上有一个演讲：https://www.ted.com/talks/tim_berners_lee_on_the_next_web ，说出了他为什么发明 WWW。


2017 年，李爵士获得了图灵奖，我觉得这个奖实至名归。

[万维网之父Tim Berners-Lee获图灵奖：奖金100万美元](http://www.sohu.com/a/132077489_465975)

[如何评价 Tim Berners-Lee 于 2017 年获得图灵奖？](https://www.zhihu.com/question/58034118)

![URL的常见组成](https://upload-images.jianshu.io/upload_images/6299738-dab50d6b5faf7a81.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

### 二：HTTP 简介

--------------------- 

HTTP（HyperText Transfer Protocol，超文本传输协议）最早就是计算机与计算机之间沟通的一种标准协议，这种协议限制了通讯内容的格式以及各项 内容的含义。 

随着时代的发展，技术的变迁，这种协议现在广泛的应用在各种领域，也不仅仅局限于计算机与计算机之间，手机、电视等各种智能设备很多时候都在使用这种协议通讯，所以一般现在称 HTTP 为端与端之间的通讯协议。


 应用软件架构一般分为两类：

（1）B/S 架构：Browser（浏览器） ←→ Server（服务器），这种软件都是通过浏览器访问一个网站使用，服务器提供数据存储等服务。

（2）C/S 架构：Client（客户端） ←→ Server（服务器），这种软件通过安装一个软件到电脑，然后使用，服务器提供数据存储等服务。

Web 属于 B/S 架构的应用软件，在 B/S 架构中，浏览器与服务器沟通的协议就是 HTTP 协。

![服务器与浏览器的交互](https://upload-images.jianshu.io/upload_images/6299738-5a6b43b3308b607e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/440)

##### 过程

浏览器负责发起请求

服务器在 80 端口接收请求

服务器负责返回内容（响应）

浏览器负责下载响应内容

###### HTTP 的作用就是指导浏览器和服务器如何进行沟通。


### 三：请求和相应

--------------------- 

curl -s -v -H "Frank: xxx" -- "https://www.baidu.com"

![用 curl 创造一个请求，并得到响应](https://upload-images.jianshu.io/upload_images/6299738-5b9c3f3cb57ee883.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/840)

#### 请求

###### 请求内容

    GET / HTTP/1.1
    Host: www.baidu.com
    User-Agent: curl/7.54.0
    Accept: */*
    Frank: xxx


###### 请求格式

> 1 动词 路径 协议/版本
      2 Key1: value1
      2 Key2: value2
      2 Key3: value3
      2 Content-Type: application/x-www-form-urlencoded
      2 Host: www.baidu.com
      2 User-Agent: curl/7.54.0
      3 
      4 要上传的数据

#### 小结：

请求最多包含四部分，最少包含三部分。

第三部分永远都是一个回车（\n）

动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等

这里的路径包括「查询参数」，但不包括「锚点」

如果你没有写路径，那么路径默认为 /

第 2 部分中的 Content-Type 标注了第 4 部分的格式

##### 响应

请求了之后，应该都能得到一个响应，除非断网了，或者服务器宕机了。

###### 响应内容：

```
HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

<!DOCTYPE html>
<!--STATUS OK--><html> <head> 后面太长，省略了……
```

###### 响应的格式


>1 协议/版本号 状态码 状态解释
>2 Key1: value1
>2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容


##### 小结

状态码要背，是服务器对浏览器说的话

>1xx不常用
2xx 表示成功
3xx 表示滚吧
4xx 表示你丫错了
5xx 表示好吧，我错了

状态解释没什么用

第 2 部分中的 Content-Type 标注了第 4 部分的格式

第 2 部分中的 Content-Type 遵循 MIME 规范

#### 使用用 Chrome 发送请求和查看响应

![Chrome](https://upload-images.jianshu.io/upload_images/6299738-97ced256678077c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/840)

###四：小知识
--------------------- 
##### 1:请求方式

http://www.w3school.com.cn/tags/html_ref_httpmethods.asp
http://www.runoob.com/http/http-methods.html
 
 GET  字面意思：拿，获取
 
 POST 字面意思：发，给 

![对比 GET 与 POST](https://upload-images.jianshu.io/upload_images/6299738-d8bef3cefc1d5111.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/840)

##### 2:常见状态码

常见状态代码、状态描述的说明如下。

>200 OK：客户端请求成功。
400 Bad Request：客户端请求有语法错误，不能被服务器所理解。
401 Unauthorized：请求未经授权，这个状态代码必须和 WWW-Authenticate 报头域一起使用。
403 Forbidden：服务器收到请求，但是拒绝提供服务。
404 Not Found：请求资源不存在，举个例子：输入了错误的URL。
500 Internal Server Error：服务器发生不可预期的错误。
503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能恢复正常。

##### 3:URI和URL的区别

URI，是uniform resource identifier，统一资源标识符，用来唯一的标识一个资源。

Web上可用的每种资源如HTML文档、图像、视频片段、程序等都是一个来URI来定位的

URI一般由三部组成：

①访问资源的命名机制

②存放资源的主机名

③资源自身的名称，由路径表示，着重强调于资源。

URL是uniform resource locator，统一资源定位器，它是一种具体的URI，即URL可以用来标识一个资源，而且还指明了如何locate这个资源，是互联网上用来标识某一处资源的地址。

URL一般由三部组成：

①协议(或称为服务方式)

②存有该资源的主机IP地址(有时也包括端口号)

③主机资源的具体地址。如目录和文件名等

