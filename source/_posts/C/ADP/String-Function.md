---
title: 字串函式 (String Function)
date: 2019-07-09
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

字串函式 教學與筆記。

<!-- more -->

## strcpy()
```cpp
char str1[] = "hello";
char str2[6];         // 需要預先宣告大小
strcpy(str2, str1);   // str1 字串複製給 str2 字串
```

## strncpy()
<未完>

## strcat()
```cpp
char str1[11] = { 'h', 'e', 'l', 'l', 'o', '\0' }; // 需要預先宣告大小
char str2[]   = { 'w', 'o', 'r', 'l', 'd', '\0' };
strcat_s(str1, str2); // str2 字串串接在 str1 字串後
printf("%s\n", str1); // helloworld
```

## strlen()
計算不包含 `\0` 的字串長度。
```cpp
char str1[11] = { 'h', 'e', 'l', 'l', 'o', '\0' }; // 遇到 '\0' 就停止計算
printf("%d\n", strlen(str1)); // 5
```

## strcmp()
比較的標準是依 ASCII 碼的字典順序。

strcmp(str1, str2) 比較兩個字串大小，若相同傳回 0，str1 大於 str2 則傳回大於 0 的值，小於則傳回小於 0 的值。

```cpp
char str1[] = {"abc"};
char str2[] = {"abc"};
strcmp(str1, str2);    // 0
```

```cpp
char str1[] = {"abd"};
char str2[] = {"abc"};
strcmp(str1, str2);    // 1
```

```cpp
char str1[] = {"abc"};
char str2[] = {"abd"};
strcmp(str1, str2);    // -1
```