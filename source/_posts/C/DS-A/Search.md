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

# 二分搜尋法

```cpp
int Binary_search(int *arr, int L, int R, int target) {
    int ret = -1;
    int mid;

    while (L <= R) {
        mid = (L + R) / 2;

        if (arr[mid] < target) {
            L = mid + 1;
        }
        else if (arr[mid] > target) {
            R = mid - 1;
        }
        else {
            ret = mid;
            break;
        }
    }
    return ret;
}

void main() {
    int array[] = { 1,2,3,4,5,6,7,8 };
    int len = sizeof(array) / sizeof(array[0]);
    int index = Binary_search(array, 0, len-1, 5);
    printf("%d\n", index);    
}
```