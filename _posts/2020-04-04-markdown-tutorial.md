---
toc: true
layout: post
description: 如何在 fastpages 上发布 markdown 格式的博文
categories: [markdown]
title: markdown 博文发布教程
---

## 基本设置
fastpages 会将存放在 `_post` 文件夹内的 markdown 文章自动转换成博文，因此你应该将所有的markdown博文放在该文件夹下。
fastpages 也会将存放在 `_notesbooks` 中的 jupyter notebook 和 `_word` 中的 word文章自动转换成博文。因此你的博文应该存放在这三个文件夹内。

所有的博文遵循同一套命名规范，即 `YYYY-MM-DD-filename.ext`，如本篇 markdown 教程的文件名为 `2020-04-04-markdown-tutorial.md`

## 格式
markdown 文章格式遵从 markdown 格式，如不了解，请自行搜索相关内容。

除了标准markdown格式，fastpages还允许你增添一些额外的内容。

### 图片与图注
如果你想显示本地图片，可将图片放入 `images` 文件夹中，然后用 `{{site.baseurl}}/images` 表示图片路径，同时你可以仿照下面格式显示图注
```markdown
![]({{ site.baseurl }}/images/logo.png "fast.ai's logo")
```
![]({{ site.baseurl }}/images/logo.png "fast.ai's logo")

### Tweet 卡片
输入 `{% twitter https://twitter.com/jakevdp/status/1204765621767901185?s=20 %}` 会显示如下内容
{% twitter https://twitter.com/jakevdp/status/1204765621767901185?s=20 %}

### Boxes / Callouts
```
{% include warning.html text="There will be no second warning!" %}
```
{% include warning.html text="There will be no second warning!" %}

```
{% include important.html text="Pay attention! It's important." %}
```
{% include important.html text="Pay attention! It's important." %}
```
{% include tip.html text="This is my tip." %}
```
{% include tip.html text="This is my tip." %}
```
{% include note.html text="Take note of this." %}
```
{% include note.html text="Take note of this." %}


## FrontMatter
FrontMatter 相当于每篇博文的配置文件，它控制着每篇博文该如何展现内容。
在 markdown 博文中，我们会将 FrontMatter 写在文章的开头
```yaml
title: "My Title"
summary: "Awesome summary"
toc: false
comments: true
image: images/some_folder/your_image.png
hide: false
search_exclude: true
categories: [fastpages, jupyter]
metadata_key1: metadata_value1
metadata_key2: metadata_value2
```
FrontMatter允许用户自定义额外选项，但必须遵守YAML格式规则。

可以访问 [fastpages 主页](fastpages.fast.ai) 了解更多内容