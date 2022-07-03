---
title: 字元陣列指標 (Char Array Pointer)
date: 2019-07-31
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

字元陣列指標 教學與筆記。

<!-- more -->

# 宣告與定義

```cpp
char str[] = "hello";
char *p = str;            // OK
char *p = &str;           // error, 會指到 str 這個指標的位址

printf("%s\n", p);        // hello
printf("%s\n", ++p);      // ello

p = str;                  /* Reset */
printf("%c\n", *p);       // h
printf("%c\n", *p++);     // h, 注意 ++ 效果的先後順序
printf("%c\n", *p);       // e

p = &str[0];
printf("%s\n", p);        // hello
printf("%p\n", (void*)p); // 0x7ffc5d99a842

p = &str[1];
printf("%s\n", p);        // ello
printf("%p\n", (void*)p); // 0x7ffc5d99a843

p = str;                  /* Reset */
*(p+1) = 'A';             // Change value
p[2] = 'B';               // Change value
printf("%s\n", p);        // hABlo
```

# 傳入函式
字元陣列`函式`的使用要注意 `Call by value`, `Call by address` 差別。