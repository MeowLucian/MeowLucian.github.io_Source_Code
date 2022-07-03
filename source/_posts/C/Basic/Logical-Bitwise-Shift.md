---
title: 邏輯、位元、位移運算 (Logical, Bitwise, Shift)
date: 2019-07-07
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

邏輯、位元、位移運算 教學與筆記。

<!-- more -->

# 說明

常常會搞錯邏輯與位元運算兩者差別，初學時可要多注意。

* 邏輯運算： `反相：!` 、 `且：&&` 、 `或：||`

* 位元運算： `NOT：!` 、 `AND：&` 、 `OR：|` 、 `XOR：^` 、 `補數：~`

* 位移運算： `<<` 、 `>>`

# 邏輯運算 (Logical Operation)
<未完>

# 位元運算 (Bitwise Operation)

## NOT：`!`

```cpp
int a = 0;   // 0
int b = !a;  // 1
```

## AND：`&`

```cpp
int a = 20;        // 10100
int b = 26;        // 11010
int c = a & b;     // 10000, 16 in DEC
```

## OR：`|`

```cpp
int a = 20;        // 10100
int b = 26;        // 11010
int c = a | b;     // 11110, 30 in DEC
```

## XOR：`^`

奇數個 1 輸出為 1；偶數個 1 輸出為 0。

```cpp
int a = 20;        // 10100
int b = 26;        // 11010
int c = a ^ b;     // 01110, 14 in DEC
```

```cpp
int a = 0xFFAC874;        // 1111 1111 1010 1100 1000 0111 0100
int b = 0x124CA7B;        // 0001 0010 0100 1100 1010 0111 1011
int c = a ^ b;            // 1110 1101 1110 0000 0010 0000 1111
                          // E    D    E    0    2    0    F
                          // 249430543 in DEC
```

## 補數：`~`

```cpp
char a = 255;      // 11111111
int b = ~a;        // 00000000, 0 in DEC
```

# 位移運算 (Shift Operation)

* `<<`：向左移位，a << n 即 a 向左移 n 個 bits，相當於乘以 2 的 n 次方。

* `>>`：向右移位，a >> n 即 a 向右移 n 個 bits，相當於除以 2 的 n 次方。

> 左移運算：左邊被擠出去的位元會被丟棄，而右邊會補上 0。
> 右移運算：右邊被擠出去的位元會被丟棄，而左邊會補上 0。

```cpp
int a = 20;        //  10100
int b = a << 1;    // 101000, 40 in DEC
int c = a >> 1;    // 001010, 10 in DEC
```