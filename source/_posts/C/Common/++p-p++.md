---
title: ++p, p++ (++p p++)
date: 2022-07-04
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

++p, p++  教學與筆記。

<!-- more -->

```cpp
#include <stdio.h>

int array_1[] = {10, 20, 30, 40, 50};
int array_2[] = {10, 20, 30, 40, 50};
int array_3[] = {10, 20, 30, 40, 50};
int array_4[] = {10, 20, 30, 40, 50};
int array_5[] = {10, 20, 30, 40, 50};

void main() {
    int *p = NULL;
    int v = 0;

    p = array_1;
    v = 0;
    v = ++*p; // *p = *p + 1; v = *p + 1
    printf("v = ++*p;\n");
    printf("v = %d, array[0] = %d, array[1] = %d, *p = %d\n\n", v, array_1[0], array_1[1], *p);

    p = array_2;
    v = 0;
    v = *p++; // v = *p; p = p + 1
    printf("v = *p++;\n");
    printf("v = %d, array[0] = %d, array[1] = %d, *p = %d\n\n", v, array_2[0], array_2[1], *p);

    p = array_3;
    v = 0;
    v = *(p++); // same as *p++
    printf("v = *(p++);\n");
    printf("v = %d, array[0] = %d, array[1] = %d, *p = %d\n\n", v, array_3[0], array_3[1], *p);

    p = array_4;
    v = 0;
    v = (*p)++; // v = *p; *p = *p + 1
    printf("v = (*p)++;\n");
    printf("v = %d, array[0] = %d, array[1] = %d, *p = %d\n\n", v, array_4[0], array_4[1], *p);

    p = array_5;
    v = 0;
    v = *++p; // p = p + 1; v = *p
    printf("v = *++p;\n");
    printf("v = %d, array[0] = %d, array[1] = %d, *p = %d\n\n", v, array_5[0], array_5[1], *p);
}

```

結果 :
```cpp
v = ++*p;
v = 11, array[0] = 11, array[1] = 20, *p = 11

v = *p++;
v = 10, array[0] = 10, array[1] = 20, *p = 20

v = *(p++);
v = 10, array[0] = 10, array[1] = 20, *p = 20

v = (*p)++;
v = 10, array[0] = 11, array[1] = 20, *p = 11

v = *++p;
v = 20, array[0] = 10, array[1] = 20, *p = 20
```

[cppreference](https://en.cppreference.com/w/c/language/operator_precedence)
[geeksforgeeks](https://www.geeksforgeeks.org/operators-c-c/)