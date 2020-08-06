---
toc: true
layout: post
description: Wireshark 学习笔记
categories: [others]
title: Wireshark 学习笔记
comments: true
---

# Wireshark 学习笔记

## 常见问题
### 在 macOS 环境下无法读取网卡信息
- 方法一：在命令行中以管理员权限打开 wireshark `sudo wireshark`。
- 方法二：在命令行中输入如下命令 `chmod 777 /dev/bpf*` 之后重启即可。

