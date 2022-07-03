---
title: 字串交換 (Swap String)
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

字串交換 實作教學與筆記。

<!-- more -->

# 說明

使用指標的指標(多重指標)來實現。

```cpp
#include <stdio.h>

void swap(char** str1_ptr, char** str2_ptr) {
    char *temp = *str1_ptr;
    *str1_ptr = *str2_ptr;
    *str2_ptr = temp;
}

void main() {
    char* str1 = "Hello";
    char* str2 = "World";
    swap(&str1, &str2);
    printf("str1 is %s, str2 is %s", str1, str2);
}
```