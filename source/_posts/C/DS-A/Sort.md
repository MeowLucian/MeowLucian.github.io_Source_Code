---
title: 排序 (Sort)
date: 2019-06-24
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

排序 教學與筆記。

<!-- more -->

# swap 函式

先將變數交換的函式設定好，之後的排序算法都會用到。

而傳入值普遍是陣列，所以設定為指標。

```cpp
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

通常測試排序用的會是陣列形式：

# 氣泡排序 (Bubble Sort)
```cpp
void Bubble_Sort(int *array, int len) {
    for (int i = 0; i < len - 1; ++i) {
        for (int j = 0; j < len - 1 - i; ++j) {
            if (array[j] > array[j + 1])
                swap(&array[j], &array[j + 1]);
        }
    }
}
```

# 選擇排序 (Selection Sort)
```cpp
void Selection_Sort(int *array, int len) {
    for (int i = 0; i < len - 1; ++i) {
        int min_index = i;
        for (int j = i + 1; j < len; ++j) {
            if (array[min_index] > array[j])
                min_index = j;
        }
        swap(&array[i], &array[min_index]);
    }
}
```

# 插入排序 (Insertion Sort)
```cpp
void Insertion_Sort(int *array, int len) {
    for (int i = 1; i < len; ++i) {
        int key = array[i];
        int j = i - 1;
        while (array[j] > key && j >= 0) {
            array[j + 1] = array[j];
            j--;
        }
        array[j + 1] = key;
    }
}
```

# 快速排序 (Quick Sort)
```cpp
int Partition(int *arr, int front, int end) {
    int pivot = arr[end];
    int i = front - 1;
    for (int j = front; j < end; ++j) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    i++;
    swap(&arr[i], &arr[end]);
    return i;
}

void Quick_Sort(int *arr, int front, int end) {
    if (front < end) {
        int pivot_index = Partition(arr, front, end);
        Quick_Sort(arr, front, pivot_index - 1);
        Quick_Sort(arr, pivot_index + 1, end);
    }
}
```

# 合併排序 (Merge Sort)
```cpp
void Merge(int *array, int front, int end, int mid) {

    // Let L[0...n1] and R[0...n2] be new arrays

    int n1 = mid - front + 1; // size
    int n2 = end - mid;       // size
    int* L = (int*) malloc(n1 * sizeof(int));
    int* R = (int*) malloc(n2 * sizeof(int));

    // copy array[front...mid] to L[0...n1]
    // copy array[mid+1...end] to R[0...n2]

    for (int i = 0; i < n1; i++) {
        L[i] = array[front + i];
    }
    for (int i = 0; i < n2; i++) {
        R[i] = array[mid + 1 + i];
    }

    // Let end be Max
    int Max = INT_MAX;
    L[n1] = Max;
    R[n2] = Max;

    int i = 0, j = 0;

    for (int k = front; k <= end; k++) {
        if (L[i] <= R[j]) {
            array[k] = L[i];
            i++;
        }
        else {
            array[k] = R[j];
            j++;
        }
    }
}

void Merge_Sort(int *array, int front, int end) {
    if (front < end) {
        int mid = (front + end) / 2;
        Merge_Sort(array, front, mid);
        Merge_Sort(array, mid + 1, end);
        Merge(array, front, end, mid);
    }
}
```

# Main
```cpp
#include <stdio.h>
#include <stdlib.h>
#include <limits.h>

void main()
{
    int array[] = { 5, 3, 1, 2, 6, 4 };
    int len = sizeof(array) / sizeof(array[0]);

    Bubble_Sort(array, len);
    Selection_Sort(array, len);
    Insertion_Sort(array, len);

    Quick_Sort(array, 0, len-1);
    Merge_Sort(array, 0, len-1);

    // print array
    for (int i = 0; i < len; i++){
        printf("%d ", array[i]);
    }
    printf("\n");
}
```