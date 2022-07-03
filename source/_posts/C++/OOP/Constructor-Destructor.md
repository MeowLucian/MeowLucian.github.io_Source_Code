---
title: 建構式 & 解構式 (Constructor & Destructor)
date: 2019-05-15
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

建構式 & 解構式 教學與筆記。

<!-- more -->

# 建構式 (Constructor)

當新增物件變數時，將會自動執行建構式。

## 建立建構式初始化

原始方式：

```cpp
class Car {
    private:
        string _name = "Benz";
        int _speed = 100;
    public:
        Car() {
            cout << _name << endl;
            cout << _speed << endl;
        }
};
```

第二種方式有同樣效果：

```cpp
class Car {
    private:
        string _name;
        int _speed;
    public:
        Car() : _name("Benz"), _speed(100) { 
            cout << _name << endl;
            cout << _speed << endl; 
        };
};
```

## 建構式多載 (Overload)

當建立物件時無引數或有多個引數，可允許使用多個建構式相對應。

```cpp
class Car {
    private:
        string _name = "Benz";
        int _speed = 100;
    public:
        Car() {
            cout << _name << endl;
            cout << _speed << endl;
        }
        
        Car(string name, int speed) {
            _name = name;
            _speed = speed;
            cout << _name << endl;
            cout << _speed << endl;
        }
};
```

# 解構式 (Destructor)

當物件消滅時將會自動執行解構式。解構式只允許有一個。

```cpp
class Car {
    public:
        ~Car() {
            cout << "Car " << _name << " was eliminated." << endl;
        }
};
```

# 完整程式碼

```cpp
#include <iostream>
#include <string>
using namespace std;

class Car {
    private:
        string _name = "Benz";
        int _speed = 100;
    public:
        Car() {
            cout << _name << endl;
            cout << _speed << endl;
        }

        Car(string name, int speed) {
            _name = name;
            _speed = speed;
            cout << _name << endl;
            cout << _speed << endl;
        }

        ~Car() {
            cout << "Car " << _name << " was eliminated." << endl;
        }
};

int main() {
    Car MyCar;
    cout << endl;
    Car MyCar2("BMW",200);
    
    system("PAUSE");
    return 0;
}
```

結果圖：

![](https://drive.google.com/uc?export=download&id=1Pvr7pvvUkFlAudmw3k5fx1t2FfuA-Uwx)