---
title: Ubuntu安装完之后所需要做的配置
category: Linux
tags: Linux
date: 2017-12-28 20:18:16
author:
keywords:
description:
source_url:
---



#字体推荐思源
lantern可以设置全局代理
#### 安装好了ubuntu之后，安装gnome主题
安装Gnome之前，升级系统：
```
$ sudo apt update
$ sudo apt upgrade
```
```
sudo apt-get update
sudo apt-get install gnome-session-flashback
```
安装完之后使用classic主题登录（此时终端不可用ctrl+alt+t）

#### Ubuntu 16.04/16.10安装KDE Plasma

```
$ sudo add-apt-repository ppa:kubuntu-ppa/backports  # Ubuntu 16.04
# 如果使用16.10，不用添加第三方源
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install kubuntu-desktop

```
- lightdm：Unity桌面默认的Display Manager
- ssdm：KDE桌面更倾向于使用ssdm（选这个）
最后安装登录系统没反应，只有一个下划线，然后在登录时ctrl+alt+F3进入终端模式
```
sudo apt-get remove kubuntu-xxxx
```
然后登录的时候就可以使用gnome登录，此时终端可使用快捷键唤出

#### Ubuntu安装QQ

crossover安装与破解

在官网下载crossover安装包：

https://www.codeweavers.com/products/crossover-linux

等待安装完毕，安装完成后先不要打开crossover，下载破解文件：

https://pan.baidu.com/s/1slTLv8T

在命令行输入sudo nautilus打开一个root权限的文件管理器

把破解文件 (crossover16crack->winewrapper.exe.so) 替换路径: /opt/cxoffice/lib/wine下的winewrapper.exe.so文件。提示已有文件，点“替换”破解完成。

安装Deepin QQ 7.9 轻聊版

下载安装包：

https://pan.baidu.com/s/1gfl00ZT

下载之后用归档管理器打开

点开 data.tar.xz 找到 ./opt/cxoffice/support
把 apps.com.qq.im.light 这个文件夹提取出来

在命令行输入sudo nautilus打开一个root权限的文件管理器

然后将这个文件夹复制到系统的 /opt/cxoffice/support 下

#### QQ最小化叫唤不出来解决

```
sudo apt-add-repository ppa:fixnix/indicator-systemtray-unity
sudo apt-get update
sudo apt-get install indicator-systemtray-unity
```
或者是使用gnome主题

win+alt 鼠标右键状态栏  add to panel 增加消息通知事件即可

#### Ubuntu安装Chrome

2.在终端中，输入以下命令：
```
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/

wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -

sudo apt-get update

sudo apt-get install google-chrome-stable
```
#### sudo:/etc/sudoers 可被任何人写 解决方案
解决方式

```
sudoers的权限被改了，改回来就好了。

pkexec chmod 0440 /etc/sudoers
```

#### git push时提示：更新被拒绝，因为您当前分支的最新提交落后于其对应的远程分支
```
git remote add origin https://github.com/username/test.git    
$git fetch origin  
$git merge origin/master  

```

#### .md模板
```
title: "[译]Kotlin 1.1 候选版本来啦"
date: 2017-02-17 13:37:00
author: Mikhail Glukhikh
tags:
keywords:
categories: 官方动态
reward: false
reward_title: Have a nice Kotlin!
reward_wechat:
reward_alipay:
source_url: https://blog.jetbrains.com/kotlin/2017/02/kotlin-1-1-release-candidate-is-here/
translator: ahong222
translator_url: https://github.com/ahong222
```

tar
解包：tar xvf FileName.tar
打包：tar cvf FileName.tar DirName

.gz
解压1：gunzip FileName.gz
解压2：gzip -d FileName.gz
压缩：gzip FileName
.tar.gz
解压：tar zxvf FileName.tar.gz
压缩：tar zcvf FileName.tar.gz DirName

.bz2
解压1：bzip2 -d FileName.bz2
解压2：bunzip2 FileName.bz2
压缩： bzip2 -z FileName
.tar.bz2
解压：tar jxvf FileName.tar.bz2
压缩：tar jcvf FileName.tar.bz2 DirName

.bz
解压1：bzip2 -d FileName.bz
解压2：bunzip2 FileName.bz

.tar.bz
解压：tar jxvf FileName.tar.bz

.Z
解压：uncompress FileName.Z
压缩：compress FileName


.tar.Z
解压：tar Zxvf FileName.tar.Z
压缩：tar Zcvf FileName.tar.Z DirName

.tgz
解压：tar zxvf FileName.tgz

.tar.tgz
解压：tar zxvf FileName.tar.tgz
压缩：tar zcvf FileName.tar.tgz FileName

.zip
解压：unzip FileName.zip
压缩：zip FileName.zip DirName

.rar
解压：rar a FileName.rar
压缩：rar e FileName.rar

.lha
解压：lha -e FileName.lha
压缩：lha -a FileName.lha FileName

#### AndroidStudio配置
```
Edit /etc/apt/sources.list file and add one of following line :

deb http://download.virtualbox.org/virtualbox/debian trusty contrib
Save and exit

update using :sudo apt-get update

According to virtualbox_wiki you need to Install dkms

sudo apt-get install dkms
Setup oracle public key:

wget http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc
sudo apt-key add oracle_vbox.asc
Install Oracle VirtualBox

sudo apt-get update
sudo apt-get install virtualbox-5.0
```
#### 安装OBS推流软件
```
 sudo apt-get install ffmpeg

 sudo add-apt-repository ppa:obsproject/obs-studio
 sudo apt-get update && sudo apt-get install obs-studio
```
#### ftp上传文件
使用[Filezillia](https://filezilla-project.org/)

注意！！！

上传文件的时候默认是不支持中文的，要自己在站点设置里边强制使用UTF-8字符集




---

<div align=center>
欢迎关注我的 Github：itgoyo<br>

发现更多有趣好玩的，欢迎关注我的微信公众号

![](/assets/getqrcode.jpeg)
</div>
