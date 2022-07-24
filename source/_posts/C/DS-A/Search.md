---
title: 搜尋 (Search)
date: 2019-07-02
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

搜尋 教學與筆記。

<!-- more -->

# 二分搜尋法 (binary search)

```cpp
#include <stdio.h>

int b_search(int* arr, int L, int R, int target){
    int mid = 0;

    while(L<R){
        mid = (L+R)/2;
        if(target == arr[mid]){
            return mid;
        }
        if(target > arr[mid]){
            L = mid + 1;
        }
        if(target < arr[mid]){
            R = mid;
        }
    }
    return -1; // not found
}

void main(){
    int array[6] = {3,7,8,15,16,17};
    int array_size = sizeof(array)/sizeof(array[0]);

    int index = b_search(array, 0, array_size, 8);
    printf("%d\n", index); // 2
}
```

[Reference](https://www.youtube.com/watch?v=CMweVF2iSyQ)