---
title: 傳值、傳址、傳參考 (Call by Value, Address, Reference)
date: 2019-06-25
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

傳值、傳址、傳參考 教學與筆記。

<!-- more -->

# 傳值 (Call by Value)

```cpp
#include <stdio.h>

void swap(int c, int d) {
    int temp = c;
    c = d;
    d = temp;
}

void main() {
    int a = 5, b = 10;
    swap(a, b);
}
```

main 裡的 a,b 沒有變化，只把`值`複製給對方。

* `執行前`：

\          | main 的 a | main 的 b | ......... | swap 的 a | swap 的 b 
:---------:|:---------:|:---------:|:---------:|:---------:|:---------:
儲存值     | 5         | 10        | ......... | 5         | 10        
記憶體位址 | 0x04      | 0x08      | ......... | 0x16      | 0x20      

* `執行完`：

\          | main 的 a | main 的 b | ......... | swap 的 a | swap 的 b 
:---------:|:---------:|:---------:|:---------:|:---------:|:---------:
儲存值     | 5         | 10        | ......... | 10        | 5        
記憶體位址 | 0x04      | 0x08      | ......... | 0x16      | 0x20      

# 傳址 (Call by Address)

```cpp
#include <stdio.h>

void swap(int *c, int *d) {
    int temp = *c;
    *c = *d;
    *d = temp;
}

void main() {
    int a = 5, b = 10;
    swap(&a, &b);
}
```

* `執行前`：

\          | main 的 a | main 的 b | ......... | swap 的 *c | swap 的 *d 
:---------:|:---------:|:---------:|:---------:|:----------:|:---------:
儲存值     | 5         | 10        | ......... | 0x04       | 0x08        
記憶體位址 | 0x04      | 0x08      | ......... | 0x16       | 0x20      

* `執行完`：

\          | main 的 a | main 的 b | ......... | swap 的 *c | swap 的 *d 
:---------:|:---------:|:---------:|:---------:|:----------:|:---------:
儲存值     | 10        | 5         | ......... | 0x04       | 0x08        
記憶體位址 | 0x04      | 0x08      | ......... | 0x16       | 0x20      

結論：

> 指標是專門用來儲存某記憶體的位址，但指標本身也有自己的記憶體位址。
> Call by Address 本質上還是 `Call by Value`。

# 傳參考 (Call by Reference)

傳參考的功能只有 C++ 才有。

```cpp
#include <iostream>
using namespace std;

void swap(int &c, int &d) {
    int temp = c;
    c = d;
    d = temp;
}

int main() {
    int a = 5, b = 10;
    swap(a, b);
    cout << a << endl;
    cout << b << endl;

    return 0;
}
```

* `執行前`：

\          | main 的 a | main 的 b | ......... | swap 的 &c | swap 的 &d
:---------:|:---------:|:---------:|:---------:|:----------:|:---------:
儲存值     | 5         | 10        | ......... | 5          | 10      
記憶體位址 | 0x04      | 0x08      | ......... | 0x04       | 0x08      

* `執行完`：

\          | main 的 a | main 的 b | ......... | swap 的 &c | swap 的 &d
:---------:|:---------:|:---------:|:---------:|:----------:|:---------:
儲存值     | 10        | 5         | ......... | 10         | 5      
記憶體位址 | 0x04      | 0x08      | ......... | 0x04       | 0x08      

傳參考的意思就是變數的別名、綽號，因此 c 的記憶體位址跟主程式的 a 的位址一樣。

> Call by Reference 其實才是真正意義上的 Call by Address。

# 練習

```cpp
#include <iostream>
using namespace std;

void CallByValue(int b) {
    cout << "Call By Value : " << &b << endl; // 0x002FFD58
}

void CallByAddress(int *b) {
    cout << "Call By Address : " << &b << endl; // 0x002FFD58
}

void CallByReference(int &b) {
    cout << "Call By Reference : " << &b << endl; // 0x002FFE2C
}

int main() {
    int a = 1;

    cout << "main a address : " << &a << endl; // 0x002FFE2C

    CallByValue(a);
    CallByAddress(&a);
    CallByReference(a);

    system("pause");
    return 0;
}
```

只有 Call By Reference 能讓 function 裡的變數之記憶體位址跟主程式的位址一樣。