---
title: 輸入輸出 (Input Output)
date: 2019-07-07
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

輸入輸出 教學與筆記。

<!-- more -->

# 說明

要使用輸出入必須先 include `<iostream>`。

* 輸出：`cout <<`

* 輸入：`cin >>`

# 不同進位輸出

```cpp
int a = 200;              // 預設 10 進位
cout << hex << a << endl; // 16 進位
cout << oct << a << endl; // 8  進位
cout << dec << a << endl; // 10 進位
```

# 輸入

使用 `cin` 函式，但輸入字串時中間不能包括空白；使用 `gets_s()`函式則可。

```cpp
char str[6];
cin >> str; // hello
```

```cpp
char str[6];
gets_s(str);         // AB CD
cout << str << endl; // AB CD
```

# 輸出到檔案

把結果印在 txt 檔案。

語法：[檔名.exe] >> [檔名.txt]

```
test >> result.txt
```