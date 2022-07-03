---
title: quickBitcount (quickBitcount)
date: 2022-04-13
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

quickBitcount 教學與筆記。

<!-- more -->

# 說明
x &= (x-1) 的功能是`消除`從`右向左`遇到的第一個`1`

```cpp
#include <stdio.h>

unsigned quickBitcount(unsigned x) {
    int count = 0;

    while(x) {
        x &= (x-1);
        count++;
    }
    return count;
}

void main() {
    printf("%d\n", quickBitcount(78));   // 4
}
```