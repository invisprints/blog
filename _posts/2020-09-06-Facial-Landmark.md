---
toc: true
layout: post
description: 人脸关键点检测简述
categories: [computer vision, keypoints]
title: 人脸关键点检测
hide: true
comments: true
---

# 人脸关键点检测
人脸关键点的目标在于确定预先定义的关键点的位置，如鼻尖、眼角、眉毛等。可靠的关键点是许多复杂视觉任务的基础，它在 3D 人脸重建、人脸姿态估计、人脸识别等领域有重要作用。由于人脸有着复杂的变化，如光照与头部姿势，肤色与脸部表情等，关键点检测仍具有挑战性。

## 常用数据集介绍

### 300W 简介
300W 是一个包含 LFPW，HELEN，AFW 和 IBUG 的复合数据集，每张人脸含有68个关键点。通常将 AFW 的全部图片和 LFPW 与 HELEN 的训练图片当作训练数据，共 3148 张图片。IBUG 的全部图片和 LFPW 与 HELEN 的测试图片当作测试数据，共689张图片。其中来自 LFPW 与 HELEN 的被划分为普通测试集，来自 IBUG 被当作高难度测试集
[300 Faces In-the-Wild Challenge](https://ibug.doc.ic.ac.uk/resources/300-W/)
300W 关键点定义
![300W-landmark](https://ibug.doc.ic.ac.uk/media/uploads/images/300-w/figure_1_68.jpg)

### WFLW 简介
WFLW 数据集包含10000张人脸，其中7500张为训练数据，2500张为测试数据。图片来源于 WIDER FACE 数据集，每张人脸上有98个关键点。测试数据包含姿态、表情、光照、遮挡等多个子类。
WFLW关键点定义
![WFLW-landmark](https://wywu.github.io/projects/LAB/support/WFLW_annotation.png)

## WingLoss

[Wing Loss for Robust Facial Landmark Localisation with Convolutional Neural Networks](https://arxiv.org/abs/1711.06753) 这是一篇于2017年11月发表在 arXiv.org 上的论文，不同于之前广泛研究的级联网络，这篇文章对 loss function 函数下手，是第一篇在人脸对齐上研究损失函数的论文。由于这篇文章相对简单，非常适合作为人脸关键点检测的入门材料。

论文具体内容请阅读原文或上网搜素，这里不再赘述。

### WingLoss 复现
请跳转到下一篇博文

## 参考材料
[Wing Loss for Robust Facial Landmark Localisation with Convolutional Neural Networks](https://arxiv.org/abs/1711.06753)
[深度学习之人脸图像处理](https://u.jd.com/z6hXa0)