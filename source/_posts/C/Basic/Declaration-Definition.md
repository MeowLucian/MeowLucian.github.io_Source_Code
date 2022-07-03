---
title: 宣告 & 定義 (Declaration, Definition)
date: 2019-07-15
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

宣告 & 定義 教學與筆記。

<!-- more -->

# 說明

## 宣告 (Declarations)：

讓程式得知某個變數的型態和名稱，`但不配置其空間`。

## 定義 (Definitions)：

表示為這個變數`配置了空間`，也可能`給予初始值`。

> 兩者差別在於：是否配置空間給該變數

```cpp
// 只做宣告，不配置空間
extern int i;

// 定義，可以只配置空間，尚不決定初始值。
int i;

// 定義，配置空間並給予初始值。
int i = 1 ;

// 只要設初值，就會變成定義。
extern int i = 1 ;
```

# 使用變數

若此變數要在多個檔案使用(外部連結性全域變數)，請在某一個檔案`定義`它，而其他每個用到該變數的檔案都要`宣告`該變數。

# 各種錯誤

* `變數`不能只有宣告，而沒有定義，會發生 linking error。且只能定義`一次`。

* `函式`就可以只有宣告，沒有定義。

* 變數若定義不只一次，會發生重複定義的錯誤。

> 可以宣告很多次，但定義必須是唯一的。

# 程式有多個檔案

> 『把宣告寫在 .h 檔，把定義寫在 .c 檔』

若沒按照這個原則，在 .h 檔裡放了定義，當某 .h 檔有多個 .c 檔去 include 它，就會產生重複定義的錯誤。