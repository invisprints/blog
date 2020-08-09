---
toc: true
layout: post
description: 自己编译 code server，在网页上进行远程开发
categories: [apps]
title: 自编 code server
comments: true
---

code server 已经有相当一段时间没有发布编译版本，最近的一次 release 在6月5日。 这段期间 VS Code 已经到 1.47 了，因此我自己编译了 code server，这对编译 vscode 也有不少借鉴意义。

## 搭建环境
首先按照 [VS Code 编译环境要求](https://github.com/Microsoft/vscode/wiki/How-to-Contribute#prerequisites) 配置相应环境，要注意 python 的版本是 2.7， python 3 是无法编译 VS Code 的。
另外按照说明有可能会漏掉`pkg-config`包，这个也需安装好
```shell
sudo apt install pkg-config
```
然后按照 [code server 的要求](https://github.com/cdr/code-server/blob/master/doc/CONTRIBUTING.md)配置好其余的环境，基本上就可以到位了。

## 网络问题
只有国内网是很难编译成功的，建议编译时开启随意访问国外的网站的权限。

## release
code server 我自己编译的 release 在[这里下载](https://github.com/invisprints/my-prebuild-release/releases/tag/1.1)