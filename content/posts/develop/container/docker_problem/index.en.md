---
title: Docker Issue Collection
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
categories: ["linux","docker","tech"]
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

This article records various issues encountered while using docker.

<!--more-->

## How to execute docker commands without sudo?

```bash
cat /etc/group | grep docker # Check for the docker group to see if it exists
```
```bash 
groups # List your user groups to confirm if you are in the docker group
```
```bash

# If the docker group does not exist, add it:
sudo groupadd docker
```
`You need to switch to another user, change user groups, as changes in the current user group will not take effect`
```bash
# Add the current user to the docker group
 sudo usermod -aG docker ${USER}

```bash
# Restart the service
sudo systemctl restart docker 
sudo systemctl daemon-reload
```

## Restart all Docker containers

```bash
docker restart $(docker ps -a -q)

```