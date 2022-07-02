---
title: Mathtype 符號顯示方框錯誤修正 (Mathtype Display Error)
date: 2018-03-17
cover: /images/Mathtype-Display-Error/Mathtype-Display-Error-banner.jpg
thumbnail: /images/Mathtype-Display-Error/Mathtype-Display-Error-banner.jpg
toc: true
categories: Learning-Note-學習筆記
tags:
     - Mathtype
---

公式編輯器 Mathtype 中一些符號顯示方框亂碼，該如何解決呢？

<!-- more -->

出現這個問題的原因是 Windows 中的 mtextra.ttf `顯示為 MT Extra (TrueType)` 字體文件不存在或版本太低所導致。

# 解決方法

1. 查看 Windows 文件夾下的 fonts 中是否有 mtextra.ttf `顯示為 MT Extra (TrueType)`，找到後刪除。

2. 在 Mathtype 文件夾下 MathType\Fonts\TrueType 中找到 `mtextra.ttf`，複製到 Windows 下的 fonts 文件夾內即可。

![Fonts-folder](/images/Mathtype-Display-Error/Fonts-folder.png)

# Mathtype 轉換成 Latex 語法

* 功能列 -> Preferences -> Translators

![Translators-setting](/images/Mathtype-Display-Error/Translators-setting.png)

File 下面的兩個選項不要選擇，在轉化時會多出很多訊息，對於公式編譯本身沒有關係。

Ctrl + C 複製公式後貼至 Latex 編輯器即可。