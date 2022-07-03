---
title: Const 關鍵字 (Const Keyword)
date: 2019-06-30
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Const 關鍵字 教學與筆記。

<!-- more -->

# 說明

如果希望宣告的變數是`唯讀`的，可使用 Const 關鍵字。

## int const a

```cpp
int const a = 1;
a = 2; // error
```

## const int a

與 int const a 相同。

-----------------------------

## int const *p = &a

`不可改變指定變數的值`；但`可改變指定成其他變數`。

```cpp
int a = 1;
int b = 2;
int const *p = &a;
*p = 3; // error
p = &b; // OK
```

## const int *p = &a

與 int const *p 相同。

-----------------------------

## int *const p = &a

`可改變指定變數的值`；但`不可改變指定成其他變數`。

```cpp
int a = 1;
int b = 2;
int *const p = &a;
*p = 3; // OK
p = &b; // error
```

-----------------------------

## const int *const p = &a

`不可改變指定變數的值`；也`不可改變指定成其他變數`。