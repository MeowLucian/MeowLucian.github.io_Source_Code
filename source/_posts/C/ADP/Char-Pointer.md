---
title: 字元指標 (Char Pointer)
date: 2019-06-22
cover: /images/C-Tutorial/C-Tutorial-banner.jpg
thumbnail: /images/C-Tutorial/C-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C
---

字元指標 教學與筆記。

<!-- more -->

# 說明
可以相當方便地將一個字串常數指定給字元指標。

# 指定後不可改變字串裡的值

```cpp
char* str = "hello";
str[0] = 'H'; // error
```

# 重新指定新的字串

當重新指定新的字串時，指向的記憶體位址會`不相同`。

```cpp
char* str = "hello";
printf("%p\n", str); // 0x55d2a1638004
str = "world";
printf("%p\n", str); // 0x55d2a163800e
```

# 不可直接使用字元陣列宣告指定字串

```cpp
char* str = "hello";                        // OK
char* str = { 'h','e','l','l','o','\0' };   // error, Segmentation fault (core dumped)
```

# 指標與直接宣告字串之差異

以下兩者之差異：

```cpp
char str[] = "Hello World";
char* str  = "Hello World";
```

* 前者是個 char 陣列，包含 12 個 byte (包含空白和結尾\0)，將字元一個個複製進 s 陣列。

* 後者是一個 char 指標，指向`"Hello World"`這個字串常數的起始記憶體位置。

## 記憶體大小差異

```cpp
char s1[] = "Hello World";
char* s2 = "Hello World";

printf("size of s1: %ld\n", sizeof(s1));
printf("size of s1: %ld\n", sizeof(s2));
```

結果：
size of s1: 12
size of s2: 8

s1 是陣列，所以占了 12 個 byte；而 s2 只是指標，所以只占 8 byte。

## 迴圈寫法差異

### 普通迴圈
```cpp
char s[] = "Hello World";

void main(){
    for (int i = 0; s[i] != '\0'; i++) {
        printf("%c", s[i]);
    }
}
```

### s++ 迴圈
只有 char\* s 指標可以使用 \*s++ 寫法。

```cpp
char s[] = "Hello World";      // error, lvalue required as increment operand
char *s = "Hello World";       // OK

while(*s){
    printf("%c", *s++);
}
```

理由是 char s[] 為陣列，s 值為 `s[0]` 之位址`常數`，且無法改變。

但 char\* s 為指標，初始指向 "Hello World" 的 `H`，是一個`變數`，可以任意改變，可用 \*s++ 修改指標之指向。

一般來說只用指標 char\* s 速度會略快，因為不需複製 (copy) 的動作。

# 更方便的處理字串陣列

```cpp
char* s[] = { "John", "Harry", "George" };

for (int i = 0; i < 3; ++i) {
    printf("%s\n", s[i]);
}
```

s 中的每個元素都是字元指標，各自指向一個字串常數。