---
title: Dockerの問題集
subtitle:
date: 2024-12-08T12:52:22+09:00
slug: 306ca09
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["linux","docker"]
categories: ["linux","docker","科技"]
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

# フロントマターの詳細については、こちらをご覧ください: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---
本文では、dockerを使用する際に遭遇する様々な問題を記録します。
<!--more-->

## dockerコマンドを実行する際にsudoを使わずに実行する方法は？

```bash
cat /etc/group | grep docker # docker グループを検索し、存在を確認
```
```bash 
groups # 自分のユーザーグループをリストアップし、docker グループに自分が所属しているか確認
```
```bash

# docker グループが存在しない場合は、追加します：
sudo groupadd docker
```
`他のユーザーに切り替え、ユーザーグループを変更する必要があります。現在のユーザーグループの変更後では反映されません`
```bash
# 当該ユーザーをdockerグループに追加します
 sudo usermod -aG docker ${USER}

```bash
# サービスを再起動します
sudo systemctl restart docker 
sudo systemctl daemon-reload
```

## dockerですべてのコンテナを再起動する

```bash
docker restart $(docker ps -a -q)

```