---
title: 在Github上使用Hexo搭建个人博客
category: 编程相关
tags: Program
date: 2019-12-28 20:14:25
author: itgoyo
keywords: hexo
description:
source_url:
---



成品示例展示：[https://itgoyo.github.io/](https://itgoyo.github.io/)

![](http://omvbl46i3.bkt.clouddn.com/17-5-28/97759013.jpg)

## 1、Hexo搭建

#### 环境
一、环境安装
1. node.js（在node.js官网中下载安装）node.js官网

2. git（OS系统中直接安装x-code就可以了）

3. hexo

1）打开OS系统终端

2）输入安装hexo的代码(此处安装时有可能会提示输入系统管理员密码)

$ sudo npm install -g hexo

如果以上命令安装失败的话，换

```
sudo npm install --unsafe-perm --verbose -g hexo
```

二、hexo创建静态博客
1. 新建blog文件夹

2. 在终端进入该文件夹，初始化博客

$ hexo init
3. 上述完成后，生成原始文件；blog文件夹就是博客的根目录


4. 本地查看：启用本地服务命令(退出按ctrl+c)

$ hexo s

5. 将出现的地址输入浏览器，即可可查看到本地效果

三、github配置
1. 注册github账号并登陆

2. 获取本机的SSH口令

1）输入获取代码，回车直到出现图片所示图形为止

$ ssh-keygen

2）输入编译代码

$ vim \~/.ssh/id\_rsa.pub
3）出现SSH口令后，将红框部分复制，并在下方输入:q，随后按下回车可以退出该窗口


4）进入到github页面设置SSH口令

点击用户下拉菜单中的settings（step1)

点击左侧的SHH and GPG keys（step2)

在Title中输入口令名称（随意）（step3)

在key中贴上SSH口令（step4)

<!--more-->


3. 创建新的仓库

1）创建新的仓库（repOSitory）

点击用户左侧的+号菜单中的New repOSitory（step1)

在repOSitory name中输入二级域名，格式请严格遵照username.github.io（step2)

ps：username填写github的登录用户名，否则上线的时候会报错

是否公开选项可以选取Public（step3)

勾选step4处，会自动生成一份可编辑的README.md文件（建议勾选）（step4)

点击create repOSitory生成仓库完毕（step5)


2）查看新建的仓库（repOSitory）

可以回到github个人首页点击右侧的仓库区


进入后在step1处选择并复制http地址，注意此时step2处应该是空的


四、发布博客
1. 设置blog配置文件

1）打开blog文件夹下的\_config.yml文件

2）找到最下方的type，输入git（注意冒号后面是带空格的）

3）repo行可能没有，需要自己输入，后面跟上github上仓库中复制的http地址（注意此时1、2两处应该是一样的username），不然上传时会报错


4）其他博客设置

title：博客名称

subtitle：博客副标题

description：博客描述

author：作者

language：语言（简体中文是zh-CN）

2. 在终端上传博客

1）进入终端，输入git上传插件安装代码（安装时会提示输入github用户名及密码）

  $ npm install hexo-deployer-git --save
2）安装完毕后，输入获取代码

  $ hexo g
3）最后输入上传代码

  $ hexo d
4）重新在github仓库查看上传文件，此时在step2中会有之前bolg中生成的文件

5）step3处就是你的博客地址


五、新建与更新博客
1. 新建博客

1）终端bolg文件下，输入新建博客代码

	$ hexo new 'filename'
2）此时在bolg/source/\_posts/下面会看到新建的博客

3）博客文件的后缀是.md文件，OS下推荐使用MOU编辑器mou下载地址


2. 更新博客

1）完成编辑后，在终端上依次重复以下代码（此时必须先将编辑器关闭，否则会出现获取错误）

	$ hexo g
	$ hexo d
2）完成后便能刷新博客网页看到新更新的内容了

[1]:	https://github.com/itgoyo/itgoyo.github.io
[2]:	https://github.com/itgoyo/itgoyo.github.io

## 2、Hexo加入评论功能

### Yilia主题（别的主题也是一样的操作）

首先，我们要有一个多说的账号[多说][1](2017-6-1废弃)

然后进入到后台把我们的网站填写进去

