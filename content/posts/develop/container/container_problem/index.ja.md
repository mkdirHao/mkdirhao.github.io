---
title: コンテナ問題集
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
本文はコンテナに関する様々な問題を記録しています。
<!--more-->

## containerdをコンパイルする方法

> [!Tip]詳細な問題については、公式ドキュメント[containerd/BUILDING.md](https://github.com/containerd/containerd/blob/v2.0.0/BUILDING.md)を参照してください。
### コンパイル前の準備


protoc releaseを/usr/localにインストールします
```bash
wget -c https://github.com/protocolbuffers/protobuf/releases/download/v3.11.4/protoc-3.11.4-linux-x86_64.zip
sudo unzip protoc-3.11.4-linux-x86_64.zip -d /usr/local
```
containerdはBtrfsに依存するため、インストールが必要です。

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

### コンパイルを開始

コードをcloneします
```bash 
git clone https://github.com/containerd/containerd
```
コードディレクトリを開きます

```bash
cd containerd
git checkout v2.0.0
```

コードを少し修正します
```
sed -i 's/app.Name = "containerd"/app.Name = "containerd-hao"/g' cmd/containerd/command/main.go
```

次に
```bash
make
```
バイナリファイルを得ます。コンパイルされたバイナリファイルはbinディレクトリにあります。
```bash
[15:08:26] [~/Desktop/ing/code/containerd] [v2.0.0 ✖] ❱❱❱ ./bin/containerd -v
containerd-hao github.com/containerd/containerd/v2 v2.0.0.m 207ad711eabd375a01713109a8a197d197ff6542.m
```

## Kubernetesをコンパイルする方法

> [!Tip]golang環境が必要です。その他の問題については、k8s公式ドキュメント[kubernetes/build/README.md ](https://github.com/kubernetes/kubernetes/blob/master/build/README.md)をご覧ください。

> [!Tip]私のコンパイル環境はmanjaro linux amd64 | go1.23.4 linux/amd64です。

コードをcloneします

```bash
git clone https://github.com/kubernetes/kubernetes
```
コードディレクトリを開いて1.32バージョンのブランチに切り替えます
 ```bash
  cd kubernetes
  git checkout release-1.32 
```
コンパイルするプラットフォームを修正し、不要なプラットフォームをコメントアウトします
```bash
nvim hack/lib/golang.sh
```

コンパイルします
```bash
  KUBE_BUILD_PLATFORMS=linux/amd64 make all  GOFLAGS=-v GOGCFLAGS="-N -l"
```
コンパイル結果を確認します。コンパイルされたバイナリは_outputフォルダ内にあります。

```bash
 ❱❱❱ ls _output/bin
apiextensions-apiserver  e2e_node.test  go-runner        kube-apiserver           kube-log-runner  kube-scheduler  kubectl          kubelet   mounter
e2e.test                 ginkgo         kube-aggregator  kube-controller-manager  kube-proxy       kubeadm         kubectl-convert  kubemark
```