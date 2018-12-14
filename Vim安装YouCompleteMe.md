---
title: Vim安装YouCompleteMe
toc: true
category: 编程相关
tags: Program
date: 2018-05-10 22:23:35
author:
keywords:
description:
source_url:
---

本人使用的是[Macvim](https://macvim-dev.github.io/macvim/)使用的配置是[spf-13](https://github.com/spf13/spf13-vim)

虽然里面已经集成黑多插件了，但是由于最近本人折腾起了C\C++,然后想在Vim上面进行基本的代码编辑，主要是一开始项目比较小，都是运行一些简单的Demo，所以在vim上面基本能满足需求，自己也在Mac上面安装VS code然后配置了C\C++的开发环境。至于为什么还是想要在Vim上面进行代码编辑呢？只是本人自己想使用Vim而已，也趁这个机会，提高自己在Vim上面的编码效率，还有Vim的一般使用，也没特别的需求。

## 步骤

### 配置.vimrc
在文件的最后加上一下内容
```
Plugin 'Valloric/YouCompleteMe'
```
然后在Vim里面运行以下命令安装YouCompleteME
```
PluginInstall
```
整个过程比较久，请耐心稍等，直到项目下载完成，整个项目下载下来有好几百M。

### 安装cmake

```
brew install cmake
```

### 下载LLVM+Clang

下载地址：`http://llvm.org/releases/download.html`


- Clang for x86_64 Ubuntu 14.04 (.sig)
- Clang for x86_64 Ubuntu 16.04 (.sig)
- Clang for Mac OS X (.sig)

自己看好自己的系统下载对应的软件，别下载错了

下载之后解压到`~/ycm_temp/llvm_root_dir` 看好目录名称，你自己随意，但是我后面的代码按这个目录来进行运行，所以如果你不是这个名字，你自己在命令行中自行改正。

### 正式编译安装ycm_core

在根目录下创建一个新文件夹，其中将放置构建文件。 运行以下命令:
```
cd ~
mkdir ycm_build
cd ycm_build
```

需要C族语言的语义支持，还得分几种情况：
- 从llvm的官网下载了LLVM+Clang的二进制包(也就是上面下载的东西)**本人使用这种方法**

解压到：~/ycm_temp/llvm_root_dir

文件夹中含有`bin`,`lib`,`include`等文件夹

然后执行:
```
cmake -G "Unix Makefiles" -DPATH_TO_LLVM_ROOT=~/ycm_temp/llvm_root_dir . ~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp
```

自己看清楚你的`YouComplete`是不是在上面的目录

- 如果想用系统的libclang:

```
cmake -G "Unix Makefiles" -DUSE_SYSTEM_LIBCLANG=ON . ~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp
```

- 如果想用自定义的libclang:

```
cmake -G "Unix Makefiles" -DEXTERNAL_LIBCLANG_PATH=/path/to/libclang.so . ~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp
```

至此，`makefile`已生成,运行以下命令

`cmake --build . --target ycm_core --config Release`

最后如果你想添加C的支持的话,进入目录

~/.vim/bundle/YouCompleteMe/master/

```
./install.py --clang-completer
```

最后在`.vimrc`添加以下内容

```
let g:ycm_global_ycm_extra_conf = '~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp/ycm/.ycm_extra_conf.py'
```
请自行查看你的目录是不是上面的目录，如果不是的话请自行改成自己本地的路径

然后重启Vim，尝试编辑代码一下,如果出现左边那种`>>`则表示安装成功了

![](http://omvbl46i3.bkt.clouddn.com/95b2ff1939587e751d59614d6a5f73a1.png)

如果没有这样子的`>>`的箭头，则在Vim运行一下命令

```
:YcmRestarServer
```
即可出现箭头。

---

<div align=center>
发现更多更好玩的，欢迎关注我的微信公众号:toolpool

![](/img/qrcode.jpg)
</div>
