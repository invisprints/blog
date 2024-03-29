---
toc: true
layout: post
description: 打开 macOS 上的 App 后，让 1Password 自动找到对应的账号密码
categories: [apps, password]
title: 1Password 使用技巧
comments: true
image: https://blog.1password.com/posts/2020/big-sur-autofill/header.png
---

- [浏览器自动填充](#浏览器自动填充)
- [本地应用的密码提示](#本地应用的密码提示)
- [查找本地 APP 的包名](#查找本地-app-的包名)
- [在 Edge 浏览器上不工作](#在-edge-浏览器上不工作)

1Password 是一款非常好用的密码管理软件，虽然有着高昂的订阅价格，但其美观的设计和丰富的功能吸引了大批忠实用户。
有关密码管理软件的好坏这里就不再讨论，这篇文章主要来讲一下 1Password 在桌面端的使用技巧。

## 浏览器自动填充
这个我就不用说了，相关的入门介绍多如牛毛。

## 本地应用的密码提示
很多本地应用也需要我们进行登录使用，经常使用 1Password 的老用户会发现 1Password 会识别某些本地 App，这让从不记密码的我们能快速登录这些软件。
![App Store](/blog/images/1password-app-store.png)
如在打开 App Store 后，点击 1Password mini 能自动显示我们的 Apple ID。

但很多时候我们发现 1Password 并不能自动识别，如打开 setapp 后，mini 里面空空如也
![](/blog/images/1password-setapp.png)

但细心人发现在 mini 的建议栏中，1Password 其实已经认出这是 setapp 了，只是它还没有将这个 setapp 与我们账号中的 setapp 账号对上号。

根据 [reddit 论坛](https://www.reddit.com/r/1Password/comments/hk02p7/suggestions_in_apps_for_1password_for_macos/) 的提示，我们需创建一个 URL scheme 链接来指向这个 App， 1Password 方能将账号密码和这个 App 对应上。URL scheme的功能与网址类似，一个记录网上网页的地址，一个记录本地 App 的地址。

## 查找本地 APP 的包名
打开终端，输入以下命令
```osascript
osascript -e 'id of app "App Name"'
```
比如对于 setapp，我们就输入如下命令
```osascript
osascript -e 'id of app "setapp"'

com.setapp.DesktopClient
```
得到的 `com.setapp.DesktopClient` 就是这个 App 的包名了。

有了 App 的包名，我们便可以在 1Password 中添加它的链接

```
app://com.setapp.DesktopClient
```
![](/blog/images/1password-1password.png)

这样下次再打开 setapp 时，1Password 就能找出当前 App 所对应的账号密码了

## 在 Edge 浏览器上不工作
1Password 对 Edge 浏览器的支持仅限于订阅的 1Password X，macOS 上买断版的 1Password 7 并不能直接支持（截止到v7.8版本）

![1Password-could-not-connent](https://i.1password.com/media/could-not-connect.png)

官方文档已经对此提出了[解决方案](https://support.1password.com/could-not-connect/#what-you-should-do)，照着做即可。

需要注意的是如果没有安装 Chrome 浏览器，**必须按照第一步创建相应的文件夹**，即

```shell
 mkdir -p  ~/Library/Application\ Support/Google/Chrome
```

对于 Edge，因为 Microsoft 已经发布 Edge 正式版，而该解决方案页面还没有及时更新，所以在第4步时，需要修改成把 `2bua8c4s2c.com.agilebits.1password.json` 文件粘贴到 `~/Library/Application Support/Microsoft Edge/NativeMessagingHosts/` 位置即可。