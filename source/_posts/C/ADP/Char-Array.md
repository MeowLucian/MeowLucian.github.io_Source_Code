---
title: 字元陣列 (Char Array)
date: 2019-06-21
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

字元陣列 教學與筆記。

<!-- more -->

# 字元陣列組成說明

字串的是由字元所組成的陣列，使用連續的記憶體區段，並在最後加上一個空(null)字元 `\0`。

* 宣告方式(1)：

注意需要使用單引號表示字元。

```cpp
char str[] = {'h', 'e', 'l', 'l', 'o', '\0'};
```

* 宣告方式(2)：

此法程式會在最後自動加上空字元。

```cpp
char str[] = "hello";
```

2種方法 `hello` + `\0` 共使用了6個字元。

```cpp
printf("%d\n", sizeof(str)/sizeof(str[0])) // 6
```

# 使用空字元檢驗字串是否為空

```cpp
if(str[0] == '\0') {
    printf("String is NULL\n")
}
```

# 指定新的字串值

## 不能直接指定
```cpp
char str[6];
str = "hello"; // error
```

## 一個一個指定

需要一個個字元指定至陣列中，並在最後加上空字元。

```cpp
char str[6];
str[0] = 'h';
str[1] = 'e';
str[2] = 'l';
str[3] = 'l';
str[4] = 'o';
str[5] = '\0';
```

# 與記憶體位址的關係

> 本質上字元陣列`變數`就是一個`指標`。
> 但`並不會直接輸出或存取位址`。
> 使用上跟字元陣列`指標`有差異。

因為字元指標常常是字串，所以 cout 一個字元指標時，會把它`當成字串來印`，(是由 operator << 定義的)。

```cpp
char str[] = "hello";
printf("%s\n", str);            // hello
printf("%p\n", &str);           // 0x7ffd2770bcd2
printf("%p\n", (void*)str);     // 0x7ffd2770bcd2
printf("%c\n", str[0]);         // h
printf("%s\n", &str[0]);        // hello
printf("%c\n", str[1]);         // e
printf("%s\n", &str[1]);        // ello

printf("%p\n", (void*)&str[0]); // 0x7ffd2770bcd2
printf("%p\n", (void*)&str[1]); // 0x7ffd2770bcd3
printf("%p\n", (void*)&str[2]); // 0x7ffd2770bcd4
printf("%p\n", (void*)&str[3]); // 0x7ffd2770bcd5
printf("%p\n", (void*)&str[4]); // 0x7ffd2770bcd6
```