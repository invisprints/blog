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
以下内容引用自MWeb

### 标题

Markdown 语法：

```
# 第一级标题 `<h1>` 
## 第二级标题 `<h2>` 
###### 第六级标题 `<h6>` 
```

效果如下：

# 第一级标题 `<h1>` 
## 第二级标题 `<h2>` 
###### 第六级标题 `<h6>` 



### 强调

Markdown 语法：

```
*这些文字会生成`<em>`*
_这些文字会生成`<u>`_

**这些文字会生成`<strong>`**
__这些文字会生成`<strong>`__
```

效果如下：

*这些文字会生成`<em>`*
_这些文字会生成`<u>`_

**这些文字会生成`<strong>`**
__这些文字会生成`<strong>`__

### 换行

四个及以上空格加回车。

### 列表

#### 无序列表

Markdown 语法：

```
* 项目一 无序列表 `* + 空格键`
* 项目二
* 项目二的子项目一 无序列表 `TAB + * + 空格键`
* 项目二的子项目二
```

效果如下：

* 项目一 无序列表 `* + 空格键`
* 项目二
* 项目二的子项目一 无序列表 `TAB + * + 空格键`
* 项目二的子项目二

#### 有序列表

Markdown 语法：

```
1. 项目一 有序列表 `数字 + . + 空格键`
2. 项目二 
3. 项目三
    1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
    2. 项目三的子项目二
```

效果如下：

1. 项目一 有序列表 `数字 + . + 空格键`
2. 项目二 
3. 项目三
    1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
    2. 项目三的子项目二

#### 任务列表（Task lists）

Markdown 语法：

```
- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务 `- + 空格 + [x]`
```

效果如下：

- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务 `- + 空格 + [x]`

### 图片

Markdown 语法：

```
![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif)
格式: ![Alt Text](url)
```

效果如下：

![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif)

### 链接

Markdown 语法：

```
email <example@example.com>
[GitHub](http://github.com)
自动生成连接  <http://www.github.com/>
```

效果如下：

Email 连接： <example@example.com>
[连接标题Github网站](http://github.com)
自动生成连接像： <http://www.github.com/> 这样

### 区块引用

Markdown 语法：

```
某某说:
> 第一行引用
> 第二行费用文字
```

效果如下：

某某说:
> 第一行引用
> 第二行费用文字

### 行内代码

Markdown 语法：

```
像这样即可：`<addr>` `code`
```

效果如下：

像这样即可：`<addr>` `code`

### 多行或者一段代码

Markdown 语法：

    ```js
    function fancyAlert(arg) {
        if(arg) {
        $.facebox({div:'#foo'})
        }
    
    }
    ```

效果如下：

```js
function fancyAlert(arg) {
    if(arg) {
    $.facebox({div:'#foo'})
    }

}
```


### 表格

Markdown 语法：

```
第一格表头 | 第二格表头
--------- | -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格
```

效果如下：

第一格表头 | 第二格表头
--------- | -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格


### 删除线

Markdown 语法：

加删除线像这样用： ~~删除这些~~

效果如下：

加删除线像这样用： ~~删除这些~~

### 分隔线

以下三种方式都可以生成分隔线：


```
***

*****

- - -
```

效果如下：

***

*****

- - -


### 脚注（Footnote）

Markdown 语法：

```
这是一个脚注：[^sample_footnote]
```

效果如下：

这是一个脚注：[^sample_footnote]

[^sample_footnote]: 这里是脚注信息


### 注释和阅读更多

<!-- comment -->
<!-- more -->

Actions->Insert Read More Comment *或者* `Command + .`
**注** 阅读更多的功能只用在生成网站或博客时，插入时注意要后空一行。

### TOC

Markdown 语法：

```
[TOC]
```

效果如下：

[TOC]


除了标准markdown格式，fastpages还允许你增添一些额外的内容。

### 图片与图注
如果你想显示本地图片，可将图片放入 `images` 文件夹中，然后用 `{{site.baseurl}}/images` 表示图片路径，同时你可以仿照下面格式显示图注
```markdown
![]({{ site.baseurl }}/images/logo.png "fast.ai's logo")
```
![]({{ site.baseurl }}/images/logo.png "fast.ai's logo")

### Tweet 卡片


输入 `\{% twitter https://twitter.com/jakevdp/status/1204765621767901185?s=20 %\}` 会显示如下内容


{% twitter https://twitter.com/jakevdp/status/1204765621767901185?s=20 %}


### Boxes / Callouts

    {% include alert.html text="You can include alert boxes" %}

{% include alert.html text="You can include alert boxes" %}

    {% include info.html text="You can include info boxes" %}

{% include info.html text="You can include info boxes" %}


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