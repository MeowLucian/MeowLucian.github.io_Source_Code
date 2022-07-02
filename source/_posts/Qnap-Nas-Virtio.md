---
title: Qnap Nas 安裝 Virtio (Qnap Nas Virtio)
date: 2018-12-1
cover: https://drive.google.com/uc?export=download&id=1WmmkoyDgzzhfVbtMgfJTmfz6h164wzag
thumbnail: https://drive.google.com/uc?export=download&id=1WmmkoyDgzzhfVbtMgfJTmfz6h164wzag
toc: true
categories: Learning-Note-學習筆記
tags:
     - Nas
---

在 Nas 主機中安裝虛擬機器(Virtual Machine) 後發現 Nas 的主系統磁碟與虛擬機磁碟之間的傳輸速度不高，可使用 Virtio 的方法解決。

<!-- more -->

# 傳輸速度的疑難雜症

由於在虛擬機器安裝一個 Windows 的作業系統，所以 Qnap 的主 Linux 作業系統與虛擬出來的 Windows 作業系統在橋接(Bridge) 模式下，兩系統為獨立個體，透過各自的實體 IP 出去再由路由器交換資料、來達到互相傳輸的功能。

此方式為安裝虛擬機後預設配置，交換資料是透過兩個階段而不是直接在 Nas 裡的硬體磁碟交換資料，以致於傳輸速度較低。

可在 Qnap 的`網路與虛擬交換機`頁面中查看目前網路硬體配置，如下圖所示：

![雙實體 IP 示意圖](https://drive.google.com/uc?export=download&id=1jQC6HvHAPtqU0hJlFniCnpHqNLFnfc1M)

# 何謂 Virtio

在 Kernel-based Virtual Machine(KVM) 架構下， Virtio 是用來虛擬 I/O 裝置的主要平台。透過應用程式介面讓主系統與虛擬機溝通而不需再透過實體網路。

# Virtio 驅動下載

* For Windows : [Fedora Project Wiki](https://stg.fedoraproject.org/wiki/Windows_Virtio_Drivers) 點選 `Stable virtio-win iso`。

# 安裝步驟

1. 虛擬工作站頁面 -> 設定 -> 網路 -> 型別 -> 改成 Virtio

![](https://drive.google.com/uc?export=download&id=1tX_KQE_1DWyPUujc-ZDTA41ccM1-yPET)

2. 儲存空間 -> 新增裝置

![](https://drive.google.com/uc?export=download&id=1PhPWMQckthYPAKvEIzd1yJurItsuoCbd)

有別於 Windows 虛擬主磁碟的預設 IDE 介面；這裡我們要新增一個 Virtio 介面的虛擬副磁碟，以便載入剛剛下載的 Virtio 驅動程式。

3. 介面 -> Virtio

![](https://drive.google.com/uc?export=download&id=1p_g8aMdoHtSUSxNi2tM_vVbO3H6TSZmY)

這裡的容量大小不重要，設置為最小 1 GB 即可。

4. CD /DVD 頁面 -> 載入剛剛下載的驅動程式路徑

![](https://drive.google.com/uc?export=download&id=1FXoPTmvAOKdW3ZqXZANxgDlAlWDoV_8S)

5. 進入 Windows 虛擬機 -> 裝置管理員

![](https://drive.google.com/uc?export=download&id=1nkJqfl0HA4lzYTBs5KpEbD5FPEGSbDlS)

發現有幾個 Virtio 裝置尚未安裝。

6. 右鍵更新驅動 -> 瀏覽電腦上的驅動程式軟體

![](https://drive.google.com/uc?export=download&id=1DpXm1KJicf8i0et0lq6zdZwwenjmH6U5)

7. 點選剛剛新增的虛擬光碟機檔案

![](https://drive.google.com/uc?export=download&id=1AT3UpgmNbFuCjKEOztM7Uuh4ok_yziT2)

記得點選`包含子資料夾`給它搜尋。

8. 確認安裝

![](https://drive.google.com/uc?export=download&id=1J-IOFIfNR8h9F4STCA2nDXGf0THAOvlZ)

9. 個別點選並更新驅動

![](https://drive.google.com/uc?export=download&id=1FK_-B-ZKJcXQW8JkntXimUHzzxieJQHd)

確認所有都安裝完成後，會看到硬體都可辨識成功。

10. 回到虛擬工作站頁面 -> 儲存空間 -> X

![](https://drive.google.com/uc?export=download&id=1xGk1DT_jCt3V4eNQo1QqHOaP6nDiYO_F)

驅動安裝完成後，將虛擬 Windows 關閉，並將虛擬主磁碟的介面由原本的 IDE 改成 Virtio。

剛剛新增的虛擬副磁碟已不再需要，所以可以把它刪除。

11. 移除虛擬副磁碟

![](https://drive.google.com/uc?export=download&id=16Aum_RlF3PiVzt1v7jQuteLAFOt1gbPo)

映像檔也不再需要，可以一併刪除。

12. 移除虛擬光碟機裝置

![](https://drive.google.com/uc?export=download&id=1nQ7wVucqQ-wjnDp2KuWJ6fW50PAm7N4l)

新增的虛擬光碟機也不再需要，可以一併刪除。

13. 確認移除裝置

![](https://drive.google.com/uc?export=download&id=1olDCpaqoqWIx2GEbtNH3X67jzzdHmhCx)

# 結語

大功告成，現在 Nas 的主系統磁碟應該與虛擬機執行的 Windows 磁碟之間有 Virtio 介面做連接，可有較快的交換資料速度。