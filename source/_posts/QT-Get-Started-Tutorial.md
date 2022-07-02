---
title: QT 入門教學 (QT Get Started Tutorial)
date: 2019-02-08
cover: https://drive.google.com/uc?export=download&id=1VybFrH-TKgUJxrqBesZXzQMJsTL2dSoN
thumbnail: https://drive.google.com/uc?export=download&id=1VybFrH-TKgUJxrqBesZXzQMJsTL2dSoN
toc: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - C++
    - QT
---

QT 入門教學與筆記。

<!-- more -->

# Install QT

## Install QT Components

首先安裝必要的 QT 組件，以下 Visual Studio 2017 為例：

![](https://drive.google.com/uc?export=download&id=1EwpHJSlwsZUtK2dRzOhYtgBncnVSQ5Md)

如有 64 bit 的開發需求，請務必勾選。

其他功能依使用需求勾選。

## Install Visual Studio QT Extension Tools

工具列 -> Tools -> Extensions and Updates -> Online

搜尋 QT 後，就可看到 QT Visual Studio Tools 並安裝它。

![](https://drive.google.com/uc?export=download&id=1K_7M9NVvBuL8tqg2I4LG83cdPpwNmvfn)

或到 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TheQtCompany.QtVisualStudioTools-19123) 直接下載安裝檔安裝。

## Qt Visual Studio Tools Setting

工具列 -> Qt VS Tools -> Qt Options -> Add

![](https://drive.google.com/uc?export=download&id=19XPxq9ceIQ_R3EGcD5mZk3FArRq5-teL)

設定預設的 QT 安裝位置 `C:\Qt\5.12.3\msvc2017_64`。

![](https://drive.google.com/uc?export=download&id=1Yk-PCkkfHcnntFbzuYouPevB4cdGOqmB)

# Get Started

## Add New QT Project

工具列 -> File -> New -> Project

![](https://drive.google.com/uc?export=download&id=1_xIKgL-5hcmke1YXvnezcV4bDZImBoXW)

已經預設 Core、Gui、Widgets 等基礎功能，目前先不另外勾選其他功能。

![](https://drive.google.com/uc?export=download&id=15OcaOJMO2M8EZGEVrVr423EVERb0pubs)

## Execution

按 F5 即可執行，結果如下：

![](https://drive.google.com/uc?export=download&id=1MZLQDHoh77zFPPmmzhN2wareF7WE0hvj)

# Fix Execution Error

![](https://drive.google.com/uc?export=download&id=1EszOqBHrmeEj55MTZTNxuQp5JBq-3QLn)

如果遇到缺少 dll 檔而無法執行程式的話，解決方法如下：

* 如果 exe 檔不用發佈，可以在系統環境變量添加路徑，點擊`我的電腦右鍵->內容->系統及安全性->進階系統設定->環境變數->Path->編輯`。以我為例，在最後面添加 `C:\Qt\5.12.3\msvc2017_64\bin` 後按確定，實際添加內容要看個人的 Qt 版本及安裝位置。

* 如果要發佈給別人使用，到個人的 Qt 安裝目錄下的 bin 資料夾，這邊的位置在 `C:\Qt\5.12.3\msvc2017_64\bin` 內，複製缺少的 dll 檔放置於 exe 檔旁，持續運行並添加其他缺少的 dll 檔，這邊一共複製了以下 9 個 dll 檔才啟動成功。