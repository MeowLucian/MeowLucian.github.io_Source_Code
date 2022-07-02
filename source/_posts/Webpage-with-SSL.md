---
title: 為網頁加上 SSL 憑證 (Webpage with SSL)
date: 2018-11-26
cover: https://drive.google.com/uc?export=download&id=1X6wQABrUPlU8Jz83dTXF6LttTOJoWbub
thumbnail: https://drive.google.com/uc?export=download&id=1X6wQABrUPlU8Jz83dTXF6LttTOJoWbub
toc: true
categories: Learning-Note-學習筆記
tags:
     - Web
     - SSL
---

由於 Github Pages 對自有域名不提供 SSL 證書，所以使用 CloudFlare 服務將網頁加上免費的 SSL 憑證。

<!-- more -->

# SSL 原理

大致上來說 User 與 Server 進行溝通時會經過第三方 Cloudflare 進行加密認證，使機密資訊不再以明文來傳送。

![](https://drive.google.com/uc?export=download&id=1FFonpLGizTmjRxoY-JrwhuCkaExp3Ev6)

# Github Page 設定

新增 CNAME 檔案並填入自己購買的網域名稱，讓它自動導向所指定的網站。例如：Brain-Garden.tw。注意：前面不需要加 `http://`。

# CloudFlare 設定

首先要有 CloudFlare 的帳號，免費註冊。

1. 新增網站域名

登入後，會出現 Add your site 頁面，輸入自己註冊的帳號，例如：Brain-Garden.tw。注意：前面不需要加 `http://`。

![Add-your-site](https://drive.google.com/uc?export=download&id=1LiSGljnCsYAaxqorzcgJIeXo9Load9Od)

2. 自動新增 DNS 紀錄

點擊 `Add site` 按鈕後，會出現 We’re querying your DNS records 頁面，點擊 `Next` 按鈕。

![DNS-records](https://drive.google.com/uc?export=download&id=1xgBSPCc3HTVkZ2OxUfbtrAudJ3pJu_8K)

3. 選擇方案

這裡我們選擇免費的方案，當然如果有更多經濟能力的人，可以升級成月費方案，功能更多。

![Select-a-Plan](https://drive.google.com/uc?export=download&id=1pWuNFuc2qRjp69GMR7wqxpFdkWia8Isi)

4. 添加 Cloudflare Nameservers

Cloudflare 會提供給你兩組 Cloudflare Nameservers 來進行設定，每個人所獲得的名稱可能不一樣。

![Cloudflare-Nameservers](https://drive.google.com/uc?export=download&id=1Hsu4wuzAFVoNpr5FFWx0_5J5dI4MxAQk)

# "網路中文"網域註冊網站設定

到網域註冊網站(此例是"網路中文")的 `DNS` 頁面添加 Cloudflare Nameservers。

備註："網路中文"設定 Nameservers 時需要這兩個 server 的實際 IP 位址，而 Cloudflare 沒有給，所以自己去搜尋了一下，`jeff` 和 `molly` 這兩個 IP 位址分別是 `173.245.59.124` 和 `173.245.58.205`。

![DNS-setting](https://drive.google.com/uc?export=download&id=1VIS8p_Yfp-2nE7Ka0NH1B5cyfeCgH8hp)

# 回到 CloudFlare 設定 DNS

接著回到 Cloudflare 管理介面 -> DNS 頁面。

![](https://drive.google.com/uc?export=download&id=1D3Vjs8QfiTZTocuyMmLUi0KPfJJVMbPV)

* 加入 4 筆 Type 為 `A`，Name 為 `@`，IP 分別為 `185.199.108.153`、`185.199.109.153`、`185.199.110.153`、`185.199.111.153`。

* 加入 1 筆 Type 為 `CNAME`，Name 為 `www`，IP 為 `brain-garden.tw`，功能是不論網址前面有無輸入 www 都會導向 brain-garden.tw。

![CloudFlare-DNS-setting](https://drive.google.com/uc?export=download&id=1-2zOtk3yCrTGuJ74MKP02FPrt94qoZ-C)

回到 Cloudflare 管理介面 -> Crypto 頁面。

![](https://drive.google.com/uc?export=download&id=1xezTqOnMKBhExXSYsRL38DWB2fZUKcUK)

SSL 認證的形式選擇默認的 Flexible 即可。

![Crypto-seeting](https://drive.google.com/uc?export=download&id=1rbUmAxLdAMKyCTIGDh8LDLFgR4VUNf4g)

另外可將頁面滑至下方 Always Use HTTPS 設定開啟，可將連結強制導向 HTTPS，增加安全認證。

![](https://drive.google.com/uc?export=download&id=1KGlviz5gqXX2JkV61NEMXq1kTQTR2vnq)

大功告成，靜待大約 30 分鐘等待網站解析生效。

可回到 Overview 頁面確認有無 `Active`、同時 Cloudflare 也會寄一封完成設定的通知信。

# SSL 憑證確認

瀏覽個人網站，確認是否有綠色小鎖，即是完成 SSL 認證。

![](https://drive.google.com/uc?export=download&id=166nrTczgKR_MQN7W66DEZZjpIXz0G2Fa)

若無，可使用 Chrome 在個人網站頁面中按下 `F12` 進入管理人員介面，點選 `Security`，檢查是否認證成功，它會告訴你哪裡有外連且沒有 SSL 憑證的 http 網址，並嘗試修改它即可。

![F12-Security](https://drive.google.com/uc?export=download&id=14EDoF5o4pOmAqri3uovxzReweyctObpJ)