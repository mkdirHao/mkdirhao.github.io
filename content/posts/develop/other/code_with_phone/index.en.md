---
title: How to Write Code on Android Phones
subtitle:
date: 2024-12-13T23:13:00+09:00
slug: 9590ae3
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["termux","android"]
categories: ["linux","technology"]
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
This article tells how to use termmux to write code on mobile phones
<!--more-->
## How to Write Code on Android Phones

First, install [Termux](https://termux.dev/en/)

Then start termux,
install necessary tools (golang java)
```bash
pkg install git 
pkg install neovim 
pkg install golang 
pkg install openjdk-21
```
Then configure nvim according to your needs, lazy people can use [🚀LazyVim](https://www.lazyvim.org/)
```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim

```
Then start nvim to automatically load the required plugins, and then you can happily write code on your phone.