---
title: Docker问题集
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

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---
本文记录了使用docker遇到的各种问题
<!--more-->

##  执行docker命令的时候如何能不加sudo?

```bash
cat /etc/group | grep docker # 查找 docker 组，确认其是否存在
```
```bash 
groups # 列出自己的用户组，确认自己在不在 docker 组中
```
```bash

# 如果 docker 组不存在，则添加之：
sudo groupadd docker
```
`需要切换到其他用户，更改用户组，在当前用户组更改后不会生效`
```bash
# 将当前用户添加到 docker 组
 sudo usermod -aG docker ${USER}

```bash
# 重启服务
sudo systemctl restart docker 
sudo systemctl daemon-reload
```

## docker 重启所有容器

```bash
docker restart $(docker ps -a -q)

```