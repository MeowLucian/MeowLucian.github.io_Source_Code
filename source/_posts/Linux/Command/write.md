---
title: write
date: 2022-06-23
cover: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
thumbnail: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - Linux
---

# Tutorial
傳送訊息給另一個 shell

```bash
write <user name> <pts number>

<message>  (will send after Ctrl + D)

< Ctrl + D >
```

# Example
```bash
[lucian-vm@:~/Desktop]$ w
21:39:51 up 13:48,  4 users,  load average: 0.00, 0.00, 0.00
USER       TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
lucian-vm  tty2     tty2             Mon19    2days  0.06s  0.06s /usr/libexec/gnome-session-binary --systemd --session=ubuntu
lucian-vm  pts/0    192.168.6.2      Mon19    7.00s  0.14s  0.13s screen -S test
lucian-vm  pts/1    :pts/0:S.0       Mon19    7.00s  0.02s  0.00s w
lucian-vm  pts/2    :pts/0:S.1       Tue22   15.00s  0.06s  0.06s /bin/bash
```

## 第一個傳送 shell (pts/1)
```bash
[lucian-vm@:~/Desktop]$ write lucian-vm pts/2
Hello
< Ctrl + D >
```

## 第二個接收 shell (pts/2)
```bash
[lucian-vm@:~/Desktop]$
Message from lucian-vm@lucianvm-virtual-machine on pts/1 at 21:44 ...
Hello
EOF
```