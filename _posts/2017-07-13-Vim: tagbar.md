---
toc: true
layout: post
description: "Vim: tagbar"
categories: [vim]
title: "Vim: tagbar"
comments: true
---

# Vim: tagbar
tagbar 是一个标签浏览的超有用的插件，它依赖 ctags，因此可以快速查看被 ctags 索引的标签，如函数名，变量、宏定义等。

![](http://ww1.sinaimg.cn/large/a2c78f10ly1fhikhpg536j20hi0bsdh2.jpg)

<!-- more -->

[项目 GitHub](https://github.com/majutsushi/tagbar)
## 安装
在 `.vimrc` 的 vundle 部分添加如下语句即可：

    	Plugin 'majutsushi/tagbar'

然后输入 `:PluginInstall` 安装。

## 使用

在被 ctags 索引的文件中输入 `:TagbarToggle` 即可启动 Tagbar，当然你可以为此设置快捷键。
令我惊讶的是它居然支持鼠标操作！点一下那个三角即可折叠或展开，标签也支持鼠标操作。

快捷键：
感觉常用的就是回车键，跳转到该文件下函数出现部分，其他就没啥常用的了。。。


