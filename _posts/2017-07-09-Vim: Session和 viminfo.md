---
toc: true
layout: post
description: Vim: Session和 viminfo
categories: [others]
title: Vim: Session和 viminfo
comments: true
---

# Vim: Session和 viminfo
Session 和 viminfo 用来保存上次的环境，如窗口布局、映射、标记、折叠等。
用了后才发现这玩意太 tm 强大了！用了 vim 这么多年还是对 vim 知之甚少。

![](http://ww1.sinaimg.cn/large/a2c78f10ly1fh9x639t02j20gt0fcdhf.jpg)

<!-- more -->

本文参考此篇[文章](http://easwy.com/blog/archives/advanced-vim-skills-session-file-and-viminfo/)，调整了一些顺序，增删了一些内容，更有助于初学者上手。

##Session
Session 文件会保存当前环境的空口、缓冲区、目录、折叠、映射、标签页等信息。用如下命令创建 Session 文件：

    :mksession [filename]

缺省文件名 `Session.vim`
在重新打开项目的时候，输入如下命令恢复编辑环境

    :source [filename]

**注意！Session 文件无法保存由插件动态生成的窗口，在生成 Session 文件时，需要关闭。**

###Session 进阶
Session 文件中保存的信息由 `sessionoptions` 选项决定。`sessionoption`缺省选项包括`blank, buffers, curdir, folds, help, options, tabpages, winsize`

####Session文件能被 Windows 和 Unix 共同使用
在 Vim 中输入如下命令：

    set sessionoptions+=slash
    set sessionoptions+=unix

`slash`把文件名中的’\’替换为’/’；`unix`会把Session文件的换行符保存成 unix 格式。

####将工作目录设置为 Session 文件所在位置
Session 文件默认将当前目录设为工作目录，如果我们想让当前目录设为 Session 文件所在目录的话，用如下命令：

    :set sessionoptions-=curdir
    :set sessionoptions+=sesdir

`curdir`指示目录为当前目录，`sesdir`指示目录为 Session 文件所在目录。

##viminfo
viminfo 文件保存的信息由`viminfo`选项决定。其缺省选项在 Windows 和 Unix 中不同。viminfo 文件一般保存命令记录、搜索记录、输入记录、寄存器记录和文件标记。
vim 在退出时，默认保存一个 `.viminfo` 文件在用户主目录。使用如下命令手动创建一个 viminfo 文件。

    :wviminfo [filename]

[filename] 不可缺省。
载入 viminfo 文件用如下命令：

    :rviminfo [filepath]



