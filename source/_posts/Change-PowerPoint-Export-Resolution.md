---
title: 變更 PowerPoint 投影片的匯出解析度 (Change PowerPoint Export Resolution)
date: 2019-05-07
cover: https://drive.google.com/uc?export=download&id=13A1VZRW-LihD9gc5DHmDJX0W3OVE_Ae-
thumbnail: https://drive.google.com/uc?export=download&id=13A1VZRW-LihD9gc5DHmDJX0W3OVE_Ae-
toc: true
categories: Learning-Note-學習筆記
tags:
     - Dpi
     - Office
---

設定 Microsoft Office PowerPoint 匯出解析度。

<!-- more -->

PowerPoint 並無內建修改解析度的功能，需要修改登錄碼來達成。

# 變更匯出的解析度設定

1. 按一下 `開始`，然後按一下 `執行`。

2. 輸入 `regedit`。

3. 以 PowerPoint 2016 為例：

   需要找到

   ```
   HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\PowerPoint\Options
   ```

4. 按一下 `選項` 子機碼，指向 `編輯` 功能表上的 `新增`，再按一下 `DWORD 值`。

5. 輸入 `ExportBitmapResolution`，然後再按 Enter 鍵。

6. 選取 `ExportBitmapResolution`，然後再按一下 `編輯` 功能表上的 `修改`。

7. 在 `編輯 DWORD 值` 對話方塊中，按一下 `十進位`。

8. 輸入想要的解析度值，以下為參數表格：

十進位值   | 全螢幕像素  | 寬螢幕像素 | 每英吋點數
-----------|:-----------:|-----------:|-----------:|
50	       | 500 × 375	 | 667 × 375  | 50 dpi     |
96 (預設值)| 960 × 720	 | 1280 × 720 | 96 dpi     |
100	       | 1000 × 750	 | 1333 × 750 | 100 dpi    |
150	       | 1500 × 1125 | 2000 × 1125| 150 dpi    |
200	       | 2000 × 1500 | 2667 × 1500| 200 dpi    |
250	       | 2500 × 1875 | 3333 × 1875| 250 dpi    |
300	       | 3000 × 2250 | 4000 × 2250| 300 dpi    |

數值越大解析度越高，但須注意檔案是否會過大。

我目前的設定是 200，供大家參考。

![](https://drive.google.com/uc?export=download&id=1gdfIkUckwQTV6zBotFSZ-5H88DV1AAO3)

# Reference

[如何變更 PowerPoint 投影片的匯出解析度](https://support.microsoft.com/zh-tw/help/827745/how-to-change-the-export-resolution-of-a-powerpoint-slide)