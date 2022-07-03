---
title: 指標的指標 (Pointer of Pointer)
date: 2019-06-24
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

指標的指標 教學與筆記。

<!-- more -->

# 基本宣告

```cpp
#include <stdio.h>

void main() {
    int p = 10;
    int *ptr1 = &p;
    int **ptr2 = &ptr1;

    printf("p = %d\n", p);
    printf("&p = %p\n", &p);

    printf("*ptr1 = %d\n", *ptr1);
    printf("ptr1 = %p\n", ptr1);
    printf("&ptr1 = %p\n", &ptr1);

    printf("**ptr2 = %d\n", **ptr2);
    printf("*ptr2 = %p\n", *ptr2);
    printf("ptr2 = %p\n", ptr2);
}

```

結果：
```cpp
p = 10
&p = 0x7fff22f90794
*ptr1 = 10
ptr1 = 0x7fff22f90794
&ptr1 = 0x7fff22f90798
**ptr2 = 10
*ptr2 = 0x7fff22f90794
ptr2 = 0x7fff22f90798
```

# 進階練習

## 沒使用指標的指標

`以下不會改變 localPtr 本身：`

```cpp
#include <stdio.h>

int value = 5;

void changePtr(int *ptr) { //Same type
    ptr = &value;
}

void main() {
    int localValue = 1;
    int *localPtr = &localValue;
    changePtr(localPtr);
    printf("%d\n", *localPtr);
}
```

因為 changePtr 中 ptr 的值是 localPtr 的複本，屬於傳值。

類比在單純的 int 函式：

```cpp
#include <stdio.h>

int value = 5;

void change(int a) { // Same type
    a = value;
}

void main() {	
    int localValue = 1;
    change(localValue);
    printf("%d\n", localValue);
}
```

`同樣不會改變 localValue 的值。`

## 正確使用雙重指標用法

```cpp
#include <stdio.h>

int value = 5;

void changePtr(int **ptr) { // 透過雙重指標改變指標變數的值 
    *ptr = &value;          // 改變指標變數的值，即改變 localPtr 存放的值 
}

void main() {
    int localValue = 1;
    int *localPtr = &localValue;
    changePtr(&localPtr);
    printf("%d\n", *localPtr); // value 變數值 5
}
```

## 使用雙重指標直接指定
```cpp
#include <stdio.h>

void main() {
    int Value = 1;
    int Value2 = 2;

    int *ptr = &Value;
    int **ptr_ptr = &ptr;

    **ptr_ptr = Value2;
    printf("%d\n", *ptr); // 2
}
```

結論：

> 如果要將傳入的`變數`內容改變，就要用`傳址`呼叫
> 如果要將傳入的`指標`內容改變，就要用`雙重傳址`呼叫