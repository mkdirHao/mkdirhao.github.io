---
title: Container Issue Collection
subtitle:
date: 2024-12-08T16:07:59+09:00
slug: ba92ba1
draft: false
description:
keywords:
license:
comment: true
weight: 0
tags: ["container","linux","technology"]
categories: ["container","linux","technology"]
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
This article records various issues related to containers.
<!--more-->

## How to Compile containerd

> [!Tip] For more issues, please refer to the official documentation [containerd/BUILDING.md](https://github.com/containerd/containerd/blob/v2.0.0/BUILDING.md)
### Preparation Before Compilation

Install protoc release to /usr/local
```bash
wget -c https://github.com/protocolbuffers/protobuf/releases/download/v3.11.4/protoc-3.11.4-linux-x86_64.zip
sudo unzip protoc-3.11.4-linux-x86_64.zip -d /usr/local

```
containerd depends on Btrfs, which needs to be installed

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
Manjaro Arch Linux

```bash

sudo pacman -S  btrfs-progs
```

### Start Compilation

Clone the code
```bash 
git clone https://github.com/containerd/containerd
```
Open the code directory

```bash
cd containerd
git checkout v2.0.0
```

Make a slight modification to the code
```
sed -i 's/app.Name = "containerd"/app.Name = "containerd-hao"/g' cmd/containerd/command/main.go
```

Then
```bash
make
```
Get the binary, the compiled binary file is located in the bin directory
```bash
[15:08:26] [~/Desktop/ing/code/containerd] [v2.0.0 ✖] ❱❱❱ ./bin/containerd -v
containerd-hao github.com/containerd/containerd/v2 v2.0.0.m 207ad711eabd375a01713109a8a197d197ff6542.m
```

## How to Compile Kubernetes

> [!Tip] A golang environment is required, for other issues, please refer to the k8s official documentation [kubernetes/build/README.md](https://github.com/kubernetes/kubernetes/blob/master/build/README.md)

> [!Tip] My compilation environment is Manjaro Linux amd64 | go1.23.4 linux/amd64

Clone the code

```bash
git clone https://github.com/kubernetes/kubernetes
```
Open the code directory and switch to the 1.32 version branch
 ```bash
  cd kubernetes
  git checkout release-1.32 
```
Modify the compilation platform, comment out the platforms that are not needed
```bash
nvim hack/lib/golang.sh
```

Compile
```bash
  KUBE_BUILD_PLATFORMS=linux/amd64 make all  GOFLAGS=-v GOGCFLAGS="-N -l"
```
Check the compilation results, the compiled binaries are in the _output folder

```bash
 ❱❱❱ ls _output/bin
apiextensions-apiserver  e2e_node.test  go-runner        kube-apiserver           kube-log-runner  kube-scheduler  kubectl          kubelet   mounter
e2e.test                 ginkgo         kube-aggregator  kube-controller-manager  kube-proxy       kubeadm         kubectl-convert  kubemark
```