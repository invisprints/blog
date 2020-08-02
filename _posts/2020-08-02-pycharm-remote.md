---
toc: true
layout: post
description: 用本地 Pycharm 远程调试代码，或者直接使用远程环境
categories: [pycharm]
title: 用 Pycharm 进行远程调试
comments: true
---
## 官方说明

[Remote Debugging with PyCharm](https://www.jetbrains.com/help/pycharm/remote-debugging-with-product.html?keymap=secondary_default_for_macos)

官网详细介绍了如何在本地创建项目，上传本地项目并在远程服务器上调试运行。但对于服务器上已有项目，并没有明确提到该如何操作。

## 调试服务器上的代码

其实方法很简单，在按着上述官网教程创建新项目，在新建项目时选择远程 python 解释器环境环境。之后在 setting 设置检查解释器是否设置正确，没有问题的话找到 Build, Execution, Deployment 节点，在 Deployment 标签页中设置好连接选项（一般就是修改下root path），然后在mappings中将远程路径指向远程项目所在路径。

待 pycharm 建立好本地与远程的映射关系后，在 Tools-Deployment 中选择 Download from，这样就可以把远程代码同步到本地。