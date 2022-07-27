---
title: Calculate size without sizeof
date: 2022-07-27
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Calculate size without sizeof 實作教學與筆記。

<!-- more -->

# 說明

使用指標來實現。

```cpp
#include <stdio.h>
#define my_sizeof(type) ((char *)(&type+1)-(char*)(&type))

struct test{
    int a;
    int b;
};

void main(){
    int  arr[] = {1, 2, 3, 4, 5, 6};
    struct test A_struct;

    printf("%ld\n", my_sizeof(arr));       // 24
    printf("%ld\n", my_sizeof(A_struct));  // 8
}
```