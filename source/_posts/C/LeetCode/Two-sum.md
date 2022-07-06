---
title: Two sum
date: 2022-07-06
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

LeetCode 1. Two sum 教學與筆記。

<!-- more -->

# 說明
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

使用 暴力法

```cpp
#include <stdio.h>
#include <stdlib.h>

int* twoSum(int* nums, int numsSize, int target, int* returnSize){
    *returnSize = 2;
    int* ret_arr = (int*)malloc((*returnSize)*sizeof(int));
    int find_num = 0;
    for(int i = 0; i < numsSize; i++){
        find_num = target-nums[i];
        for(int j = i + 1; j < numsSize; j++){
            if(find_num == nums[j]){
                ret_arr[0] = i;
                ret_arr[1] = j;
                return ret_arr;
            }
        }
    }
    return ret_arr;
}

void main(){
    // test case 1, result_array should be [0,1]
    int nums[] = {2,7,11,15};
    int target_num = 9;

    // test case 2, result_array should be [1,2]
    // int nums[] = {3,2,4};
    // int target_num = 6;

    int nums_size = sizeof(nums)/sizeof(nums[0]);
    int* returnSize = (int*)malloc(sizeof(int));
    int *result_array = twoSum(nums, nums_size, target_num, returnSize);

    // print result_array
    for(int i = 0; i < *returnSize; i++){
            printf("%d\n", result_array[i]);
    }
}
```

# 參考
[LeetCode Two SUM webpage](https://leetcode.com/problems/two-sum/)