---
title: strchr 實作 (strlen Implementation)
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

strchr 實作 教學與筆記。

<!-- more -->

# 說明

尋找字串裡某字元。若有回傳字元第一次出現的指標，若無返回 NULL。

```cpp
#include <stdio.h>

char* _strchr(char *s, char c) {
    char *p = NULL;
    while(*s) {
        if(*s == c) {
            p = s;
            return p;
        }
        s++;
    }
    return p;
}

void main() {
    char str[] = "hello";
    char *p = str;

    // print all address
    while(*p) {
        printf("%p\n", p);
        p++;
    }

    printf("\n");

    // search
    char *ptr = _strchr(str, 'l');
    printf("%p\n", ptr);
}
```

結果圖：

```cpp
0x7ffdf60ba0b2
0x7ffdf60ba0b3
0x7ffdf60ba0b4
0x7ffdf60ba0b5
0x7ffdf60ba0b6

0x7ffdf60ba0b4
```