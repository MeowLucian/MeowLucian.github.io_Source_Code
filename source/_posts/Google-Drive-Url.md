---
title: Google 雲端硬碟外連 Url 並下載 (Google Drive Url && Download)
date: 2018-03-18
cover: /images/Google-Drive-Url/Google-Drive-Url-banner.jpg
thumbnail: /images/Google-Drive-Url/Google-Drive-Url-banner.jpg
toc: true
categories: Learning-Note-學習筆記
tags:
     - Drive
     - Url
---

找出 Google 雲端硬碟的資料外連網址 Url 並下載。

<!-- more -->

# 找出外連網址 (適用 100M size 以下檔案)

開啟共用後，網址由以下組成：

* https<span>://drive<span>.google<span>.com/file/d/`id`/view?usp=sharing

其中 `id` 為33個英文+數字符號等組成。

將網址改成以下：

* https<span>://drive<span>.google<span>.com/uc?export=download&id=`id`

即可將雲端資料使用於個人網頁、部落格顯示。

# gdown

## Installation
```bash
pip install gdown

# to upgrade
pip install --upgrade gdown
```

安裝過程可能會遇到 `No module named setuptools`


只要再安裝 `python-setuptools`

```bash
sudo apt-get install -y python-setuptools
```

## Usage command
```bash
gdown `id`
```

[[gdown github webpage]](https://github.com/wkentaro/gdown)