![](http://omvbl46i3.bkt.clouddn.com/17-5-28/63843029.jpg)

在`theme/yilia/layout/_partial/post/`目录下创建文件名叫：duoshuo.ejs
把以下代码复制进去

```java
<div class="duoshuo">
    <!-- 多说评论框 start -->
    <div class="ds-thread" data-thread-key="<%=key%>" data-title="<%=title%>" data-url="<%=url%>"></div>
    <!-- 多说评论框 end -->
    <!-- 多说公共JS代码 start (一个网页只需插入一次) -->
    <script type="text/javascript">
    var duoshuoQuery = {short_name:'<%= config.duoshuo_shortname %>'};
    (function() {
        var ds = document.createElement('script');
        ds.type = 'text/javascript';ds.async = true;
        ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
        ds.charset = 'UTF-8';
        (document.getElementsByTagName('head')[0]
         || document.getElementsByTagName('body')[0]).appendChild(ds);
    })();
    </script>
    <!-- 多说公共JS代码 end -->
</div>
```


在`hexo/_comfig.yml`里边添加一下代码（名字换成自己的）

```java
duoshuo_shortname: xxxx(冒号后有空格)

```

最后在`theme/yilia/_config.yml`  里边添加以下代码（名字换成自己的）

```java
duoshuo: true
short_name: xxxx  #名字换你自己在多说后台的名字(冒号后有空格)
```

**一共配置两处地方**
不然即便是看到评论功能，但是不会保留别人对你的评论

然后重新提交代码刷新即可看到评论功能

![](http://omvbl46i3.bkt.clouddn.com/c1a4fdd0b700d1466950b335401c884f.png)
[1]:	http://duoshuo.com/



-----------

### Yilia添加Disqus评论

只需要在Yilia主题里边的_config.yml添加一句

disqus_shortname: 你的Disqus账户名称



## 2、Hexo加入网易云音乐

### Yilia主题（我使用的是这个主题就用这个来讲）
进入网易云音乐: [官网][1]

推荐：自己注册账号，这样子可以创建自己喜欢的歌单，在里边收藏自己喜欢的歌曲


![][image-1]

然后进入到自己的歌单

![][image-2]

点击生成外链，获取到云音乐播放器代码

```
  <iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=300 height=270 src="https://music.163.com/outchain/player?type=0&id=120897804&auto=1&height=430"></iframe>
```

![][image-3]

选择生成自己喜欢的样式，然后复制代码

![][image-4]

最后打开（themes/yilia/layout/\_partial/left-col.ejs）
把复制好的网易云音乐放到第二行里边(当然这个是我的样式，我选择放在左边，你喜欢放在那里自己选择)

![][image-5]

最后的效果图如下

![][image-6]

 ---
 ## 3、Hexo加入百度统计

 ## yilia主题为🌰


 编辑文件 themes/yilia/_config.yml ,添加一行配置，可以删除原来的google analytics

 ```java
 baidu_tongji: true

 ```
 <!--more-->

 新建 themes/yilia/layout/_partial/baidu_tongji.ejs 内容如下

 ```java
 <% if (theme.baidu_tongji) { %>
 <script type="text/javascript">
 #申请的百度统计代码
 </script>
 <% } %>
 ```
 编辑themes/yilia/layout/_partial/head.ejs 在 </head> 前添加

 ```java
 <%- partial("baidu_tongji") %>
 ```

 重新生产部署站点即可。
 Light主题
 编辑文件 themes/yilia/_config.yml ,添加一行配置，可以删除原来的google analytics

 ```java
 baidu_tongji: true`
 ```

 新建 themes/light/layout/_partial/baidu_tongji.ejs 内容如下

 ```html
 <% if (theme.baidu_tongji) { %>
 <script type="text/javascript">
 #申请的百度统计代码
 </script>
 <% } %>
 ```
 编辑themes/Yilia/layout/_partial/head.ejs 在 </head> 前添加

 ```java
 <%- partial("baidu_tongji") %>`
 ```

 重新生产部署站点即可。
----
最后多说一句，因为文章是采用Markdown格式编辑的，所以不免会使用到图片的时候，这个时候如果是在跟目录下创建图片文件，这样子搬迁或者复制什么的会很不便，在此我想向大家推荐一个免费的图床
[极简图床](https://jiantuku.com)
只要复制图片粘贴到极简图床，它会自动生成Markdown格式的图片地址

![](http://omvbl46i3.bkt.clouddn.com/17-5-29/76939269.jpg)

最好申请一个七牛云，这样子就可以创建自己的私密空间。

### Ubuntu下
首先安装nodejs
```
sudo apt-get nodejs

sudo npm cache clean -f
sudo npm install -g n
sudo n stable

出现了相应的版本号了之后
sudo n xxx
```

提交到Girhub还要安装一个git插件
```
npm install hexo-deployer-git --save

之前一直报错，然后手贱敲错
npm install hexo-deployer-git --save、
多了一个、居然成功了？！
```

- 邮箱 ：itgoyo@gmail.com
- Good Luck!

[1]:	http://music.163.com/

[image-1]:	https://itgoyo.github.io/pictures/2017_1_10/yunmusic.png
[image-2]:	https://itgoyo.github.io/pictures/2017_1_10/yunmusiclist.png
[image-3]:	https://itgoyo.github.io/pictures/2017_1_10/yunmusicurl.png
[image-4]:	https://itgoyo.github.io/pictures/2017_1_10/yunmusicplayer.png
[image-5]:	https://itgoyo.github.io/pictures/2017_1_10/playerlocation.png
[image-6]:	https://itgoyo.github.io/pictures/2017_1_10/style.png



---

<div align=center>
欢迎关注我的 Github：itgoyo<br>

发现更多有趣好玩的，欢迎关注我的微信公众号

![](/assets/getqrcode.jpeg)
</div>
