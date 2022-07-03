---
title: 函式指標 (Function Pointer)
date: 2019-06-29
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

函式指標 教學與筆記。

<!-- more -->

# 函式指標宣告

* 傳回值型態 (*指標名稱)(傳遞參數)

# 無參數輸入宣告

以函式指標 ptr 取得函式 foo() 的位址，兩個記憶體使用空間是相同的。

```cpp
#include <stdio.h>

void foo() {
    printf("function pointer\n");
}

void main() {
    void (*ptr)() = 0;
    ptr = foo;

    foo();
    ptr();

    printf("%p\n", foo); // address
    printf("%p\n", ptr); // address same as foo
}
```

# 宣告細節

## 正確函式指標宣告

```cpp
int (*fptr)(int);
```

## 錯誤函式指標宣告

fptr 為一個`函式`而不是指標變數，回傳的資料型態為 int*。

```cpp
int *fptr(int);
```

#  加上 typedef

使用 typedef 建立一個指向 void() 函式的指標，將宣告的命名變為更簡單的形式。

```cpp
#include <stdio.h>

typedef void (*function_pointer)();

void hello() {
    printf("Hello world\n");
}

void main() {
    function_pointer fp = &hello;

    hello();
    fp();
}
```

# 運用在多個函式

```cpp
#include <stdio.h>

typedef int (*MathFp)(int);

int plus_one(int a) { 
    return ++a; // 不要寫成 a++ 會先回傳才會 + 1
}   

int minus_one(int a) {
    return --a; // 不要寫成 a-- 會先回傳才會 - 1
}

int Calc(int x, MathFp Opt) {
    return Opt(x);
}

void main() {
    printf("1 + 1 = %d\n", Calc(1, plus_one));
    printf("1 - 1 = %d\n", Calc(1, minus_one));
}
```