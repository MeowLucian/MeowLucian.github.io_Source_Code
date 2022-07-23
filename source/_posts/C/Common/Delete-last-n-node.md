---
title: Delete last n node
date: 2022-07-23
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

Delete last n node 教學與筆記。

<!-- more -->

```cpp
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void push(struct Node** head_ref, int input){
    struct Node* new = (struct Node*)malloc(sizeof(struct Node));
    new -> data = input;
    new -> next = *head_ref;
    *head_ref = new;
}

void print_list(struct Node* curr){
    while(curr != NULL){
        printf("%d ", curr->data);
        curr = curr -> next;
    }
    printf("\n");
}

int store_list_to_array(struct Node* curr, struct Node** ptr_arr){
    int total_size = 0;
    while(curr != NULL){
        *ptr_arr = curr;
        curr = curr -> next;
        ptr_arr++;
        total_size++;
    }
    return total_size;
}

void main(){
    struct Node* head = NULL;
    push(&head, 7);
    push(&head, 6);
    push(&head, 5);
    push(&head, 4);
    push(&head, 3);
    push(&head, 2);
    push(&head, 1);

    // store_list_to_array
    struct Node* ptr_arr[100];
    int list_size = store_list_to_array(head, ptr_arr);

    // print array
    for(int i = 0; i < list_size; i++){
        printf("%d ", ptr_arr[i]->data);
    }
    printf("\n");

    // Delete last n node
    int n = 2;

    // set next node of node "n-1" to node "n+1"
    ptr_arr[list_size-1-n-1]->next = ptr_arr[list_size-1-n+1];
    free(ptr_arr[list_size-1-n]);
    print_list(head);
}
```

結果 :

n = 2 example

```cpp
1 2 3 4 5 6 7
1 2 3 4 6 7
```