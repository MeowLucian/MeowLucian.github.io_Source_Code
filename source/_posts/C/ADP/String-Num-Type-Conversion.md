---
title: 數字字串型態轉換 (String Num Type Conversion)
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

數字字串型態轉換 教學與筆記。

<!-- more -->

# 說明

將`數字`的字串進行型態轉換。

# 字串轉數字

* atoi()：將字串轉為 int

* atol()：將字串轉為 long

* atof()：將字串轉為 double

```cpp
char str[] = "12.3";
int a = atoi(str);    // 12
long b = atol(str);   // 12
double c = atof(str); // 12.3
```

## 非數字字串
如果是非數字字串，將返回 0。

```cpp
char str[] = "ABC";
printf("%d\n", atoi(str)); // 0
```

# 數字轉字串
<未完>