---
title: GCC 編譯多個文件 (GCC Multiple File Compilation)
date: 2019-07-15
cover: /images/GCC-Makefile-Tutorial/GCC-Tutorial-banner.JPG
thumbnail: /images/GCC-Makefile-Tutorial/GCC-Tutorial-banner.JPG
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - GCC
---

GCC 編譯多個文件 教學與筆記。

<!-- more -->

# 範例程式

```c
// show.h
void show();
```

```c
// show.c
#include <stdio.h>

extern int a;

void show() {
    printf("%d", a);
}
```

```c
// main.c
#include "show.h"

int a = 100;

void main() {
    show();
}
```

# GCC 編譯指令

```gcc
gcc -o test main.c show.c
```