---
title: 質數 (Prime)
date: 2019-07-08
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

質數 教學與筆記。

<!-- more -->

# 說明

列印 size 個質數。

```cpp
#include <stdio.h>

int is_prime(int input){
    int flag = 1; // It's prime
    for(int i = 2; i*i <= input; i++) {
        if(input % i == 0 ){
            flag = 0; // It's not prime
            return flag;
        }
    }
    return flag;
}

void main() {
    for(int n = 2; n <= 43; n++) {
        printf("n = %d, %d\n", n, is_prime(n));
    }
}
```

結果 :
```cpp
n = 2, 1
n = 3, 1
n = 4, 0
n = 5, 1
n = 6, 0
n = 7, 1
n = 8, 0
n = 9, 0
n = 10, 0
n = 11, 1
n = 12, 0
n = 13, 1
n = 14, 0
n = 15, 0
n = 16, 0
n = 17, 1
n = 18, 0
n = 19, 1
n = 20, 0
n = 21, 0
n = 22, 0
n = 23, 1
n = 24, 0
n = 25, 0
n = 26, 0
n = 27, 0
n = 28, 0
n = 29, 1
n = 30, 0
n = 31, 1
n = 32, 0
n = 33, 0
n = 34, 0
n = 35, 0
n = 36, 0
n = 37, 1
n = 38, 0
n = 39, 0
n = 40, 0
n = 41, 1
n = 42, 0
n = 43, 1
```