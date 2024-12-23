---
title: 如何用安卓手机写代码
subtitle:
date: 2024-12-13T23:13:00+09:00
slug: 9590ae3
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["termux","安卓"]
categories: ["linux","科技"]
collections: ["develop"]
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRss: false
hiddenFromRelated: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: false
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---
本文讲述了如何在手机上利用termmux来写代码
<!--more-->
## 如何在安卓手机上写代码

首先，安装[Termux](https://termux.dev/en/)

然后启动termux，
安装必要的工具（golang java）
```bash
pkg install git 
pkg install neovim 
pkg install golang 
pkg install openjdk-21
```
然后根据自己需要去配置nvim，懒人可以用[🚀LazyVim](https://www.lazyvim.org/)
```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim

```
然后启动nvim自动加载所需要的插件，然后就可以愉快地在手机上写代码了。