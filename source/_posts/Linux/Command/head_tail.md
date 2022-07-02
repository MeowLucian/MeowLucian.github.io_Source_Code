---
title: head && tail
date: 2022-06-21
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

## head
`head -n 10` : 列印最前 10 行

## tail
`tail -n 10` : 列印最後 10 行

`tail -f <file.txt>` : Following mode 持續列印

`tail -n +1 ./*.txt` : Print all *.txt with filename
```bash
==> ./1.txt <==
1
2

==> ./2.txt <==
3
4
```

## 印中間 (head + tail)
```bash
cat file.txt
1
2
3
4
5
6

cat file.txt | tail -n 4 | head -n 2
3
4
```