---
title: 最大公因數 (Greatest Common Divisor)
date: 2019-07-07
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

最大公因數 教學與筆記。

<!-- more -->

# 說明

使用`輾轉相除法`求最大公因數。

```cpp
#include <stdio.h>

int gcd(int x, int y) {
    if (y == 0)
        return x;
    return gcd(y, x % y);
}

int main() {
    printf("%d\n", gcd(54, 24)); // 6
}
```