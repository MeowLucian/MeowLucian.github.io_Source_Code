---
title: 型態轉換 (Type Conversion)
date: 2019-07-09
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

型態轉換 教學與筆記。

<!-- more -->

# 說明

依據 ASCII 碼進行轉換。

## 字元轉 int

* 直接轉換

```cpp
char c = 'A';
int num = (int)(c); // 65
```

* 使用 C++ 特有語法：`static_cast<type>(變數)`

```cpp
char c = 'A';
int num = static_cast<int>(c); // 65
```

## int 轉 字元

* 直接轉換

```cpp
int a = 97;
char c = (char)(a); // a
```

* 使用 C++ 特有語法：`static_cast<type>(變數)`

```cpp
int a = 97;
char c = static_cast<char>(a); // a
```