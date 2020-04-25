---
toc: true
layout: post
description: 搭建一个轻量、少插件的 vim 终端环境
categories: [vim]
title: Vim 搭建教程
comments: true
---

# Vim 搭建教程
号称编辑器之神的 Vim 有着极为强大的扩展能力和陡峭的学习曲线，本文在尽可能少装插件的情况下打造较为舒适的 Vim 开发环境。

## 本文理念
在开始前先回答下面几个问题，也是写本篇博文的理念。

- 为什么用 Vim
- 为什么用 Vim 8

目前编辑器领域百花齐放，VS Code 的表现尤其亮眼，为什么我们还要用 Vim 呢？
其实目前仍有部分领域是 Vim 擅长而 VS Code 和 Sublime 3 之类不擅长的——比如 ssh 远程编辑。本篇博文的目的也是打造适合远程编辑的 Vim 环境。至于其他领域，VS Code 不香吗？

关注 Vim 的人也应该知道，NeoVim 在近几年的表现尤为亮眼，但是本文并不打算采用 NeoVim 作为远程开发环境。原因有二，一是 NeoVim 尚不稳定，还处于快速开发期，在工业场景下还是成熟的 Vim 8 更为可靠；二是 NeoVim 目前配置比较复杂，等普通人配置好了我都可以拿 VS Code 远程编辑了，不够轻量。这也是为什么我们不打算装太多插件的原因，IDE 不香吗？

## 搭建
1. 下载`.vimrc`配置文件
2. 安装 Plug 插件管理器
3. 安装插件
4. 开始远程编辑

这是笔者多年经验精简下来的`.vimrc`配置文件，没有多余的快捷键配置，零上手难度。

```vim
" Configuration file for vim
" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
set nocompatible              " 去除VI一致性,必须

"===========设置包括vundle=========
call plug#begin('~/.vim/plugged')
" Github上的插件
" 格式为 Plug '用户名/插件仓库名'
	Plug 'majutsushi/tagbar'
	Plug 'joshdick/onedark.vim'
	Plug 'neoclide/coc.nvim', {'branch': 'release'}
" 你的所有插件需要在下面这行之前
call plug#end()            " 必须
"
" 简要帮助文档
" :PluginList       - 列出所有已配置的插件
" :PluginInstall    - 安装插件,追加 `!` 用以更新或使用 :PluginUpdate
" :PluginSearch foo - 搜索 foo ; 追加 `!` 清除本地缓存
" :PluginClean      - 清除未使用插件,需要确认; 追加 `!` 自动批准移除未使用插件

"=======主题等设置========
syntax on
colorscheme onedark

set hlsearch  "高亮匹配项
set autoindent                " always set autoindenting on
set nu        " 显示行号
set relativenumber   " 相对行号
set showmatch        " 设置匹配模式，显示匹配的括号
set tabstop=4        " 设置制表符(tab键)的宽度
set softtabstop=4     " 设置软制表符的宽度
set shiftwidth=4    " (自动) 缩进使用的4个空格
set scrolloff=3		"保持最后3行可见
set guifont=SourceCodeProForPowerline-Regular:h16
set backspace=indent,eol,start
set cursorline "高亮当前行
set cursorcolumn "高亮当前列

"=====系统设置=====
set foldmethod=indent  "使用缩进定义代码折叠

set foldlevelstart=99 "默认代码不折叠
"set tags=tags; "不断递归向上查找tags
set showcmd    "显示正在输入的命令
set clipboard=unnamed "共用系统剪贴板 ubuntu:unnamedplus
set fileencodings=ucs-bom,utf-8,cp936,gb18030,big5,euc-jp,euc-kr,latin1

"===插件配置====
"====tagbar
nmap <F8> :TagbarToggle<CR>
let g:tagbar_auto_faocus=1
```

插件只有3个，tagbar 是显示代码类和变量的查看器，需要配合 ctags 使用，ctags 安装也很简单，[ctags 安装教程](https://github.com/universal-ctags/ctags#the-latest-build-and-package)
onedark 是一个 vim 配色方案，读者也可按照自己的喜好选择。
coc.nvim 是自动补全平台插件，不过我发现自带的通用补全已经很不错了，需要安装 Nodejs

所有的配置都有注释，已经算是很容易理解的了。有人说 SpaceVim 也很简单啊，当然如果读者熟悉 SpaceVim 的话我也很推荐。能简单就不要复杂，能自动化就不要手动操作。

Plug 的安装和使用参看 [plug 安装教程](https://github.com/junegunn/vim-plug#installation)

## 总结
笔者接触 Vim 8年有余，从最开始的把 Vim 打造成 IDE 到后来的用 Vim 建立 QQ 聊天框，折腾了一圈下来发现自己并没有什么收获，反而是在挖掘各种奇技淫巧方案耗费了大量时间。Vim 并不是什么 IDE 之神或者 Linux 高手标志，它只是处理文件的利器而已。因此相比于装一堆插件或写超长配置把 Vim 打造成 IDE，还不如在 IDE 里装个 Vim 插件来的省时省力。当然这是我个人的想法，读者完全可以按照自己的兴趣打造自己的 Vim，毕竟这是 Vim 的魅力所在。