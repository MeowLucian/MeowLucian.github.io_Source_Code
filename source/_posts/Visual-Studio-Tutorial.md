---
title: Visual Studio 教學 (Visual Studio Tutorial)
date: 2018-12-02
cover: https://drive.google.com/uc?export=download&id=16XB09c3DXxQHf5nAFs-Bwho1xuWL7Grj
thumbnail: https://drive.google.com/uc?export=download&id=16XB09c3DXxQHf5nAFs-Bwho1xuWL7Grj
toc: true
categories: Learning-Note-學習筆記
tags:
    - Code
---

Visual Studio 使用教學與筆記。

<!-- more -->

# 快捷鍵

* `F5` : 執行
* `F9` : 放置中斷點 (Breakpoint)
* `F10` : 單步執行 (Step Over)
* `F11` : 逐步執行 (Step Into)
* `Ctrl + K + C` : 多行註解
* `Ctrl + K + U` : 多行取消註解

# 各式功能設定

## 編譯 C++

要編譯 Cpp 檔案需要添加 `pch.h` 標頭檔

```
#include "pch.h"
```

## 跑完程式自動關閉

Options -> Debugging -> General -> Automatically close the console when debugging stops

![](https://drive.google.com/uc?export=download&id=1v9UzlKgNVUzsRkjkTxrznCu8NUzcrZNs)

## 除錯 (Debugger)

有分三種模式：

### 逐步執行 (Step Into)

遇到子函數就進入並且繼續單步執行。

### 單步執行 (Step Over)

不會進入子函數內逐步執行，而是將子函數整個執行完再停止，也就是把子函數整個作為一步。

### 跳步執行 (Step Out)

執行完子函數餘下部分，跳出子函數並返回到上一層函數。

## 除錯監看視窗 (Debug Window)

按 `F11` 逐步執行 (Step Into)，`Debug -> Windows -> Memory -> Memory1`

或按快捷鍵 `Ctrl + Alt + M` 再按 `1`。

### int 範例

```cpp
#include "pch.h"
#include <iostream>
using namespace std;

int main() {
    int a[] = { 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18 };
    cout << a << endl;

    system("pause");
    return 0;
}
```

![](https://drive.google.com/uc?export=download&id=1u-es2rJTxJAP--9Hv6JCvUEw--RHmPH4)

顯示陣列位址從 0x003CFBFC 開始，並為連續記憶體配置。

int 所占大小為 4 bytes，所以 Columns 設為 4，較適合監看。

![](https://drive.google.com/uc?export=download&id=1oPohKAuYlid4sHu0MCp9ppD8fNJUmRI_)

記憶體使用 16 位元進制來顯示。

### char 範例

```cpp
#include "pch.h"
#include <iostream>
using namespace std;

int main() {
    char a[] = {"ABCabc"};
    cout << &a << endl;
    cout << a << endl;

    system("pause");
    return 0;
}
```

![](https://drive.google.com/uc?export=download&id=1ZuQNq_qCp1mGjY6CnnCjfEhY2ob_j0tf)

顯示陣列位址從 0x003EFA24 開始，並為連續記憶體配置。

![](https://drive.google.com/uc?export=download&id=1zY6bJDdK17RUlk8gSQABSTYHaA3Gvwm3)

char 所占大小為 1 bytes，所以 Columns 設為 1，較適合監看。記憶體使用 16 位元進制來顯示。

## Power Mode 外掛

此插件可使程式撰寫時擁有更多樂趣。

Download Extension:

* [LiamMorrow version](https://marketplace.visualstudio.com/items?itemName=LiamMorrow.PowerMode)

* [BigEgg version](https://marketplace.visualstudio.com/items?itemName=BigEgg.PowerMode)

![Demo](https://drive.google.com/uc?export=download&id=1IAs63h08NQgRkMiP5DqnXAWBzV_jSQN4)