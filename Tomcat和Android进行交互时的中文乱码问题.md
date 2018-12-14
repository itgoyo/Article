---
title: Tomcat和Android进行交互时的中文乱码问题
category: Android
toc: true
tags: Android
date: 2018-05-10 09:36:29
author: itgoyo
keywords:
description:
source_url:
---

![](http://omvbl46i3.bkt.clouddn.com/12518abf1c4dd752947fd9c7c026590c.png)

在使用Tomcat服务端和Android客户端出现乱码的根本原因是由于Tomcat的String转ByteArray采用的编码集`iso-8859-1`,而Android则是采用的`UTF-8`。

解决方法：
-  Tomcat端将String转换为ByteArray的编码方式采用utf-8

```
示例代码如下：

response.getOutputStream().write("中文".getBytes("utf-8"));
```
- POST方式

```
比如表单提交，在Servlet或者Filter中设置

request.setCharacterEncoding("UTF-8");

就能很好的解决。
```
- GET方式

```
GET方式：单纯设置request.setCharacterEncoding("UTF-8");是没有用的，所以我们把默认的iso-8859-1编码改成UTF-8，在TOMCAT的配置文件的server.xml中更改：

  <Connector port="8080"protocol="HTTP/1.1"

              connectionTimeout="20000"

              redirectPort="8443" URIEncoding="UTF-8" />

添加URIEncoding=UTF-8
```
- Android访问

```
上面的访问过程提到浏览器对中文进行编码，这里我们直接发送请求，并没有编码这个过程，所以我们需要自己手动编码，即：

String name =URLEncoder.encode("德玛西亚","UTF-8");
```

---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
