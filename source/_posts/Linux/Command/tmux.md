---
title: tmux
date: 2022-05-15
cover: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
thumbnail: /images/Linux-Tutorial/Linux-Tutorial-banner.jpg
toc: true
hidden: true
categories: Learning-Note-學習筆記
tags:
    - Code
    - Linux
---

![tmux-overview](/images/Linux-Tutorial/Command/tmux/tmux-overview.png)
[Image cite reference](https://arcolinux.com/everthing-you-need-to-know-about-tmux-panes/)

# Tutorial

## Session
`tmux` : Create new session
`tmux ls` : List sessions
`tmux a -t <session name>` : Re-attach session
`Ctrl + b + d `: Detach current session
`Ctrl + b + $` : Rename session

## Window
`Ctrl + b + c` : Create new window
`Ctrl + b + n` : Switch to next window
`Ctrl + b + p` : Switch to previous window
`Ctrl + b + ,` : Rename window

## Pane
`Ctrl + b + %` : Split current window to two pane vertically
`Ctrl + b + "` : Split current window to two pane horizontally
`Ctrl + b + arrow-key` : Resize pane

## Command prompt mode
`Ctrl + b + :`: Into command prompt mode

`move-window -t <number>` : Only works if position \<number\> is empty
`swap-window -t <number>` : Swap to \<number\> window