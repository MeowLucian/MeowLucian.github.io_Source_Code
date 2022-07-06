---
title: 連結串列 (Linked list)
date: 2019-06-27
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

連結串列 教學與筆記。

<!-- more -->

# struct 實現

```cpp
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void push(struct Node** head_ref, int new_data){
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    new_node -> data = new_data;
    new_node -> next = *head_ref;
    (*head_ref) = new_node;
}

void print_list(struct Node* node){
    while(node != NULL){
        printf("%d ", node->data);
        node = node -> next;
    }
    printf("\n");
}

void reverse(struct Node** head_ref){
    struct Node* prev = NULL;
    struct Node* curr = *head_ref;
    struct Node* next = NULL;
    while(curr != NULL){
        // Notice below loop relations
        next = curr -> next; // Store next first
        curr -> next = prev;
        prev = curr;
        curr = next;
    }
    *head_ref = prev;
}

void delete(struct Node** head_ref, int input){
    // Delete all occurrences input num
    struct Node* prev = NULL;
    struct Node* curr = *head_ref;

    // If head node is input
    if(curr -> data == input){
        *head_ref = curr -> next;
        free(curr);
        curr = *head_ref;
    }

    // Search input in the middle of list
    while(curr != NULL){
        if(curr -> data == input){
            prev -> next = curr -> next;
            free(curr);
            curr = prev -> next;
        }
        else {
            prev = curr;
            curr = curr -> next;
        }
    }
}

void main() {
    struct Node* head = NULL;
    push(&head, 3);
    push(&head, 4);
    push(&head, 2);
    push(&head, 3);
    push(&head, 1);
    print_list(head); // 1 3 2 4 3

    reverse(&head);
    print_list(head); // 3 4 2 3 1

    delete(&head, 3);
    print_list(head); // 4 2 1
}
```