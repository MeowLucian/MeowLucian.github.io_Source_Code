---
title: strrev 實作 (strrev Implementation)
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

字串反轉 strrev 實作 教學與筆記。

<!-- more -->

# 說明

假設字串長度為 n，將索引值 0 和 n-1 字元調換，再換 1 和 n-2，直到字串中間為止。

```cpp
#include <stdio.h>

void _swap(char *a, char *b) {
    char temp = *a;
    *a = *b;
    *b = temp;
}

int _strlen(char *s) {
    int size = 0;

    while(*s) { // *s != '\0'
        size++;
        s++;
    }

    return size;
}

void _strrev(char *s) {
    int front = 0;
    int end = _strlen(s)-1;

    for (; front < end; front++, end--) {
        _swap(s + front, s + end);
    }
}

void main() {
    char str[] = "ABCD";
    _strrev(str);
    printf("%s", str); // DCBA
}
```