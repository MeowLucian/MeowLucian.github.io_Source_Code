---
title: Extern 關鍵字 (Extern Keyword)
date: 2019-07-17
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Extern 關鍵字 教學與筆記。

<!-- more -->

# 說明

可以宣告變數會在其他的位置被定義，這個位置可能是在同一份文件之中，或是在其他文件。

# 範例

```cpp
// some.c
int a = 100;
```

```cpp
// main.c
#include <stdio.h>

void main() {
    extern int a;
    printf("%d\n", a);
}
```

編譯：
```bash
gcc -o test main.c some.c
```

# 重覆定義錯誤
extern 宣告 a 在`其他位置被定義`。如果在使用 extern 時`同時指定其值`，則視為在該位置`定義`變數。結果就是引發重覆定義錯誤。

```cpp
// main.c
#include <stdio.h>

void main() {
    extern int a = 200; // error, 'a' has both 'extern' and initializer
    printf("%d\n", a);
}
```

# 重新指定其值
`先聲明 extern 找到變數，再重新指定其值。`

```cpp
// main.c
#include <stdio.h>

void main() {
    extern int a;
    a = 200;
    printf("%d\n", a);
}
```