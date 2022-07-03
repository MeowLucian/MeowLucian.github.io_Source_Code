---
title: 計時基礎 (Time Basic)
date: 2019-07-15
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

計時 基礎教學與筆記。

<!-- more -->

# 說明

## clock_t

返回從`開啟這個程序`到`程序中調用 clock() 函數`之間的 `CPU 時鐘計時單元 (clock tick) 數`。

## time_t

返回 `CUT (Coordinated Universal Time)`，時間從 1970 年 1 月 1 日 00:00:00 (稱為 UNIX 系統的 Epoch 時間)到當前時刻的秒數。

# 計算所花時間範例

對一段 function 計時所花的時間，單位為 ms。

```cpp
#include <iostream>
#include <ctime>
using namespace std;

void fun() {
    double Sum = 0;
    for (int i = 0; i < 10000; ++i)
        for (int j = 0; j < 10000; ++j)
            Sum += i * j;
}

int main() {
    clock_t start, end;
    start = clock();
    fun();
    end = clock();
    double diff = end - start; // ms
    cout << diff << endl;

    return 0;
}
```