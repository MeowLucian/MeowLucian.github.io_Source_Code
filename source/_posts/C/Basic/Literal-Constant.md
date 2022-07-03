---
title: 字面常數 (Literal Constant)
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

字面常數 教學與筆記。

<!-- more -->

# 字面常數記憶體大小
程式中宣告一個整數值，預設它會是個 int 型態無正負號的數值；而宣告一個小數，預設會是 double 型態。

以下範例顯示出預設數值使用記憶體大小：

```cpp
#include <stdio.h>

void main() {
    printf("sizeof(1): %ld\n", sizeof(1));         // sizeof(1)   : 4
    printf("sizeof(1.0): %ld\n", sizeof(1.0));     // sizeof(1.0) : 8
}
```

# 字面常數進制

整數可以用 8 進位、10 進位與 16 進位來表示：

```cpp
#include <stdio.h>

void main() {
    printf("%d\n", 26);     // 10進位
    printf("%d\n", 0x1a);   // 16進位
}
```
以上都顯示為 26。

# 編碼

## 常用字元

符號與數字的對應關係為使用 ASCII 碼 (American Standard Code for Information Interchange)，常見的對應為：

符號  | 十進位 | 十六進位 |
:----:|:------:|:--------:|
  0   |  48    |  30      |
  1   |  49    |  31      |
  2   |  50    |  32      |
  3   |  51    |  33      |
 ...  |  ...   |  ...     |
  A   |  65    |  41      |
  B   |  66    |  42      |
  C   |  67    |  43      |
  D   |  68    |  44      |
 ...  |  ...   |  ...     |
  a   |  97    |  61      |
  b   |  98    |  62      |
  c   |  99    |  63      |
  d   |  100   |  64      |
 ...  |  ...   |  ...     |

## 跳脫自元

需要特殊功能字元，則有跳脫自元 (Escape Sequence) 可供使用：

跳脫自元 | 說明 |
-------- |:----:|
\n       | 換行       (Newline)
\t       | 水平定位點 (Horizontal Tab)
\v       | 垂直定位點 (Vertical Tab)
\b       | 退回一格   (Backspace)
\r       | 返回       (Carriage Return)
\f       | 換頁       (Formfeed)
\a       | 嗶聲       (Alert Bell)
\\\      | 倒斜線     (Backslash)
\?       | 問號       (Question Mark)
\'       | 單引號     (Apostrophe Mark)
\"       | 雙引號     (Double Quotes Mark)

更多 ASCII 碼的說明可以參考 [Wiki](https://zh.wikipedia.org/wiki/ASCII)。