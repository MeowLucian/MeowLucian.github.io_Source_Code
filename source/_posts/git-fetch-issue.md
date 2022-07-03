---
title: git version 2.36.1 - fatal unsafe repository
date: 2022-05-20
cover:
thumbnail:
toc: true
categories: Learning-Note-學習筆記
tags:
    - Linux
    - git
---

解決 git version 2.36.1 - fatal unsafe repository issue

<!-- more -->

## issue 說明
自從更新 git version 2.36.1 後，由於新增一些 security 機制，導致 fetch code issue出現 : `fatal: unsafe repository ('repository path' is owned by someone else)`

## 解法
新增以下 git config
```bash
git config --global --add safe.directory '*'
```