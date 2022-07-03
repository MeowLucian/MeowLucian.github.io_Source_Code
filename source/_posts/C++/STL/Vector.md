---
title: 向量容器 (Vector)
date: 2018-12-09
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

向量容器 教學與筆記。

<!-- more -->

# 說明

vector 與 array 類似，使用連續的記憶體空間。不過 array 一經宣告，記憶體空間即為固定。而 vector 可以動態配置、不需明確指定記憶體大小。

# vector & iterator (向量容器與疊代器)

* 原始使用方法

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> x = {1, 2, 3};

    for(vector<int>::iterator p = x.begin(); p != x.end(); p++) {
        cout << *p << endl;
    }

    return 0;
}
```

* C++11 可用 auto 關鍵字

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> x = {1, 2, 3};

    for(auto p = x.begin(); p != x.end(); p++) {
        cout << *p << endl;
    }

    return 0;
}
```

* 提供非成員函式 begin 和 end，比較有彈性的寫法

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> x = {1, 2, 3};

    for(auto p = begin(x); p != end(x); p++) {
        cout << *p << endl;
    }

    return 0;
}
```

* C++11 可用 for(元素:容器) 循序尋訪

此例 auto 不能自動辨別原始記憶體位置而為複製品，不能直接對原始值修改。

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> x = {1, 2, 3};

    for(auto c : x) {
        cout << c << endl;
    }

    return 0;
}
```

* 加入 參照(&)後，可直接修改原始內容

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> x = {1, 2, 3};

    for(auto &c : x) {
        ++c;
    }

    for(auto &c : x) {
        cout << c << endl; // 2, 3, 4
    }

    return 0;
}
```

# erase 函數用法

* 以下為`錯誤`用法 :

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 2, 3, 4, 5};

    for (auto p = begin(nums); p != end(nums); p++) {
        if (*p == 2)
            nums.erase(p);
    }	

    return 0;
}
```

因為 earase 結束後，p 變成了空指標，p++ 就產生了錯誤。

* 以下為`正確`用法 :

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 2, 3, 4, 5};

    for (auto p = begin(nums); p != end(nums); p++) {
        if (*p == 2)
            p = nums.erase(p);
    }	

    return 0;
}
```

erase() 返回的值是一個迭代器，指向刪除元素的下一個元素；如果是 remove() 刪除某範圍內的元素時，返回值也是一個迭代器，指向最後一個刪除元素的下一個元素。

`此例不能連續刪除兩個 2。` 原因是 erase 後，p 已經指向下一個元素了，即 1->`2`->3->4->5，不應該再 p++，否則會跳過下一個元素，即連續兩個 2 時跳過了第二個 2。可改為以下 :

* 連續刪除(1) :

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 2, 3, 4, 5};

    for (auto p = begin(nums); p != end(nums); ) {
        if (*p == 2)
            p = nums.erase(p);
        else
            p++;
    }

    return 0;
}
```

* 連續刪除(2) :

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 2, 3, 4, 5};

    for (auto p = begin(nums); p != end(nums); p++) {
        if (*p == 2) {
            p = nums.erase(p);
            p--;
        }
    }

    return 0;
}
```

# remove 函數用法

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> nums = { 1, 2, 2, 3, 4, 5 }; // 1 2 2 3 4 5
                                             // ^

    vector<int>::iterator pend = remove(begin(nums), end(nums), 2); // 1 3 4 5 ?
                                                                    //         ^
    // print
    for (auto c = begin(nums); c != pend; c++)
        cout << *c << endl;

    return 0;
}
```

remove() 同樣返回一個指標，指向刪除元素後、最後值的下一個元素。