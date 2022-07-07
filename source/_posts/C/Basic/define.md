---
title: define 巨集 (define Macro)
date: 2019-07-11
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

define 巨集 教學與筆記。

<!-- more -->

# 說明

根據一系列預定義的規則進行簡單的文字搜尋和替換。

# 編譯時期的常數

```cpp
#define Pi 3.14
```

# 函式功能

```cpp
#include <stdio.h>
#define Power(x) (x)*(x)

void main() {
    printf("%d\n", Power(3 + 4)); // 49
}
```

```cpp
#include <stdio.h>

#define max(x,y) (x > y ? x : y)

void main(){
    int a = 10;
    int b = 20;
    printf("%d\n", max(a,b)); // 20
}
```

# 注意事項

```cpp
#include <stdio.h>
#define Add(a,b) a+b

void main() {
    printf("%d\n", 3 * Add(3, 4) * 4);
    // 3 * 3 + 4 * 4 = 25
}
```

`define 比較像是單純替換，務必注意使用方式。`