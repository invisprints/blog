---
title: "中文搜索"
description: 如何搜索博客中的中文内容
comments: false
toc: false
layout: post
hide: true
categories: [others]
image: https://lunrjs.com/images/moon.jpg
author: "<a href='https://twitter.com/invisprints'>invisprints</a>"
sticky_rank: 1
---

突然发现博客自带的搜索系统居然不支持中文😭😭😭。本博客用的框架是fastpages，拥有目前对 jupyter notebook 的最佳支持，也正因为这点才吸引了笔者。没想到啊，该框架使用的搜索引擎[不支持中文](https://github.com/fastai/fastpages#toggle-search-visibility)，且笔者多天的尝试与探索，尚未找到如何让fastpages支持中文搜索或者另一个让笔者满意的博客平台🙍‍♂️。其实笔者对博客的要求不高，要求数据能导出、尽量直接支持 jupyter notebook、尽量支持双链、能被搜索引擎全文搜索到、良好的中英文支持、可插入交互式图标和外部资源。神奇的是这些功能大部分博客平台都支持大部分，但似乎没有全部都支持的。

## 搜索中文
那么如何搜索博客中的中文内容呢？首先要说明的是英文搜索是博客内支持的，但对于中文搜索，我们需借助外部搜索引擎来完成。

{% include info.html text="搜索特定网站" %}

语法：site:

在相应网站或网域前加上 site:。这里有两种用法，一种是查询具体的网站，比如我想看看本博客中有多少关于“技巧”的内容，输入 `技巧 site:invisprints.github.io` 。如果不输出任何关键词，那么可以了解到这个网站有多少个页面被搜索引擎收录了。