---
title: ts
date: 2022-06-22
cover: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
thumbnail: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - Linux
---

# Tutorial

## installation
```bash
sudo apt install moreutils
```

## 同時記錄 command 時間
```bash
ping 8.8.8.8 | ts
Jun 21 23:28:52 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
Jun 21 23:28:52 64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=6.00 ms
Jun 21 23:28:53 64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=6.61 ms
Jun 21 23:28:54 64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=4.03 ms
```