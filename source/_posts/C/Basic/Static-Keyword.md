---
title: Static 關鍵字 (Static Keyword)
date: 2019-07-17
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Static 關鍵字 教學與筆記。

<!-- more -->

# 三大功能

## 隱藏(私有化)

可視範圍 (scope)

`存取的範圍：只在定義的文件檔內，不具跨文件檔共享。也可以避免與其他人寫的函式名稱衝突的問題。`

* 通常寫在 .c 檔：

```cpp
static int i;
static void function(void)
```

* 若宣告 static 在 .h 檔：則所有 include .h檔 的 .c檔 都會產生 static。

## 持久生命週期

`一但變數生成，它就會一直存在記憶體之中；直到程式結束，才會從記憶體消逝。`

```cpp
#include <stdio.h>

void count() {
    static int c = 1;
    printf("%d\n", c);
    c++;
}

void main() {
    for(int i = 0; i < 10; i++) {
        count();
    }
}
```

## 初始化為 0
<未完>