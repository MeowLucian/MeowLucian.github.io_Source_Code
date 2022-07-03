---
title: Void 指標 (Void Pointer)
date: 2019-06-22
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Void 指標 教學與筆記。

<!-- more -->

# 宣告

void \* 表示這個指標可以指向任何類型的數據 (函數除外)。

```cpp
int a = 10;
void* p = &a; // address
```

# 指標取值

不能直接使用 \* 取值，須先使用型態轉換 `(type *)`。

```cpp
#include <stdio.h>

void main() {
    void* p = 0;
    printf("%d\n", *p); // error, 'void*' is not a pointer-to-object type

    // int
    int a = 1;
    p = &a;
    printf("int : %d\n", *(int*)p);

    // char
    char b = 'x';
    p = &b;
    printf("char : %c\n", *(char*)p);
}
```