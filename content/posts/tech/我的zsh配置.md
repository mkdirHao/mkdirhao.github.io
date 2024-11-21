---
title: 我的zsh配置
subtitle:
date: 2024-11-21T23:40:47+09:00
slug: 2252437
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["zsh"]
categories: ["环境配置"]
collections: []
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
# 我的zsh配置

<!--more-->
## 主题
[ChesterYue/ohmyzsh-theme-passion: An oh-my-zsh theme.](https://github.com/ChesterYue/ohmyzsh-theme-passion)

![1732200227588](image/我的zsh配置/1732200227588.png)


如果你也想试试这主题的话,按下面的顺序执行吧.

clone repo:
```bash
 git clone https://github.com/ChesterYue/ohmyzsh-theme-passion;
```
copy theme:
```bash
 cp ./ohmyzsh-theme-passion/passion.zsh-theme ~/.oh-my-zsh/themes/passion.zsh-theme;

```
打开 ~/.zshrc 找到 ZSH_THEME 然后改成 ZSH_THEME="passion";
然后让配置生效
```bash
source ~/.zshrc;
```

## 我的zsh插件

```bash

plugins=(git z vi-mode zsh-syntax-highlighting zsh-autosuggestions)

```
zsh-syntax-highlighting zsh-autosuggestions是第三方插件
需要从GitHub clone到本地的,其他的都是内置的功能

```bash
#需要clone的仓库
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```