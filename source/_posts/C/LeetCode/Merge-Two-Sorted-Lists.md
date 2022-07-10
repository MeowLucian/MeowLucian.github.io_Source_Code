---
title: Merge Two Sorted Lists
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

LeetCode 21. Merge Two Sorted Lists 教學與筆記。

<!-- more -->

# 說明
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

```cpp
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2){

    if(list1 == NULL){
        return list2;
    }
    if(list2 == NULL){
        return list1;
    }

    struct ListNode* dummy = (struct ListNode*)malloc(sizeof(struct ListNode));
    struct ListNode* tail = dummy;

    while(list1 != NULL && list2 != NULL){
        if(list1->val <= list2->val){
            tail -> next = list1;
            list1 = list1 -> next;
        }
        else{
            tail -> next = list2;
            list2 = list2 -> next;
        }
        tail = tail -> next; // Move to either old list1 node or old list2 node
    }

    if(list1 == NULL){
        tail -> next = list2;
    }

    if(list2 == NULL){
        tail -> next = list1;
    }

    return dummy->next;
}
```

# 參考
[LeetCode Merge Two Sorted Lists webpage](https://leetcode.com/problems/merge-two-sorted-lists/)
[geeksforgeeks merge-two-sorted-linked-lists](https://www.geeksforgeeks.org/merge-two-sorted-linked-lists/)