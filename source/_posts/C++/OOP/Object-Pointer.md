---
title: 物件指標 (Object Pointer)
date: 2019-05-18
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

物件指標 教學與筆記。

<!-- more -->

# 說明

將類別宣告物件指標並指向某個物件，可使用 `->` 運算子存取該物件的屬性和方法。

# 完整程式碼

```cpp
#include <iostream>
using namespace std;

class Car {
    private:
        int _speed;
    public:
        void SetSpeed(int speed) {
            _speed = speed;
        }
        
        int GetSpeed() {
            return _speed;
        }
};

int main() {
    Car MyCar;
    Car *ptr = &MyCar;
    ptr->SetSpeed(200);
    cout << ptr->GetSpeed() << endl;

    system("PAUSE");
    return 0;
}
```