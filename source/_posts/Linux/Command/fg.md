---
title: fg
date: 2022-05-21
cover: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
thumbnail: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - Linux
---

## 背景範例程式

* test.sh

```bash
#!/bin/sh

sleep 60
```

## 放到背景
```bash
$ ./test.sh &
[1] 22774
```

## 用 jobs 查看目前 shell 裡的背景程式
```bash
$ jobs
[1]+  Running                 ./test.sh &
```

## 使用 fg 指定 jobs 編號將 test.sh 返回前景(foreground)
```bash
$ fg 1
./test.sh
^C
```