---
title: 執行緒基礎 (Thread Basic)
date: 2019-07-09
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

執行緒 基礎教學與筆記。

<!-- more -->

# 說明

main 指派完 thread 的工作後，繼續完成接續的程式，並在最後等待 thread 完成工作。

```cpp
#include "windows.h"
#include <iostream>
#include <thread>
using namespace std;

void fun() {
    double Sum = 0;
    for (int i = 0; i < 10000; ++i)
        for (int j = 0; j < 10000; ++j)
            Sum += i * j;

    cout << "Thread result : " << Sum << endl;
}

int main() {
    thread mThread(fun);

    // do something
    for (int i = 0; i < 10; i++) {
        cout << i << endl;
        Sleep(50);
    }

    mThread.join(); // wait the thread stop

    return 0;
}
```

![](https://drive.google.com/uc?export=download&id=1cz3mWDrcbzR6HFA0yHaBV99_czbEJPEJ)

# 競爭條件 (Race Condition)

使用互斥鎖 (Mutual Exclusion, Mutex)、Lock

# 行程死結 (Process Deadlock)

## 原因四要素

### 互斥 (Mutual Exclusion)：

一個系統資源只能被一個行程所持有。

### 禁止搶占 (No Preemption)：

系統資源不能被強制從一個行程中退出。

### 持有和等待 (Hold and Wait)：

一個行程可以在等待時持有系統資源。

### 循環等待 (Circular Waiting)：

一系列行程互相持有其他行程所需要的資源。

## 解決死結

### 破壞互斥：

很困難(不可能)打破。

### 破壞禁止搶占：

提高優先權。

### 破壞持有和等待：

* 除非 process 可以一次取得完成工作所需的全部資源，才允許 process 持有資源，否則不准持有任何資源

* 一旦要申請新資源，則必須先釋放持有的全部資源，才可以提申請。

### 破壞循環等待：

給予每個Resource唯一的(unique)資源編號(ID)、規定process需依資源編號`遞增`的方式提出申請。