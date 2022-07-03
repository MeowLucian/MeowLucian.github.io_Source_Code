---
title: STL 簡介 (STL Introduction)
date: 2019-07-09
cover: /images/C++-Tutorial/C++-Tutorial-banner.jpg
thumbnail: /images/C++-Tutorial/C++-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
---

標準庫 STL 簡介。

<!-- more -->

# 說明

標準庫中的順序容器包含：

## array

固定大小數組。支持隨機訪問。不能增刪元素。

## vector

可變大小數組。支持隨機訪問。尾端增刪元素很快。在尾部之外的位置增刪元素可能很慢。

## deque

雙端佇列。支持隨機訪問。在頭尾位置增刪元素速度很快。

## list

雙向連結串列。任何位置增刪元素速度都很快。

## forward_list

單向連結串列。只支持單向順序訪問。任何位置增刪元素速度都很快。

## string

與 vector 相似的容器，但專門用於保存字符。隨機訪問快。在尾部增刪元素速度快。