---
title: Ubuntu扁平化主题Flatabulous安装教程
category: Linux
tags: Linux
date: 2017-09-03 09:25:48
author:
keywords:
description:
source_url:
---

不知道大家对Ubuntu自带的主题效果怎么看，反正我自己觉得自带的主题看起来挺难受的，所以网上找了许多法子，终于把主题美化成自己喜欢的样子。

Flatabulous: 一个超好看的扁平化 Ubuntu 桌面主题

![](http://omvbl46i3.bkt.clouddn.com/17-9-3/16411938.jpg)

安装此主题步骤：

#### 一、TweeakTool

```
sudo add-apt-repository ppa:tualatrix/ppa  
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

该工具是用来设置各种Ubuntu偏好使用的

![](http://omvbl46i3.bkt.clouddn.com/17-9-3/47946394.jpg)

#### 二、安装Flatabulous

[下载地址](https://github.com/anmoljagetia/Flatabulous/archive/master.zip)
或者直接在Github上 Clone下来
```
https://github.com/anmoljagetia/Flatabulous
```
把下载下来的zip包解压，移动到/usr/share/themes/下

```
sudo mv Flatabulous-master /usr/share/themes/
```
#### 三、安装扁平化图标ultra-flat-icons
```
sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update
sudo apt-get install ultra-flat-icons
```
或者到[http://ppa.launchpad.net/noobslab/icons/ubuntu/pool/main/u/ultra-flat-icons/](http://ppa.launchpad.net/noobslab/icons/ubuntu/pool/main/u/ultra-flat-icons/)自己下载安装

#### 注意，在Ubuntu15.04会提示找不到ultra-flat-icons这个包

解决方法：在软件和更新中把ultra-flat-icons源中的vivid改成trusty，即可安装成功，最后记得改回来过

或者你也可以运行sudo apt-get install ultra-flat-icons-orange或者 sudo apt-get install ultra-flat-icons-green

根据你自己喜欢的颜色选择。

![](http://omvbl46i3.bkt.clouddn.com/17-9-3/90967736.jpg)

最后完成以上设置的效果图

![](http://omvbl46i3.bkt.clouddn.com/17-9-3/47946394.jpg)


---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
