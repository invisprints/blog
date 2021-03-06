---
toc: true
layout: post
description: "Vim: 小技巧"
categories: [vim]
title: "Vim: 小技巧"
comments: true
---

# Vim: 小技巧

[toc]

<!-- more -->


最近发现这篇 [readme](https://github.com/VSCodeVim/Vim/blob/master/ROADMAP.ZH.md) 是学 Vim 小技巧的神器，强烈建议参考

## Linux下去掉\^M
1. vi filename
2. :%s/\^M//g
3. \^M 输入方法： ctrl+V ,ctrl+M

若要将`^M`换成回车，则输入下面语句

    :%s/^M/[ctrl-v]+[enter]/g

或

    :%s/^M/\r/g
    
若想查找回车，用户`\n`代替`\r`。

## 转换文件格式
通过输入下面命令查看 vim 支持格式：

    set fileformats
    
转换：
dos->unix:

    set ff=unix

unix->dos:

    set ff=dos


## 自动补全

    <Ctrl-x><Ctrl-k>:字典查找
需要运行`:set spell`启动补全

    <Ctrl-x><Ctrl-l>：整行补全


## 代码折叠
vim中自带了代码折叠功能。
配置foldmethod可以定义折叠方式，有6种可选方式：
 
1. manual //手工定义折叠
2. indent //用缩进表示折叠
3. expr　 //用表达式来定义折叠
4. syntax //用语法高亮来定义折叠
5. diff   //对没有更改的文本进行折叠
6. marker //用标志折叠

我选用syntax来定义折叠，这种方式比较简单，但是当配置完这个值后，你打开代码，就会发现vim默认把所有代码都折叠了，这显然不是我想要的，设置foldlevelstart为99后，打开默认没有折叠。
 

```vim
"使用语法高亮定义代码折叠
set foldmethod=syntax
"打开文件是默认不折叠代码
set foldlevelstart=99
```

这里提供最简单的折叠命令：
zc 关闭折叠
zo 打开折叠
za 打开/关闭折叠互相切换

## 不离开插入模式，粘贴寄存器中的内容
    <C-r>0
    
## 深入理解寄存器
所有复制的内容，不仅被复制到了无名寄存器"",还被复制到复制专用寄存器"0.

## 转换单词大小写

    :guaw
    :gUaw

## 替换

    ：%s/[1]/[2]/gc
%：范围为整个文件，否则为当前行
[1]:查找内容，为空则为上次查找的内容
[2]:替换内容
g：作用于一行所有匹配项，否则为一行第一项
c：手动确认

## 文本排序

假设对下面内容进行排序

    first name,last name,email
    john,smith,john@example.com
    drew,neil,drew@vimcasts.org
    jane,doe,jane@example.com
    
假设我们想基于第二个字段"last name"来重排这些记录。我们可以用`-t',' k2`参数进行排序（有关sort的具体命令请在命令行输入`man sort`查阅），由于文件的第一行是标题信息，我们想把它们保留的文件顶部，因此需要用到范围`:2,$`指定范围

    :2,$!sort -t',' -k2

### 相关知识
这个是在vim中运行Shell命令的一个用法。当给定一个范围时，`:!{cmd}`命令具有特殊含义，由[range]所指定的行会传给{cmd}作为标准输入，又会用{cmd}的输出覆盖[range]内原本的内容

## 数字加减
在普通模式下光标指向该数字，按
    
    ctrl-a  //加1
    ctrl-x  //减1
    

## 选中单词
`aw`这个命令可以表示选中单词的意思，如
复制单词

    yaw
    
转换大写

    gUaw

## vim多文件搜索字符串
### vimgrep
vim自带的`vimgrep`命令除了搜索速度慢，其他的都很好用
vimgrep命令格式如下:

    vimgrep /搜索字符串/gj 文件

上面的`g`和`j`参数都是可选的,

* /g : 加上g参数的话, 如果一行有多个匹配, 那么这些匹配会都出现在搜索结果里, 所以一般不用加`/g`参数;
* /j : 如果不加j参数, 执行完vimgrep会自动跳转到第一个匹配处, 所以一般都会加上`/j`参数;

比如`vimgrep /keyword/j *.php`表示仅在当前目录下的所有php文件里搜索"keyword", 且不自动跳转到搜索结果.
如果也要在子目录递归搜索, `**`表示在当前目录以及子目录递归, 比如`**/*.php`

一些栗子:

* 当前目录下递归搜索: `vimgrep /字符串/j **/*.php`
* 仅当前目录, 不递归: `vimgrep /字符串/g *.php`
* 如果要搜索多个文件扩展名, 用空格分开即可: `vimgrep /字符串/j **/*.cpp **/*.php`
* Linux绝对路径, 递归搜索: `vimgrep /字符串/j /home/user/**/*.cpp`
* Win绝对路径, 递归搜索: `vimgrep /字符串/j D:\home\user/**/*.cpp`

搜索完成后vim会将搜索结果存放在quickfix中，输入命令`:cw`即可打开quickfix

## 搜索
### 不区分大小写
在最后面添加`\c`，如

    /goodday\c

就可以搜索到`GoodDay`，`goodday`等字符串


