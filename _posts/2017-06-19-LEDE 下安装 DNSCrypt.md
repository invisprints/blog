---
toc: true
layout: post
description: LEDE 下安装 DNSCrypt
categories: [others]
title: LEDE 下安装 DNSCrypt
comments: true
---

# LEDE 下安装 DNSCrypt
安装完成后加持 IPv6 的话目前就只有 Twitter 上不去了。

<!-- more -->

本文参考[官方文档](https://wiki.openwrt.org/inbox/dnscrypt)完成。

##安装 DNSCrypt

    opkg update
    opkg install dnscrypt-proxy

安装完成后还不能马上使用，需要一些配置。
##配置 DNSCrypt
DNSCrypt 的配置文件在 `/etc/config/dnscrypt-proxy` 不过我们一般不需要修改。

我们需要修改 DNSmasq 的一些配置让它接入 DNSCrypt。
编译文件 `/etc/config/dhcp`
设置这重要三行

```
#   option resolvfile           '/tmp/resolv.conf.auto'
    option noresolv             '1'
    list server                 '127.0.0.1#5353'
```

resolvfile 是使用 ISP 提供的 DNS 服务器，当然要隐去。
noresolv 是禁止使用 `/etc/resolv.conf` 中的 DNS 服务器。
第三行为使用 DNSCrypt。

##启动 DNSCrypt
接下来把 DNSCrypt 加入开机启动并重启 dnsmasq

    /etc/init.d/dnscrypt-proxy enable
    /etc/init.d/dnscrypt-proxy start
    /etc/init.d/dnsmasq restart

可以愉快使用啦！

##备注
如果想分流使用 DNS，国内用国内 DNS，国外用 DNSCrypt，请自行参考官方文档，本博文仅作入门使用。
如果遇到开机无法启动 DNSCrypt，参考官方文档解决。


