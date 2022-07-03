---
title: 費氏數列 (Fibonacci)
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

列印 size 個費氏數列數字  教學與筆記。

<!-- more -->

# 遞迴法 (Recursion)
```cpp
#include <stdio.h>

int fib(int n) {
    if (n == 0 || n == 1)
        return n;
    else
        return (fib(n - 1) + fib(n - 2));
}

void main() {
    int size = 10;
    for (int i = 0; i < size; ++i)
        printf("%d\n", fib(i));
}
```

# 動態規劃 (Dynamic Programming)
```cpp
#include <stdio.h>
#define SIZE 10

int fib(int* arr, int n) {
    if (n == 0 || n == 1) {
        return n;
    }

    int last = *(arr+n-1);
    int last2 = *(arr+n-2);
    return last+last2;
}

void main() {
    int f_array[SIZE] = {0};

    for (int i = 0; i < SIZE; i++) {
        f_array[i] = fib(f_array, i);
        printf("%d\n", f_array[i]);
    }
}
```