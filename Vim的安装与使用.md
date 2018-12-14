---
title: Vim的安装与使用
category: Vim
tags: Vim
date: 2017-11-03 16:55:29
author: itgoyo
keywords: Vim
description:
source_url:
---
## Vim

#### Vim的配置以spf-13为例子

项目地址:   https://github.com/spf13/spf13-vim

#### Vim的安装

- Linux, *nix, Mac OSX Installation

The easiest way to install spf13-vim is to use our automatic installer by simply copying and pasting the following line into a terminal. This will install spf13-vim and backup your existing vim configuration. If you are upgrading from a prior version (before 3.0) this is also the recommended installation.

Requires Git 1.7+ and Vim 7.3+

```
curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh
```
If you have a bash-compatible shell you can run the script directly:
```
sh <(curl https://j.mp/spf13-vim3 -L)
```
此过程会比较长，包括插件的下载还有安装，这个过程将近1个多小时

- Installing on Windows

On Windows and *nix Git and Curl are required. Also, if you haven't done so already, you'll need to install Vim. The quickest option to install all three dependencies (Git, Curl, Vim and spf13-vim) is via Chocolatey NuGet. After installing Chocolatey, execute the following commands on the command prompt:

Install with cmd.exe(run as admin mode)
```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

```
C:\> choco install spf13-vim
```

一直Y，整个过程大概2h左右

## Vim插件的介绍

- #### Vundle(The best plugin manager)

Vundle is an excellent system built on the same principles as Pathogen, but with an integrated plugin management system that is Git and Github aware.

spf13-vim uses the Vundle plugin management system to have a well organized vim directory (Similar to mac's app folders). Vundle also ensures that the latest versions of your plugins are installed and makes it easy to keep them up to date.

- #### NERDTree(file navigation)

NERDTree is a file explorer plugin that provides "project drawer" functionality to your vim editing. You can learn more about it with :help NERDTree or checkout my post on NERDTree.

Use `Ctrl+e` to toggle NERDTree

- #### ctrlp(fast file finder)

Ctrlp replaces the Command-T plugin with a 100% viml plugin. It provides an intuitive and fast mechanism to load files from the file system (with regex and fuzzy find), from open buffers, and from recently used files.

Use `Ctrl+p` to toggle Ctrlp

- #### neocomplcache(autocomplete++)

NeoComplCache is an amazing autocomplete plugin with additional support for snippets. It can complete simulatiously from the dictionary, buffer, omnicomplete and snippets. This is the one true plugin that brings Vim autocomplete on par with the best editors.

Use `Ctrl+n` to toggle neocomplcache

- #### Tagbar(tag generation and navigation)

spf13-vim includes the Tagbar plugin. This plugin requires exuberant-ctags and will automatically generate tags for your open files. It also provides a panel to navigate easily via tags

Use ` ,tt ` to toggle neocomplcache

#### 关于在Mac端ctags无效的解决方法

https://brew.sh/

https://github.com/universal-ctags/ctags

https://github.com/universal-ctags/homebrew-universal-ctags

-----

在Windows端，如果想切换到别的盘符进行操作的话,使用

`:NERDTree D:\\`

进行目录的跳转

----
#### Preview: To preview markdown format you need to install bluecloth gem

在使用previewMarkdown的时候出现了
`Preview: To preview markdown format you need to install bluecloth gem`

解决方法：

- `sudo gem install redcarpet`

- `sudo gem install bluecloth`

#### Linux出现的问题

can't find header files for ruby at /usr/lib/ruby/include/ruby.h

解决方法:sudo apt-get install ruby-dev

### 提示找不到tag文件

```
用法:
    1.生成标签文件(cmd到项目的目录中执行)
        在当前目录下(运行$提示符后面的命令):
        $ctags -R .
      -R表示recursive，递归,为当前目录及其子目录中的c文件生成标签文件。最后一个.表示在当前目录。
        运行完当前目录会多一个文件tags,就是c标签的索引文件。
    2.跳转
        1)用vim打开一个已经建过标签的c文件    
        2)ctrl+] 找到光标所在位置的标签定义的地方
        3)ctrl+t 回到跳转之前的标签处
    3.窗口显示方法
         命令Tagbar toggle打开相应的方法窗口显示
    注意：此时运行vim，必须在"tags"文件所在的目录下运行。否则，运行它会找不到"tags"文件，而需要在vim中用":set tags="命令设定"tags"文件的路径。对于一个稍微大点的项目，你可能在任何一个目录下打开vim，然而在每个目录下都生成一个tags文件并不 是个好主意，那么如何解决呢？方法是在.vimrc中增加一行：
        set tags=tags;/
    这是告诉vim在当前目录找不到tags文件时请到上层目录查找。
```
#### 窗口切换快捷键
`Ctrl+w+w`

#### 关闭分屏
```
关闭当前窗口。
Ctrl+W c
关闭当前窗口，如果只剩最后一个了，则退出Vim。
Ctrl+W q
```
#### 打开多个窗口了之后，怎么快速切换
`:buffers 列表  :bn下一个 :bp 上一个  :b17`

#### 取消查找遗留的边框
```
set: nohlseach
```





---

<div align=center>
欢迎关注我的 Github：itgoyo<br>

发现更多有趣好玩的，欢迎关注我的微信公众号

![](/assets/getqrcode.jpeg)
</div>
