---
title: "Ping With Location"
date: 2022-02-28T22:04:05+08:00
draft: false
tags: ["daily", "tech"]
categories: ["daily"]
collections: ["develop"]
---

# prerare
go develop envirement > 1.18
install zsh 
# start
1.[nali](https://github.com/zu1k/nali)
```bash
go install github.com/zu1k/nali
```
2.zsh

add this in .zshrc 
```zsh
	ping () {
	   /bin/ping $1 $2 $3 | nali
	}
```

# final
```bash
$ ping -c 2 www.baidu.com
PING www.a.shifen.com [百度旗下业务地域负载均衡系统]  (110.242.68.3 [河北省保定市 联通] ) 56(84) bytes of data.
64 bytes from 110.242.68.3 [河北省保定市 联通]  (110.242.68.3 [河北省保定市 联通] ): icmp_seq=1 ttl=52 time=10.3 ms
64 bytes from 110.242.68.3 [河北省保定市 联通]  (110.242.68.3 [河北省保定市 联通] ): icmp_seq=2 ttl=52 time=10.9 ms

```
