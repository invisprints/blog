---
toc: true
layout: post
description: 在 Microsoft Word 下插入公式，满足大部分论文要求
categories: [Word]
title: Word 下插入公式
comments: true
image: https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Microsoft_Office_2013-2019_logo_and_wordmark.svg/200px-Microsoft_Office_2013-2019_logo_and_wordmark.svg.png
---

Microsoft 365/ 2019 如今已经非常强大，近几年的更新中加入了对 [LaTeX 公式的支持](https://support.microsoft.com/zh-cn/office/编写方程式或公式-1d01cabc-ceb1-458d-bc70-7f9737722702)，基本上可以摆脱对 [mathtype](https://www.dessci.com/en/products/mathtype/) 或其他专业公式编辑器的依赖。

关于在 Word 中插入公式的方法，Microsoft 支持中一文[Word 中使用 UnicodeMath 和 LaTeX 的线性格式公式](https://support.microsoft.com/zh-cn/office/word-中使用-unicodemath-和-latex-的线性格式公式-2e00618d-b1fd-49d8-8cb4-8d17f25754f8)已经阐述得很清楚了，此篇博文在这篇说明上上作以下几点重要补充。

## 推荐使用 LaTeX 编辑公式
目前学术界广泛使用 LaTeX 编辑公式，或者说就笔者所知，目前除了 Microsoft Office 外没有其他软件支持 UnicodeMath，因此从分享的便利性来讲，LaTex 公式更易与他人共享合作。

## 公式字体
尽管 Word 默认支持各种各样的字体，但是公式编辑器默认只支持 Cambria Math 字体，这难以满足大部分论文要求。

以 macOS 版的 2019 Word 为例，在安装好期刊会议要求的公式字体后，在格式-公式选项中将公式的默认字体切换到要求的字体上。Word 公式编辑器支持的字体需满足 Opentype Math 格式。
![](/blog/images/Word-formula-option.png)

## 公式编号
像下图这种公式后面的编号怎么实现呢？
![](/blog/images/Word-formula-index.png)
很简单，在公式末尾添加`#(数字序号)`即可实现。
```
h=F(x_1,x_2,\cdots,x_n)#(7)
```

## 导出
对于使用自定义公式字体的 Word 文档，导出成 pdf 时可能会遇到公式模糊，锯齿感严重等问题。这时只需将导出改成【文件】- 【打印】，然后选择打印机为 Microsoft Print to PDF ，点击打印，即可完美实现 PDF 输出。

## 参考
文中所有链接

[Microoft Word 数学公式完美解决方案](https://github.com/LittleNewton/Replace_MathType)