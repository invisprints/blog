---
toc: true
layout: post
description: 总结 subconverter 的常用情景
categories: [subconverter, Heroku]
title: subconverter 实用案例
comments: true
image: https://miro.medium.com/max/1400/1*fIjRtO5P8zc3pjs0E5hYkw.png
---

# subconverter
subconverter 是在各种订阅格式之间进行转换的实用程序

本文已更新到兼容 subconverter v0.6.4，更新日期 2020-11-08

[github 项目地址](https://github.com/tindy2013/subconverter/blob/master/README-cn.md)

[公共 API](https://gfwsb.114514.best/)

## 常用案例
关于 subconverter 的用法在 readme 中已经给出详细的说明与部分简单用法了，本文将继续扩充一些 readme 中没有涉及到的 example。

### 云端运行
readme 中介绍了大量本地运行的情况，但是对于众多用户来说我们并不希望在本地一直运行着 subconverter，我们希望有个云端 API。每当我们更新云端数据时，所有的更新就会自动 update 到我们的手机、电脑、路由器中，十分方便。

最简单的方法是使用[公共 API](https://gfwsb.114514.best/)，但有些人担心隐私机场泄漏问题，因此我们需要自己搭建一个云端转换器。

[Heroku](heroku.com) 是一个在云端部署 web app 的平台，它托管于 Amazon 云且与 Github 深度集成。 subconverter 作者也提供了一键部署到 Herokuapp 的模版 [heroku-subconverter](https://github.com/tindy2013/heroku-subconverter)，这里你可以一键部署到你的 Heroku 平台上，然后就可以使用 subconverter readme 中的简易用法。

但简易用法的链接通常十分冗长且难以记忆，在出现这种情况后，我们就需要利用 subconverter 提供的[配置档案](https://github.com/tindy2013/subconverter/blob/master/README-cn.md#配置档案)简化操作

---

**step 1**
既然需要用到配置档案，我们自然就不能使用 heroku 一键部署的功能（不然怎么添加本地文件？）。在[heroku-subconverter](https://github.com/tindy2013/heroku-subconverter)页面，点击 `use this template` 将该模版 copy 自己的仓库下，这里建议将仓库权限设置为 `Private`，不然全世界人们都可以看见你的配置档案了。

**step 2**
所有的配置档案都应保存在 base 文件夹中，因为 base 文件夹是软件运行的根目录。

修改 README.md 中的部署地址为 https://heroku.com/deploy?template=自己的仓库地址，这样在配置完成后点击 README 中 `Deploy to Heroku` 即可将服务部署在 Heroku 上。

**step 3**
根据你的喜好在 base 中添加相应的配置档案。
配置档案参照[subconverter 说明](https://github.com/tindy2013/subconverter/blob/master/README-cn.md)进行配置。

{% include info.html text="建议在本地调试好后再上传云端。" %}

**step 4**
在 Heroku 中关联 GitHub 的方法已经失效。每次修改完成后都需点击 `Deploy to Heroku` 将 Docker 部署到云端。

**step 5**
至此部署云端 API 基本完成，这里有几个注意事项。
* 云端的根目录就是 base 目录。比如你在 base 下有一个`example_profile.ini`配置文件，路径就是`https://***.herokuapp.com/getprofile?name=example_profile.ini&token=***`
* 需修改你在`pref.ini`的`managed_config_prefix`路径，将其指向云端路径
* 为了安全考虑，建议修改`token`默认密码
* 订阅时直接在订阅链接里输入云端 API 地址即可，如`https://***.herokuapp.com/getprofile?name=example_profile.ini&token=***`
* 你可以建立多个配置文件，让不同软件使用不同配置文件。

### 自定义规则
在 subconverter 说明文档中对自定义规则有少许描述，这里给出一个完整的自定义规则配置过程。
subconverter 的默认配置规则为神机规则，里面包含了大量与广告相关的规则。下面我们就以去除神机规则中的广告拦截规则为例。

在配置档案中，我们可以通过添加`config`参数加载额外的配置文件。当然我们也可以通过直接修改 `pref.ini` 实现。

```ini
[Profile]
target=clash
url=ss://Y2hhY2hhMjAtaWV0Zi1wb2x5MTMwNTpwYXNzd29yZA@www.example.com:1080#Example
; 加载位于 config/example_external_config.ini 的配置文件
config=config/example_external_config.ini
```

仿照默认的配置文件编辑自定义配置文件，默认配置文件在`pref.ini`由`surge_ruleset`和`custom_proxy_group`指出。
比如我们不想添加广告过滤。
```ini
[custom]
; 自定义策略组
custom_proxy_group=🔰 节点选择`select`[]♻️ 自动选择`[]🎯 全球直连`.*
custom_proxy_group=♻️ 自动选择`url-test`.*`http://www.gstatic.com/generate_204`300
custom_proxy_group=🌍 国外媒体`select`[]🔰 节点选择`[]♻️ 自动选择`[]🎯 全球直连`.*
custom_proxy_group=🌏 国内媒体`select`[]🎯 全球直连`[]🔰 节点选择
custom_proxy_group=Ⓜ️ 微软服务`select`[]🎯 全球直连`[]🔰 节点选择`.*
custom_proxy_group=📲 电报信息`select`[]🔰 节点选择`[]🎯 全球直连`.*
custom_proxy_group=🍎 苹果服务`select`[]🔰 节点选择`[]🎯 全球直连`[]♻️ 自动选择`.*
custom_proxy_group=🎯 全球直连`select`[]DIRECT
custom_proxy_group=🐟 漏网之鱼`select`[]🎯 全球直连`[]🔰 节点选择`[]♻️ 自动选择`.*

;Options for custom rulesets
; 自定义规则片段
enable_rule_generator=true
overwrite_original_rules=true

surge_ruleset=🎯 全球直连,rules/LocalAreaNetwork.list
surge_ruleset=Ⓜ️ 微软服务,rules/MSServices.list
surge_ruleset=🎯 全球直连,rules/ConnersHua/Surge/Ruleset/Unbreak.list
surge_ruleset=🌍 国外媒体,rules/ConnersHua/Surge/Ruleset/GlobalMedia.list
surge_ruleset=🌏 国内媒体,rules/lhie1/Surge/Surge 3/Provider/AsianTV.list
surge_ruleset=📲 电报信息,rules/ConnersHua/Surge/Ruleset/Telegram.list
surge_ruleset=🔰 节点选择,rules/ConnersHua/Surge/Ruleset/Global.list
surge_ruleset=🍎 苹果服务,rules/ConnersHua/Surge/Ruleset/Apple.list
surge_ruleset=🎯 全球直连,rules/ConnersHua/Surge/Ruleset/China.list
surge_ruleset=🎯 全球直连,rules/NobyDa/Surge/Download.list
surge_ruleset=🎯 全球直连,[]GEOIP,CN
surge_ruleset=🐟 漏网之鱼,[]FINAL
```
至此在调用配置档案时，会调用自定义配置档案并覆盖掉原始配置档案。

### 管理订阅节点
如果多份配置文件都要使用同一套订阅节点，比如我同时用到 Clash，surge，quanx，shadowrocket 等，在每处配置文件的 `url` 处都加上订阅节点显得有些繁琐，特别是节点有修改时就很容易出错。

方法是将节点信息添加进`pref.ini`中，这是全局配置文件，根据需求在`default_url`或`insert_url`添加相应的节点信息即可。支持如下格式：
- 机场订阅：https://dler.cloud/subscribe/ABCDE?surge=ss
- 节点链接：ss://YWVzLTEyOC1nY206dGVzdA==@192.168.100.1:8888#Example1
- 文件路径：config/nodes.txt

其中文件里的节点内容支持 Clash 和 Quanx 格式（其它格式可能也支持，但我没有测试）

## 小结
subconverter 还有很多高级玩法，这篇文章只是抛砖引玉补充一些基础自定义案例，方便读者了解部分高级 API 的使用。