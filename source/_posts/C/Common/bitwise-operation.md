---
title: bitwise-operation
date: 2022-07-08
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

bitwise-operation 教學與筆記。

<!-- more -->

# 題目 1
```cpp
unsigned long v1 = 0x00001111;
unsigned long v2 = 0x00001202;
unsigned long v;
v = v1&(~v2);
v = v | v2;
ask: the value of v ?
```

* 過程 :
```cpp
v1  0001000100010001
v2  0001001000000010

v1  0001000100010001
~v2 1110110111111101

v1&(~v2) 0000000100010001
v2       0001001000000010
v | v2   0001001100010011
            1   3   1   3

Final v = 0x1313
```

* 實際驗證 :
```cpp
#include <stdio.h>

void main(){
        unsigned long v1 = 0x00001111;
        unsigned long v2 = 0x00001202;
        unsigned long v;
        v = v1&(~v2);
        v = v | v2;
        printf("0x%lx\n", v); // 0x1313
}
```

# 題目 2

* Setting a bit (Force nth bit to 1)
```cpp
#include <stdio.h>

void main(){
    int a = 76;         // 1001100, DEC 76
    a |= (1UL << 4);
    printf("%d\n", a);  // 1011100, DEC 92
}
```

* Clearing a bit (Force nth bit to 0)
```cpp
#include <stdio.h>

void main(){
    int a = 76;         // 1001100, DEC 76
    a &= ~(1UL << 3);
    printf("%d\n", a);  // 1000100, DEC 68
}
```

* Toggling a bit (Change nth bit "from 1 to 0" or "from 0 to 1")
```cpp
#include <stdio.h>

void main(){
    int a = 76;         // 1001100, DEC 76
    a ^= (1UL << 3);
    printf("%d\n", a);  // 1011100, DEC 92
}
```

[Stackoverflow Reference](https://stackoverflow.com/questions/47981/how-do-i-set-clear-and-toggle-a-single-bit)