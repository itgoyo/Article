---
title: Vim所遇到的各种坑
category: Vim
toc: true
tags: Vim
date: 2018-03-24 00:12:57
author:
keywords:
description:
source_url:
---



## Vim

[详细Vim快捷键大全](https://github.com/itgoyo/Vim-HotKeys)

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
#### VIM编辑多行
```
vim进了多行编辑模式：<ESC>之后按CTRL+V进入visual block模式（列编辑）。光标移到某行行首,进入visual block模式，上下键选择行，按I（i的大写字母），输入##，然后按<ESC>键，这样就在多行行首添加##了。也可以在多行的固定位置添加固定字符。

如果要删除这些##，进入visual block模式，选中这些##，按d即可。
```
### 全局搜索Ack

按键 | 功能|
|:---:|:---:|
| ?	 | 显示键盘映射  |
| o | 打开文件 |
|O  | 	打开文件关闭QuickFix窗口 |
| go |  预览文件，但焦点留在ack搜索结果上|
|t  | 在新标签页打开文件 |
| T | 在新标签页打开但不切换到那个标签页 |
| h | 分屏打开 |
| H | 分屏打开，但焦点停留在ack搜索结果上 |
| v | 竖直分屏打开 |
|gv|竖直分屏打开，但焦点停留在ack搜索结果上|
|q|关闭QuickFix窗口|

#### windows
在Windows下安装它们可以使用Chocolatey，安装方法如下：首先以管理员权限打开cmd窗口，然后运行下列命令,首先以管理员权限打开cmd窗口(管理员那个终端才有效)，然后运行下列命令

```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```
安装完了之后
```
choco install ack
```
#### Mac
```
brew install ack
```
如果出现一下乱码
![](http://omvbl46i3.bkt.clouddn.com/fa55122e9ff4eca89ac684255ab72822.png)

```
'perl' 不是内部或外部命令,也不是可运行的程序
```
下载安装ActivePerl，配置环境变量即可解决此问题。
[下载地址](https://pan.baidu.com/s/1i3GLKAp)

#### SpaceVim

该配色使用的是`gruvbox`

如果想更换成此主题
- 在vimrc文件中增加
```
 "gruvbox主题"
Plugin 'morhetz/gruvbox'
set bg=dark
colorscheme gruvbox

```
然后全局搜索`let g:airline_theme`,改成如下颜色防止颜色不协调
```
  let g:airline_theme = 'dark'
```
终端运行
`PluginInstall`完成之后，重启就可以了

#### 怎么打开最进打开过的文件

启动Vim的时候`Ctrl+o`即可

#### 标记
使用标记可以快速移动。到达标记后，可以用Ctrl+o返回原来的位置。 Ctrl+o和Ctrl+i 很像浏览器上的 后退 和 前进 。

m{a-z}: 标记光标所在位置，局部标记，只用于当前文件。

m{A-Z}: 标记光标所在位置，全局标记。标记之后，退出Vim， 重新启动，标记仍然有效。

`{a-z}: 移动到标记位置。

‘{a-z}: 移动到标记行的行首。

`{0-9}：回到上[2-10]次关闭vim时最后离开的位置。

\`: 移动到上次编辑的位置。"也可以，不过`精确到列，而"精确到行 。如果想跳转到更老的位置，可以按C-o，跳转到更新的位置用C-i。

`”: 移动到上次离开的地方。

`.: 移动到最后改动的地方。

:marks 显示所有标记。

:delmarks a b – 删除标记a和b。

:delmarks a-c – 删除标记a、b和c。

:delmarks a c-f – 删除标记a、c、d、e、f。

:delmarks! – 删除当前缓冲区的所有标记。

:help mark-motions 查看更多关于mark的知识。

#### Linux版本中粘贴系统剪切板内容失败

－　首先，查看vim版本是否支持clipboard
```
vim --version | grep "clipboard"
```
![](http://omvbl46i3.bkt.clouddn.com/80609a3dd8983bf450e9a8448c56b1e4.png)

clipboard前面有一个小小的减号，说明不支持。

##### 如果不支持的话，需要安装图形化界面的vim，或者重新编译vim

```
sudo apt-get install vim-gnome
```

安装完成后再次执行：
```
vim --version | grep "clipboard"
```
发现已经支持clipboard

那么我们的目的是要复制到系统剪切板则需要选中内容后输入命令："+y

粘贴到特定的寄存器也是同理。例如"+p将系统剪切板的内容拷贝到vim中（非编辑模式下）。

### 快速跳转插件Easymotion
[vim-easymotion](https://github.com/easymotion/vim-easymotion)

配置如下：
```
let g:EasyMotion_smartcase = 1
"let g:EasyMotion_startofline = 0 " keep cursor colum when JK motion
map <Leader><leader>h <Plug>(easymotion-linebackward)
map <Leader><Leader>j <Plug>(easymotion-j)
map <Leader><Leader>k <Plug>(easymotion-k)
map <Leader><leader>l <Plug>(easymotion-lineforward)
" 重复上一次操作, 类似repeat插件, 很强大
map <Leader><leader>. <Plug>(easymotion-repeat)
```
- 用法1: 跳转到当前光标前后的位置(w/b)
- 用法2: 搜索跳转(s)
- 用法3: 行级跳转(jk)
- 用法4: 行内跳转(hl)
- 用法5: 重复上一次动作(.)
#### 建议
1.还可以<Leader><leader>f和<Leader><leader>t, 不过建议简单化, 一个<Leader><leader>w/b走天下.

2.如果你不经常使用s, 可以将s改键, nmap s <Plug>(easymotion-s), 这样你只需要输入s就可以进行搜索快速跳转(强迫症表示不能忍....)
具体做法见官方文档

3.默认<leader><leader>作为这个插件的快捷键其实挺好的, 貌似没有其他插件会导致冲突, 还可以配置一整套, 强迫症很满意

4.可以配置2/n个字符的搜索跳转, 更精准, 按需自取(个人觉得太复杂了没必要) 文档和文档

5.这个插件专心做好跳转就好, 没必要把搜索的活给做了

### Vim窗口切换
鼠标在各个窗口间循环移动:
ctrl+w+(小写的 hjkl), "非线性"的跳转的: ctrl_w+t(top : 左上角, +b: bottom, 右下角), p: preview: 上一个子窗口.
set mouse=a 所有all 的状态下都可以使用 鼠标..

窗口本身的位值的移动:
ctrl_w + r: 窗口本身, 不是鼠标指针顺时针 (向下, 向右 移动), R : 则是逆时针反方向(向上, 向左)移动.
ctrl_w+x: 左右上下对应位置的窗口 对调. 要注意窗口必须是 对应的, 如果不对应将无法对换, 比如左边一个大窗口, 右边有两个小的 子窗口, 则左右不能互换.

窗口本身 的位置移动, 而且大小也发生"最大化"变化
Ctrl_w+ HJKL( 注意是大写的字母 H, J, K, L , 表示要按shift才能实现的)... 要注意, 可以通过 windows 窗口 "贴边" 最大化来理解, H和 L 就是 向左或向右 最大化贴边 显示; 而 JK 则是 向上 或 向下 贴边 最大化显示. 最大化后 就不能 再次操作复原窗口了, 其实也没有必要

调整窗口的水平/垂直尺寸?
用ctrl+ w 结合 >, <调整水平尺寸, 用+ - 调整垂直尺寸, 这个是微调. 也可以用纯粹的命令用 :resize +/- n, 或者 vertical resize +/- n (支持命令简写, 但是要能够使命令被唯一确定才行. 通常要用5,10,15, 20的大小间隔来调...太小了没有意义)

除了这些调整/ 遍历鼠标的方法, 还有一个关闭子窗口的问题. 关闭的方式, 除了命令外, 还有窗口关闭 的方式: 用ctrl+w + q(quit), c(close), o(other)等.

### VIM注释插件nerdcommenter
[nerdcommenter](https://github.com/scrooloose/nerdcommenter)
```
使用：  
1、 \cc 注释当前行和选中行  
2、 \cn 没有发现和\cc有区别  
3、 \c<空格> 如果被选区域有部分被注释，则对被选区域执行取消注释操作，其它情况执行反转注释操作  
4、 \cm 对被选区域用一对注释符进行注释，前面的注释对每一行都会添加注释  
5、 \ci 执行反转注释操作，选中区域注释部分取消注释，非注释部分添加注释  
6、 \cs 添加性感的注释，代码开头介绍部分通常使用该注释  
7、 \cy 添加注释，并复制被添加注释的部分  
8、 \c$ 注释当前光标到改行结尾的内容  
9、 \cA 跳转到该行结尾添加注释，并进入编辑模式  
10、\ca 转换注释的方式，比如： /**/和//  
11、\cl \cb 左对齐和左右对其，左右对其主要针对/**/  
12、\cu 取消注释  
```
### It requires Vim 7.3.885 or later with Lua support (“+lua”)
```
方案一：

brew install vim --with-lua

方案二：

brew uninstall vim
brew install luajit
brew install vim --with-luajit
```



---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
