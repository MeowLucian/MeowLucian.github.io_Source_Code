---
title: strlen 實作 (strlen Implementation)
date: 2019-07-30
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

strlen 實作 教學與筆記。

<!-- more -->

# 說明

strlen 計算字串長度 (不包含空字元`\0`)。

```cpp
#include <stdio.h>

int _strlen(char *s) {
    int size = 0;

    while(*s) { // *s != '\0'
        size++;
        s++;
    }

    return size;
}

void main() {
    char str[] = "Hello";
    printf("%d\n", _strlen(str)); // 5
}
```