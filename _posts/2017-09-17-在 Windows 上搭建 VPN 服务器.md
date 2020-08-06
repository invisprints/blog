---
toc: true
layout: post
description: 在 Windows 上搭建 VPN 服务器
categories: [others]
title: 在 Windows 上搭建 VPN 服务器
comments: true
---

# 在 Windows 上搭建 VPN 服务器
Windows 自带的功能以强大和难用著称，在搭建多次失败后果断转向第三方软件。本文适用于不想装 Linux 系统又有 VPN 需求的同学，同样需要注意，本方法不太适合翻墙。

<!-- more -->

## 介绍
之前在 Windows 上搞文件共享搞了半天都没成功，网上随便下了个脚本一下就成了。最近搞 VPN 也是一直不成，找个第三方软件就很轻松搭建成功。所以原生的真的不一定好。
本文介绍的软件是 SoftEtherVPN，虽然界面丑陋，但是免费且功能强大，算是凑合着用了。

##安装
安装和搭建之类的教程大家去网上找吧，一搜一大片，本篇不继续造轮子了。推荐几篇博文：
[SoftEtherVPN——轻松搭建VPN服务器](https://blog.feixueacg.com/softethervpn-easyvpn/)
[官网](http://www.softether.org/4-docs/2-howto)
其实软件安装完成后是有中文引导的啦，如果不是高级 VPN 需求按照软件的指引来就可以了。

##注意点
这才是本文的精华！！
[软件下载地址](http://www.softether-download.com/cn.aspx?product=softether)
选择软件主流电脑这样选就可以啦。
![-w400](http://ww1.sinaimg.cn/large/a2c78f10gy1fjmm69i81yj20qa0kuq52.jpg)

安装时注意引导程序似乎不会引导本地网桥设置，如果你用的是本机做 VPN 服务器的话需要对本地网桥进行设置。让 VPN 的虚拟网卡和服务器的网卡桥接。这样你就能访问 VPN 服务器所在的外网了。

动态 DNS 针对没有固定 IP 的服务器，开启动态 DNS 服务会给你分配一个SoftEther.ent的二级域名，这样就不需要花钱申请域名或静态 IP 了。需要注意的是，介绍中的 NAT 穿透功能有很大局限性，你可以当这个穿透功能不存在。

VPN Azure 功能是真正实现内网穿透了的，最牛逼的在于他免费！！缺点是只支持 SSTP 协议，苹果家族的就很难使用了。iOS 端目前是不行的，macOS 上可以用 sstp-client 命令行工具或 isstp 图形界面来连接。
sstp-client:

    brew install sstp-client
    
isstp [下载地址](https://www.axot.org/2015/03/03/isstp-a-sstp-client-for-mac-osx/)

默认的 VPN 服务器搭建好后只能使用 SoftEther VPN Client 连接，如果要让 iOS 等移动端连接的话，需要打开 IPsec / L2TP 设置。

另外如果要远程连接需要在管理用户选项中添加用户，这里面功能还是蛮强的。

如果想让 iOS 设备登录处于内网中的 VPN 服务器，可以试试神器 [frp](https://github.com/fatedier/frp)。我稍后会出一篇博文将如何使用 frp 访问内网 VPN 服务器。


