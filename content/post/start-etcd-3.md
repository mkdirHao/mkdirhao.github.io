---
title: "用goreman快速启动三节点etcd"
date: 2022-03-02T17:33:56+08:00
draft: false
---



# 前提准备

1.golang环境

2.安装好etcd

# 安装goreman

```bash
go get github.com/mattn/goreman
```

# 下载Procfile文件

从[etcd源码](https://github.com/etcd-io/etcd/blob/release-3.5/Procfile)下载文件

# 启动

```bash
goreman -f procfile start
```

