---
title: "Anki 复习参数设定"
description: 修改 Anki 默认复习参数，更好适应不同考试周期或者平时使用
comments: false
toc: false
layout: post
hide: true
categories: [Anki]
image: https://apps.ankiweb.net/img/anki-logo.png
author: "<a href='https://twitter.com/invisprints'>invisprints</a>"
permalink: /drafts
---

Anki 是使用相当广泛的卡片类复习记忆软件，被广泛应用于平常的知识点记忆和各种考试前夕冲刺。很明显，Anki 默认的一套复习参数并不全适用于各类复习计划。因为对于不同的任务，要求的复习时间与强度都是千差万别。本文拟针对一些常用场景，给出一些更适合的参数设定，希望这有助于读者更进一步。

## 默认参数怎么样

首先我们要讨论的就是，默认参数怎么样？弄清楚默认参数的优势和适用范围，我们能节省大量的时间和精力。毕竟乱改参数导致的结果往往是事倍功半。

根据笔者大量的实践经验和一些[资料查询](https://www.zhihu.com/question/429347879/answer/1564939676)，Anki的默认参数足以应对大部分的场景。因此如果你刚接触 Anki 不久或者一点都不了解 Anki 的复习参数，笔者建议先按照默认设定复习，然后在了解了相关参数的含义后再做适当调整。

默认参数参考：[【硬核】参数模拟——每天 40 张新卡片，365 天后我要复习多少？](https://zhuanlan.zhihu.com/p/78398403)

## 优化方案一

{% include info.html text="该方案适用于一年之内考试的同学" %}

方案特点：复习时量大重复次数多，复习中期谨慎添加新卡片

新卡片页面参数

- 数量上限自定
- 毕业间隔Graduating interval —— 1
- 简单间隔Easy ———— 3
- 开始简化Starting ease —— 200%~230%

复习页面参数

- 复习最大值自取
- 简单奖励Easy bonus 100%~120% （越低每日重复频率越低）
- 间隔修饰符Interval modifier
    1. 找插件 “True Retention” 安装后查看Retention是多少。
    2. 自己计算公式：log(预期保留率%) / log(现有保留率%)
    3. 保留率可以理解为你能够记忆的多少，90%保留率可理解为90%的卡片我都能差不多记住。
    4. 0.65-0.95之间，初试请使用0.95（百分比），公式算出数值后自行修改并以公式算出数值为准。

- 最大间隔：30-60天之间。

Lapses失误

- 步伐：5到8之间 或10即原样不动（越低当天重复次数越高）
- 新间隔 0
- 最小间隔 1
- 失误次数 维持原样或调高到10-15

方案参考：[个人使用Anki方法+考试党“专用”参数](https://zhuanlan.zhihu.com/p/24020791)