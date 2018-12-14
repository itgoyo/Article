---
title: 印象笔记+hexo搭建自己的个人博客
toc: true
category: 编程相关
tags: Program
date: 8888-08-08 18:16:48
author:
keywords:
description:
source_url:
---
之前在逛[V2EX](https://www.v2ex.com/)的时候以外发现一个好玩的东西,就是使用印象笔记Evernote来写文章让后生成响应的html同步到hexo上面。由于自己在生活中使用印象笔记的频率也比较高，而且收藏文章的时候也比较方便。不用自己又特意转成md格式的,这样子省时省力所以决定把自己的博客搭建给换成这个框架来搭建。

### 搭建过程

#### 一、安装[everblog](https://github.com/everblogjs/everblog)
```
1. Install everblog:

$ npm i everblog -g
$ vim ~/.everblogrc

  token: xxx,
  noteStoreUrl: xxx,
  notebook: myblog

2. Clone theme, like `everblog-theme-spa`:

$ git clone https://github.com/everblogjs/everblog-theme-spa myblog
$ cd myblog && npm i

3. Open evernote:

- create a new notebook named `myblog`
- create a new note named `_config.yml`, add some configs, like: `title`, `description`
- create some notes

4. Start everblog:

$ DEBUG=* everblog start
```
#### 二、Adapter适配器
以上是原框架作者的搭建过程，但是本人自己在实践的过程中出现了很多问题，所以并没有完全按照他的版本来做。我用的是网上搜索出来的另一位作者的方法，他同时也把自己的代码提交到了everblog中，大家可以看commit记录，使用[zhougy0717](https://github.com/zhougy0717)的版本来搭建，这个是我搭建过程中所有遇到的问题他都很热心的帮助解答了，[对话记录](https://github.com/zhougy0717/zhougy0717.github.io/issues/1),希望能帮助到你.

按照以上操作只能算是完成了一半，你还有在你当前的hexo博客目录安装一个[everblog-adaptor-hexo](https://github.com/everblogjs/everblog-adaptor-hexo)（也就是你hexo init的那个目录）

```
$ cd your_hexo_blog_dir
$ npm i everblog-adaptor-hexo --save
$ vim index.js, add `module.exports = require('everblog-adaptor-hexo')`
Open evernote, create `_config.yml`(see below) and some notes

    title: NSWBMW's blog
    subtitle: lalala
    description: my blog
    author: nswbmw

$ everblog build
$ hexo server
$ open http://localhost:4000/
```

注意由于本人在使用以上框架的时候出现了很多问题，我用的Adapter是其他版本的[everblog-adaptor-hexo-html](https://github.com/zhougy0717/everblog-adaptor-hexo-html)
```
cd your_hexo_blog_dir

npm i everblog-adaptor-hexo-html --save

vim index.js, add:

module.exports = require('everblog-adaptor-hexo-html')

DEBUG=* everblog build (see everblog)
```

由于上面安装的第一个步骤也就是`npm i everblog -g`中安装了很多文件夹，但是有一个`evernote`这个文件夹的版本不是我所需要的我需要的版本是`evernote@1.25.82`,所以你只需要使用命令安装`sudo npm install evernote@1.25.82`就可以了，当然最好你要先删除掉`usr/local/lib/node_modules/evernote`先在安装不然我担心它还是会使用默认的`evernote2.0`版本。

最后打开你的印象笔记，新建笔记本组新建一个名字`.everblogrc`文件中`notebook`同名的笔记本组，我的就叫`myblog`

我的`.everblogrc`配置如下
```
token:d9fab5c755171aedf0d9fab5c755171aedf0d9fab5c755171aedf0d9fab5c755171aedf0
noteStoreUrl: 'https://app.yinxiang.com/shard/sxx/notestore'
notebook: myblog
serviceHost: app.yinxiang.com
sandbox: false

```

#### 三、申请Token
上面的Token是从你自己的个人开发者上面获取到的

国际版Evernote：https://www.evernote.com/api/DeveloperToken.action

国内版印象笔记：https://app.yinxiang.com/api/DeveloperToken.action

由于Evernote因为安全问题已经自动把Token的功能给砍掉了，但是你可以让客服单独为你账号开通

以上所有步骤都完成之后，在你印象笔记里面新建的笔记本组里新建一个名为`_config.yml`的文件然后把你hexo目录下面的`config.yml`全部复制进去（后面我印象笔记没有这个东西好像也能同步也不知道是为什么，可能是我换了其他Adapter的原因吧）

只要在首页不是缩略展示文章的都是在印象笔记中完成的，因为.md文件会自动截断文章，但是Evernote的文章内容不会。


---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
