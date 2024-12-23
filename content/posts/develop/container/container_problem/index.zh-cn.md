---
title: container问题集
subtitle:
date: 2024-12-08T16:07:59+09:00
slug: ba92ba1
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["container","linux","科技"]
categories: ["container","linux","科技"]
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
本文记录了容器相关各种问题
<!--more-->

## 如何编译containerd

> [!Tip]更多问题请参考官方文档[containerd/BUILDING.md](https://github.com/containerd/containerd/blob/v2.0.0/BUILDING.md)
### 编译前准备


安装 protoc release 到 /usr/local 
```bash
wget -c https://github.com/protocolbuffers/protobuf/releases/download/v3.11.4/protoc-3.11.4-linux-x86_64.zip
sudo unzip protoc-3.11.4-linux-x86_64.zip -d /usr/local

```
containerd 依赖 Btrfs 需要安装它

CentOS/Fedora: 
```bash
yum install btrfs-progs-devel
```
Debian/Ubuntu:
```bash
 apt-get install btrfs-progs libbtrfs-dev
 ```
Debian(before Buster)/Ubuntu(before 19.10):
```bash
 apt-get install btrfs-tools
 ```
manjaro arch linux 

```bash

sudo pacamn -S  btrfs-progs
```

### 开始编译

clone代码
```bash 
git clone https://github.com/containerd/containerd
```
打开代码目录

```bash
cd containerd
git checkout v2.0.0
```

稍微修改一下代码
```
sed -i 's/app.Name = "containerd"/app.Name = "containerd-hao"/g' cmd/containerd/command/main.go
```

然后
```bash
make
```
得到二进制，编译好的二进制文件，位于bin目录
```bash
[15:08:26] [~/Desktop/ing/code/containerd] [v2.0.0 ✖] ❱❱❱ ./bin/containerd -v
containerd-hao github.com/containerd/containerd/v2 v2.0.0.m 207ad711eabd375a01713109a8a197d197ff6542.m
```

## 如何编译Kubernetes

> [!Tip] 需要拥有golang环境，其他问题请看k8s官方文档[kubernetes/build/README.md ](https://github.com/kubernetes/kubernetes/blob/master/build/README.md)

> [!Tip]我的编译环境manjaro linux amd64  | go1.23.4 linux/amd64

clone代码

```bash
git clone https://github.com/kubernetes/kubernetes
```
打开代码目录切换到1.32版本的分支
 ```bash
  cd kubernetes
  git checkout release-1.32 
```
修改编译平台，把用不到的平台注释掉
```bash
nvim hack/lib/golang.sh
```

编译
```bash
  KUBE_BUILD_PLATFORMS=linux/amd64 make all  GOFLAGS=-v GOGCFLAGS="-N -l"
```
查看编译结果,编译完的二进制在_output文件夹内

```bash
 ❱❱❱ ls _output/bin
apiextensions-apiserver  e2e_node.test  go-runner        kube-apiserver           kube-log-runner  kube-scheduler  kubectl          kubelet   mounter
e2e.test                 ginkgo         kube-aggregator  kube-controller-manager  kube-proxy       kubeadm         kubectl-convert  kubemark

```
