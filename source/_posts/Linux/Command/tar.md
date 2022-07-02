---
title: tar (tar)
date: 2019-08-04
cover: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
thumbnail: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - Linux
---

tar 指令 教學與筆記。

<!-- more -->

# 說明

打包與壓縮檔案相關指令。

# 參數

* `-c` ： 打包一個 tar 檔案
* `-x` ： 解開一個 tar 檔案
* `-t` ： 檢視 tar 檔案的內容
* `-z` ： 使用 gzip 壓縮
* `-v` ： 顯示建立 tar 檔案的過程
* `-P` ： 使用絕對路徑
* `-f` ： 指定 tar 檔案的檔案名稱。此參數的後面要接檔案名稱，因此要注意參數的順序 (通常是把 f 參數寫在最後一個，或者是與其它參數拆開使用)

# 範例