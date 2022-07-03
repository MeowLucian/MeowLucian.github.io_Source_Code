---
title: Friend 函式 (Friend Function)
date: 2019-06-29
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

Friend 函式 教學與筆記。

<!-- more -->

# 說明

有時候我們希望私有成員給某些外部函式來存取，這時可以設定類別的 friend 函式，只有 friend 函式可以直接存取該類別的私有成員。

```cpp
#include <iostream>
using namespace std;

class Point {
private:
    int m_x;
    int m_y;
public:
    Point(int x, int y) {
        m_x = x;
        m_y = y;
    }
    friend void showPoint(Point &pt); // 給其他函式存取私有成員
};

void showPoint(Point &pt) {
    cout << "(" << pt.m_x << "，" << pt.m_y << ")" << endl;
}

int main() {
    Point myPoint(3, 4);
    showPoint(myPoint);

    return 0;
}
```