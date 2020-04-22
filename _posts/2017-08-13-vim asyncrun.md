---
toc: true
layout: post
description: vim asyncrun
categories: [vim]
title: vim asyncrun
comments: true
---

# vim asyncrun
利用 Vim8.0 新增的异步特性，可以让很多东西后台运行。瞬间 Vim 可以做很多很牛逼的事情。

![](https://raw.githubusercontent.com/skywind3000/asyncrun.vim/master/doc/screenshot.gif)

<!-- more -->

[项目官网](https://github.com/skywind3000/asyncrun.vim)

##安装
把 `asyncrun.vim` 丢进 `~/.vim/plugin` 或
用 Vundle 安装，在 `vimrc` 合适位置添加下面语句

    	Plugin 'skywind3000/asyncrun.vim'


##简单使用
输入 `:AsyncRun` 后面跟其他命令就相当于在后台进行了。AsyncRun 的命令格式是

    :AsyncRun[!] [options] {cmd} ...

例如：
用 gcc 编译：
    
    :AsyncRun gcc % -o %<
    :AsyncRun g++ -O3 "%" -o "%<" -lpthread 

编译文件：

    :AsyncRun make
    :AsyncRun make -f makefile

搜索关键词：

    :AsyncRun! grep -R word
    :AsyncRun! grep -R <cword>

！的意思是禁止 quickfix 的自动滚动，可以删去看看区别。
<cword> 代表光标下的单词。

生成标签：

    :AsyncRun ctags -R --fields=+S

ctags 在大项目时生成较慢，让它在后台运行最适合不过，cscope 同理。此语句会让 ctags 在当前目录下生成标签。

##进阶
###项目根目录
vim 对于项目的多级目录管理不是很好，Asyncrun 能够设置项目根目录位置，方便项目的编译等操作。

    :AsyncRun -cwd=<root> make
    :AsyncRun make -f $(VIM_ROOT)/Makefile

上面的两条语句都是在项目根目录位置编译，而不是在当前工作目录处编译。其中项目根目录位置可配置。

####查找根目录
AsyncRun 会自动往上层查找含有 `.svn .git .hg .root .project` 的最近目录，并设置为项目根目录。如果没有找到，则自动设置当前工作目录为项目根目录。可用

    :echo asyncrun#get_root('%')

打印项目根目录位置。

####配置根目录
可用如下语句告诉 AsyncRun 如何寻找根目录：

    :let g:asyncrun_rootmarkers = ['.svn', '.git', '.root', '.bzr', '_darcs', 'build.xml']

也可以手动设置根目录位置：

    :let b:asyncrun_root = "/xxxx/path-to-the-project-root"




