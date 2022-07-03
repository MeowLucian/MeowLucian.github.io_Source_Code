---
title: 連結串列 (Linked list)
date: 2019-06-27
thumbnail: https://drive.google.com/uc?export=download&id=1akRbLktKgmvIPfGXA0HOxZPfaqcwov2C
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

連結串列 教學與筆記。

<!-- more -->

# struct 實現

```cpp
struct node {
    int data;
    node* next;
};
```

```cpp
node* creat(int newdata) {
    node* head = new node;
    head->data = newdata;
    head->next = NULL;
    return head;
}
```

```cpp
void print_node(node* p) {
    while (p != NULL) {
        cout << p->data << endl;
        p = p->next;
    }
}
```

```cpp
void push_back(node* head, int newdata) {
    node* p = head;
    while (p->next != NULL)
        p = p->next;
    p->next = new node;
    p = p->next;
    p->data = newdata;
    p->next = NULL;
}
```

```cpp
void push_front(node* &head, int newdata) {
    node* p = new node;
    p->data = newdata;
    p->next = head;
    head = p;
}
```

```cpp
void delete_node(node* &head, int ddata) {
    node* previous = NULL;
    node* current = head;
    while (current->data != ddata && current->next != NULL) {
        previous = current;
        current = current->next;
    }
	
    if (current->data == ddata) {
        if (previous == NULL) { // First node
            head = current->next;
            delete current;
        }
        else {
            previous->next = current->next;
            delete current;
        }
    }
	
    else
        cout << "Not found" << endl;
}
```

```cpp
void Reverse(node* &head) {
	node *previous = NULL;
	node *current = head;
	node *preceding = head->next;

	while (preceding != NULL) {
		current->next = previous;
		previous = current;
		current = preceding;
		preceding = preceding->next;
	}
	current->next = previous;
	head = current;
}
```

```cpp
int main() {

    node* head = creat(1);
    push_back(head, 2);
    push_front(head,0);
    delete_node(head,1);
    Reverse(head);
    print_node(head);

    system("pause");
    return 0;
}
```

# object 實現