---
title: Linux问题集
subtitle:
date: 2024-12-08T12:57:47+09:00
slug: sc6622
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["linux","科技"]
categories: ["linux","科技"]
collections: ["develop"]
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRss: false
hiddenFromRelated: false
summary:
resources:
  - name: featured-image
    src: featured-image.png
  - name: featured-image-preview
    src: featured-image-preview.png
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
本文记录了使用linux遇到的各种问题
<!--more-->

## manjaro linux 中卸载waydroid后，遗留的安卓app图标如何删除？

![alt text](image/1733597806061.png)

## 把go加入环境变量
打开zshrc添加以下变量
```bash
export PATH=$PATH:/usr/lib/go/bin

```
## vscode设置字体
这样前一个英文字体是jetbrains 后一个就是喜欢的中文字体
```json
'JetBrains Mono','LXGW WenKai Mono Screen'
```

## 为ssh登录指定证书

```ssh
Host xxxx # host alias
    Hostname xx.xx.xx # ip address
    User root # user name for log in
    IdentityFile ~/.ssh/id_ed25519 

```