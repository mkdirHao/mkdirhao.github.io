---
title: アンドロイド携帯でコードを書く方法
subtitle:
date: 2024-12-13T23:13:00+09:00
slug: 9590ae3
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["termux","アンドロイド"]
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
本文では、携帯電話でtermmuxを使用してコードを書く方法について説明します。
<!--more-->
## アンドロイド携帯でコードを書く方法

まず、[Termux](https://termux.dev/en/)をインストールします。

次にtermuxを起動し、必要なツール（golang java）をインストールします。
```bash
pkg install git 
pkg install neovim 
pkg install golang 
pkg install openjdk-21
```
次に自分のニーズに応じてnvimを設定します。手間を省きたい人は[🚀LazyVim](https://www.lazyvim.org/)を使用できます。
```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim

```
nvimを起動すると必要なプラグインが自動的にロードされ、携帯電話でコードを楽しく書くことができます。