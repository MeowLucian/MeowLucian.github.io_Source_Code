---
title: 數字反轉 (Reverse Number)
date: 2019-07-06
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

數字反轉 教學與筆記。

<!-- more -->

# 說明

每執行完取 10 的餘數後，上一筆數值需要進位。以十進位來說，就是要乘以 10。

```cpp
#include <stdio.h>

int reverse(int input) {
    int ans = 0;
    while (input != 0) {
        ans = ans * 10 + input % 10;
        input = input / 10;
    }
    return ans;
}

void main() {
    int input = 691;
    int rev = reverse(input);

    printf("%d\n", input); // 691
    printf("%d\n", rev);   // 196
}
```