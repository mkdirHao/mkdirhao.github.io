---
title: "位置付きのピング"
date: 2022-02-28T22:04:05+08:00
draft: false
tags: ["日常", "科技"]
categories: ["日常"]
---

# 準備 
go develop envirement > 1.18
install zsh 
# スタート
1.[nali](https://github.com/zu1k/nali)
```bash
go install github.com/zu1k/nali
```
2.zsh

.zshrc これを追加してください。 

```zsh
	ping () {
	   /bin/ping $1 $2 $3 | nali
	}
```

# 最終
```bash
$ ping -c 2 www.baidu.com
PING www.a.shifen.com [百度旗下业务地域负载均衡系统]  (110.242.68.3 [河北省保定市 联通] ) 56(84) bytes of data.
64 bytes from 110.242.68.3 [河北省保定市 联通]  (110.242.68.3 [河北省保定市 联通] ): icmp_seq=1 ttl=52 time=10.3 ms
64 bytes from 110.242.68.3 [河北省保定市 联通]  (110.242.68.3 [河北省保定市 联通] ): icmp_seq=2 ttl=52 time=10.9 ms

```
