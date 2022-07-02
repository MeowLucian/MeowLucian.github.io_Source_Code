---
title: GCC && Makefile 教學 (GCC && Makefile Tutorial)
date: 2019-07-15
cover: /images/GCC-Makefile-Tutorial/GCC-Tutorial-banner.JPG
thumbnail: /images/GCC-Makefile-Tutorial/GCC-Tutorial-banner.JPG
toc: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - GCC
---

GCC 和 Makefile 教學與筆記。

<!-- more -->

## 說明

GNU 編譯器套裝 (GNU Compiler Collection, GCC)

## 安裝 MinGW (Install MinGW)

## 指令列表 (Command List)

語法 ： `gcc [option] filename`

### option
功能               | 指令              |
:-----------------:|:-----------------:|
查看版本	       | `--version`       |
只做編譯、不做連結 | `-c`	           |
指定輸出檔名       | `-o filename`	   |

## 基礎編譯 (Basic Compiling)

### C Example
* 單一文件編譯：
```gcc
gcc -c main.c
gcc -o test main.c
```

### C++ Example
* 單一文件編譯：
```g++
g++ -c main.cpp
g++ -o test main.cpp
```

## 進階基礎編譯 (Advance Compiling)
* [GCC 編譯多個文件 (GCC Multiple File Compilation)](/GCC/GCC-Multiple-File-Compilation)

# Makefile