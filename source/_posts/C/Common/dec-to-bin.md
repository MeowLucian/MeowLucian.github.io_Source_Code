---
title: Dec to Bin
date: 2022-07-07
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

十進位轉二進位 教學與筆記。

<!-- more -->

# 說明
計算完餘數迴圈後，下次進入迴圈計算餘數時 `乘上10` 進位

```cpp
#include <stdio.h>

void main(){
    int input = 13;

    int mod = 0;
    int final = 0;
    int bit_loc = 1;

    while(input){
        mod = input % 2;
        final = final + mod * bit_loc;
        bit_loc = bit_loc * 10;
        input = input / 2 ;
    }

    printf("%d\n", final); // 1101
}
```