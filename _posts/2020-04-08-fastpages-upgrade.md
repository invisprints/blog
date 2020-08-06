---
toc: true
layout: post
description: 如何自动或手动更新 fastpages 到你现有的博客平台上
categories: [fastpages]
title: 更新 fastpages 框架
comments: true
---

# fastpages
fastpages 是一个在开发中的博客平台，因此会不断有新功能出现或修复现有的bug。fastpages 提供了 2 种更新方法，适用于新手的自动化更新和适用于自定义玩家的手动更新。

本文参考 [Upgrading fastpages](https://github.com/fastai/fastpages/blob/master/_fastpages_docs/UPGRADE.md)

## 自动更新
{% include important.html content="自动更新适合那些没有修改网站 HTML 的博客。" %}

### 第一步：使用 Upgrade Template 提出 Issue
在你的博客 repo 中点击 New issue，并点击显示 `[fastpages] Automated Upgrade` 的 Get Started 按钮。
![]({{site.baseurl}}/images/15863377798922.png)

### 第二步: 点击 Submit new issue 按钮

不要对页面做任何改动
![]({{site.baseurl}}/images/15863380296697.png)

### 第三步: 查看自动生成的 PR
接下来 GitHub 会打开 PR 自动更新，PR 界面如下
![]({{site.baseurl}}/images/15863381807304.png)

此时可能会报 error，通常的原因有如下几点：

    - 已是最新版，error 上会显示 "nothing to commit".
    - 之前有未合并的自动更新 PR 请求

你可以在 [fastai 社区](https://forums.fast.ai/) 提问。

### 第四步: 检查并合并 PR

- 仔细检查 PR 中修改的文件，确保你自定义的部分没有被修改。之后点击`Merge pull request` 更新 fastpages。
- 如果 PR 中修改了你自定义的部分或不想被改动的部分，请采用手动更新。


## 手动更新
{% include alert.html text="手动更新适合那些修改过网站 HTML 的博客。" %}

### 直接在 GitHub 网页上修改
进行到自动更新的第四步之后，如果你发现 PR 中修改了你不想修改的内容，可以直接在 `Files changed` 标签页中修改 PR 内容，修改完成后等待 GitHub 冲突检查，解决完可能存在的冲突或失败之后就可以点击`Merge pull request` 更新 fastpages。

### clone 到本地解决
参考 [GitHub - Pull changes from a template repository](https://stackoverflow.com/questions/56577184/github-pull-changes-from-a-template-repository/56577320) 和 [How to sync fastai/fastpages with forked FastPages](https://github.com/fastai/fastpages/issues/163#issuecomment-593766189)

**第一步**

添加远程模版库
```shell
$ git remote add template git@github.com:fastai/fastpages.git 
$ git remote -v 
origin	git@github.com:byteshiva/blog.git (fetch)
origin	git@github.com:byteshiva/blog.git (push)
template	git@github.com:fastai/fastpages.git (fetch)
template	git@github.com:fastai/fastpages.git (push)
upstream	git@github.com:fastai/fastpages.git (fetch)
upstream	git@github.com:fastai/fastpages.git (push)
```

**第二步**

更新
```shell
$ git fetch --all 
Fetching origin
remote: Enumerating objects: 43, done.
remote: Counting objects: 100% (43/43), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 26 (delta 9), reused 24 (delta 7), pack-reused 0
Unpacking objects: 100% (26/26), done.
From github.com:byteshiva/blog
   d7e8201..b67202a  gh-pages   -> origin/gh-pages
Fetching upstream
remote: Enumerating objects: 86, done.
remote: Counting objects: 100% (86/86), done.
remote: Compressing objects: 100% (54/54), done.
remote: Total 86 (delta 38), reused 64 (delta 27), pack-reused 0
Unpacking objects: 100% (86/86), done.
From github.com:fastai/fastpages
   e8bf9f8..bcdbc22  gh-pages   -> upstream/gh-pages
   5b4b79e..8f5a7bc  master     -> upstream/master
Fetching template
From github.com:fastai/fastpages
 * [new branch]      change-docker      -> template/change-docker
 * [new branch]      gh-pages           -> template/gh-pages
 * [new branch]      master             -> template/master
 * [new branch]      pin-jekyll-version -> template/pin-jekyll-version
 * [new branch]      search-highlight   -> template/search-highlight
```

**第三步**

合并
```shell
$ git merge template/master 
fatal: refusing to merge unrelated histories
```
如果出现 `fatal: refusing to merge unrelated histories`，则需要允许不关联的git 历史，参照第四步

**第四步**

```shell
$ git merge template/master --allow-unrelated-histories
CONFLICT (add/add): Merge conflict in index.md
Auto-merging index.md
CONFLICT (add/add): Merge conflict in assets/main.scss
Auto-merging assets/main.scss
CONFLICT (add/add): Merge conflict in assets/js/search.js
Auto-merging assets/js/search.js
CONFLICT (add/add): Merge conflict in _posts/2020-01-14-test-markdown-post.md
Auto-merging _posts/2020-01-14-test-markdown-post.md
CONFLICT (add/add): Merge conflict in _notebooks/2020-02-20-test.ipynb
Auto-merging _notebooks/2020-02-20-test.ipynb
CONFLICT (add/add): Merge conflict in _includes/youtube.html
Auto-merging _includes/youtube.html
CONFLICT (add/add): Merge conflict in _includes/twitter.html
Auto-merging _includes/twitter.html
CONFLICT (add/add): Merge conflict in _includes/notebook_github_link.html
Auto-merging _includes/notebook_github_link.html
CONFLICT (add/add): Merge conflict in _includes/notebook_colab_link.html
Auto-merging _includes/notebook_colab_link.html
CONFLICT (add/add): Merge conflict in _includes/favicons.html
Auto-merging _includes/favicons.html
CONFLICT (add/add): Merge conflict in _config.yml
Auto-merging _config.yml
CONFLICT (add/add): Merge conflict in _action_files/settings.ini
Auto-merging _action_files/settings.ini
CONFLICT (add/add): Merge conflict in _action_files/nb2post.py
Auto-merging _action_files/nb2post.py
CONFLICT (add/add): Merge conflict in _action_files/action_entrypoint.sh
Auto-merging _action_files/action_entrypoint.sh
CONFLICT (add/add): Merge conflict in README.md
Auto-merging README.md
CONFLICT (add/add): Merge conflict in Makefile
Auto-merging Makefile
CONFLICT (add/add): Merge conflict in .github/workflows/setup.yaml
Auto-merging .github/workflows/setup.yaml
CONFLICT (add/add): Merge conflict in .github/workflows/ci.yaml
Auto-merging .github/workflows/ci.yaml
Automatic merge failed; fix conflicts and then commit the result.
```

**第五步**

显示冲突文件
参考 [List conflicted files in git](https://stackoverflow.com/questions/3065650/whats-the-simplest-way-to-list-conflicted-files-in-git)

```shell
git diff --name-only --diff-filter=U
.github/workflows/ci.yaml
.github/workflows/setup.yaml
Makefile
README.md
_action_files/action_entrypoint.sh
_action_files/nb2post.py
_action_files/settings.ini
_config.yml
_includes/favicons.html
_includes/notebook_colab_link.html
_includes/notebook_github_link.html
_includes/twitter.html
_includes/youtube.html
_notebooks/2020-02-20-test.ipynb
_posts/2020-01-14-test-markdown-post.md
assets/js/search.js
assets/main.scss
index.md
```

**第六步**

用你擅长的方式解决冲突

**第七步**

合并并提交更新

```shell
git add . 
git commit -m " commit message comes here "
```
