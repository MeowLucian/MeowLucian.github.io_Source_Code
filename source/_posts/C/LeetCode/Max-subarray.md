---
title: Max Subarray
date: 2022-06-28
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

LeetCode 53. Maximum Subarray 教學與筆記。

<!-- more -->

# 說明
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.

使用 Kadane’s Algorithm

```cpp
#include <stdio.h>
const int INT_MIN = -1e9;

int maxSubArray(int nums[], int numsSize) {
	int maxSum = INT_MIN;
	int currSum = 0;

	for (int i = 0; i < numsSize; i++) {
		currSum += nums[i];
		if (currSum > maxSum) {
			maxSum = currSum;
		}

		if (currSum < 0) {
			currSum = 0;
		}
	}

	return maxSum;
}

int main() {
	int array[] = {-2, 1, -3, 4, -1 , 2, 1, -5, 4};
	int array_size = sizeof(array)/sizeof(array[0]);
	
	printf("%d\n", maxSubArray(array, array_size)); // 6 (4 -> -1 -> 2 -> 1)
	return 0;
}
```

# 參考
[LeetCode Max Subarray webpage](https://leetcode.com/problems/maximum-subarray)
[alchemist-al 手動練習](https://alchemist-al.com/algorithms/maximum-subarray-problem)
[台大資訊 演算法 | ADA 2.6: Maximum Subarray (21/09/30)](https://www.youtube.com/watch?v=_evw8n7rGbU)