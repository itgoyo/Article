---
title: Oh-My-Zsh
category: 编程相关
tags: Program
date: 2017-11-03 17:02:15
author: itgoyo
keywords: oh my ZSH
description:
source_url:
---
## oh my zsh

- curl or wget should be installed

- git should be installed

#### Basic Installation

Oh My Zsh is installed by running one of the following commands in your terminal. You can install this via the command-line with either curl or wget.

- via curl

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

- via wget

`sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"1`

#### Plugins

Once you spot a plugin (or several) that you'd like to use with Oh My Zsh, you'll need to enable them in the .zshrc file. You'll find the zshrc file in your $HOME directory. Open it with your favorite text editor and you'll see a spot to list all the plugins you want to load.

For example, this line might begin to look like this:

`plugins=(git bundler osx rake ruby)`

#### Themes

Robby's theme is the default one. It's not the fanciest one. It's not the simplest one. It's just the right one (for him).

Once you find a theme that you want to use, you will need to edit the ~/.zshrc file. You'll see an environment variable (all caps) in there that looks like:

`ZSH_THEME="robbyrussell"`

To use a different theme, simply change the value to match the name of your desired theme. For example:

```
ZSH_THEME="agnoster" # (this is one of the fancy ones)
# you might need to install a special Powerline font on your console's host for this to work
# see https://github.com/robbyrussell/oh-my-zsh/wiki/Themes#agnoster

```
### 出现乱码解决方式
```
执行以下命令来安装缺失的字体：
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/10-powerline-symbols.conf
wget https://raw.githubusercontent.com/powerline/powerline/develop/font/PowerlineSymbols.otf
sudo mkdir /usr/share/fonts/OTF
sudo cp 10-powerline-symbols.conf /usr/share/fonts/OTF/
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
sudo mv PowerlineSymbols.otf /usr/share/fonts/OTF/
```


Open up a new terminal window and your prompt should look something like this:
![](https://cloud.githubusercontent.com/assets/2618447/6316862/70f58fb6-ba03-11e4-82c9-c083bf9a6574.png)

In case you did not find a suitable theme for your needs, please have a look at the [wiki](https://github.com/robbyrussell/oh-my-zsh/wiki/External-themes) for more of them.

If you're feeling feisty, you can let the computer select one randomly for you each time you open a new terminal window.

`ZSH_THEME="random" # (...please let it be pie... please be some pie..)`






---

<div align=center>
欢迎关注我的 Github：itgoyo<br>

发现更多有趣好玩的，欢迎关注我的微信公众号

![](/assets/getqrcode.jpeg)
</div>
