---
title: if 條件判斷 (if-Statements)
date: 2019-06-01
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

if 條件判斷 教學與筆記。

<!-- more -->

# 說明

if 與 else 是就`最近的一組`來配對。加上括號的話就可以更清楚：

```cpp
if (條件式一) {
    if(條件式二)
        陳述句一;
    else
        陳述句二;
}
```

# 更簡短的條件運算子 (Conditional Operator）

如果條件式結果為 true，則傳回冒號前面的值，否則傳回冒號後面的值。

```cpp
int c = (a > b) ? a : b;
```