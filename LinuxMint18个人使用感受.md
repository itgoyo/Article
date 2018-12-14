---
title: LinuxMint18个人使用感受
category: Linux
tags: Linux
date: 2018-01-01 22:41:09
author:
keywords:
description:
source_url:
---


### LinuxMint18使用感受

本人最早使用的linux的系统就是大学实验室里面的hat5，再到后面自己折腾的Ubuntu
从14.04到17.10各个版本都玩过，其中遇到很多坑也是自己一步一步的解决的。前不久我在youtube上面看了一个关于linux发行版本的排行榜，看到好几个视频都是说Mint版排第一，所以这几天试了玩一下这个系统。结果真没有让我失望，真的是我玩的那么多linux系统里面最好用的一个。无论是界面还是自定义的功能，都远超于我之前的系统。

#### 与Ubuntu相比有那些区别

- 左边没有启动项

没有占空间整体效果没有那么丑了，之前Ubuntu虽然可以用软件美化布局，但是整体的风格偏黄给我的感觉很丑。

- 状态栏显示在下面

以前状态栏显示和Mac一样显示在上面，现在显示在下面感觉眼睛好受不少

- 状态栏还有添加部件的功能

显示网络实时速率，还有内存，还有当前的聊天窗口，还有剪贴板多层级的内容
![](http://omvbl46i3.bkt.clouddn.com/15867e0d5a92634de17454c5c4092283.png)

- 支持自定义快捷键

一开始玩这个系统的时候，每次启动终端都只能用鼠标去启动器里面去找，很麻烦，后面在自定义快捷键的地方本来就预设有`ctrl+shift+t`，只要勾选就可以了

- 自带Esc和CapsLock按键互换

我喜欢使用Vim编辑，所以电脑每一种系统我最先做的都是把Esc和CapsLock键互换。网上有很多切换按键的教程，但很多都是临时的，没有能解决我的需求，后面ubuntu也找到了满足自己需求的解决方法，以下分享给大家

 Ubuntu的解决方法

最近确定在网上再找找办法解决，最后找到了这个方法dconf-editor，使用这个修改切换中英文都不会发生改变，修改是永久的，为了下次修改方便，特地在此记录下，如果对他人有所帮助那再好不过了。按照提示直接sudo apt install dconf-editor进行安装，接着运行dconf-editor命令启动图形界面，选择org >> gnome >> desktop >> input-sources，修改xkb-options为['caps:swapescape']，如下图:

![](http://omvbl46i3.bkt.clouddn.com/b0d1ffed95e9f49c80b315fc444387d9.png)

LinuxMint18的解决方法：
```
click System Settings
keyboard layout
options...(lower right hand corner)
caps lock key behaviour (4th down)
Scroll down and choose "Swap ESC and Caps Lock".
```

- 支持Lantern

Lantern在linux下只有Ubuntu版本，碰巧LinuxMint版本和Ubuntu内核类似，结果我试了一下还真能够使用

- 系统自带桌面软件风格切换功能

提供多种风格给用户选择，用户可以根据自己的喜好进行修改

- 系统自带Nvidia驱动

之前在Ubuntu下还要另外下载Nvidia驱动软件，现在系统自带该软件用户可根据自己显卡选择合适自己的显卡驱动

- 文件显示

文件显示可以想mac还有windows下面一样进行归类区分，看起来比较方便

- 自带软件包管理

#### LinuxMint18遇到的问题和解决方案分享

##### 最开始是安装Chrome的时候遇到的问题

安装命令
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
```
```
sudo apt-get update
```
```
sudo apt-get -y install google-chrome-beta
```

问题：
```
[0807/144244.712736:FATAL:nss_util.cc(627)] NSS_VersionCheck("3.26") failed. NSS >= 3.26 is required
Please upgrade to the latest NSS, and if you still get this error,
contact your distribution maintainer.
```

- 方法一：chrome 版本降低

```
卸载目前的chrome
https://www.slimjet.com/chrome/google-chrome-old-version.php 下载相应的chrome旧版本安装。
```

- 方法2 : update NSS（推荐）

```
sudo apt-get install libnss3
```

##### 每次打开Chrome都会询问KDE Wallet请求的解决办法

编辑文件~/.kde/share/config/kwalletrc，追加内容：

```
[Auto Deny]
kdewallet=Google Chrome
```
##### LinuxMint18安装OBS
For Ubuntu 14.04 LTS, FFmpeg is not officially included so you will need a specific PPA:
```
  sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next
  sudo apt-get update && sudo apt-get install ffmpeg
```
For Ubuntu 15.04 and following versions, FFmpeg is officially included:
```
  sudo apt-get install ffmpeg
```
Then you can install OBS with the following commands:
```
  sudo add-apt-repository ppa:obsproject/obs-studio
  sudo apt-get update && sudo apt-get install obs-studio
```

感觉在Linux下面使用OBS推流软件比在Windows上面好很多，一点都不觉得卡，而且上传速度很快很稳定。

最后希望大家可以喜欢这个系统，如果遇到什么问题我能帮的上的话，可以探讨一下


---

<div align=center>
欢迎关注我的 Github：itgoyo<br>

发现更多有趣好玩的，欢迎关注我的微信公众号

![](/assets/getqrcode.jpeg)
</div>
