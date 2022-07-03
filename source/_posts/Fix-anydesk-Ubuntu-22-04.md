---
title: Fix anydesk Ubuntu 22.04 not works issue
date: 2022-05-17
cover:
thumbnail:
toc: true
categories: Learning-Note-學習筆記
tags:
    - Linux
    - anydesk
---

Fix anydesk Ubuntu 22.04 not works issue note.

<!-- more -->

## Install anydesk
[Download Anydesk from official website](https://anydesk.com/gb/downloads)

```bash
sudo dpkg -i ./anydesk_*_amd64.deb
```

## Install libpangox
After installing AnyDesk but it's not running and get error :
`libpangox-1.0.so.0: cannot open shared object file: No such file or directory`

install libpangox by below command :

```bash
wget http://ftp.us.debian.org/debian/pool/main/p/pangox-compat/libpangox-1.0-0_0.0.2-5.1_amd64.deb

sudo apt install ./libpangox-1.0-0_0.0.2-5.1_amd64.deb
```

## Fix display server error
AnyDesk could run now but it's still can't be connected and get error :
`Status: display_server_not_supported`

```bash
sudo vim /etc/gdm3/custom.conf
```

Apply below patch :

```diff
 [daemon]
 # Uncomment the line below to force the login screen to use Xorg
-#WaylandEnable=false
+WaylandEnable=false

 # Enabling automatic login
-#AutomaticLoginEnable = true
-#AutomaticLogin = user1
+AutomaticLoginEnable = true
+AutomaticLogin = $USERNAME
```

Reboot PC one time and anydesk works.