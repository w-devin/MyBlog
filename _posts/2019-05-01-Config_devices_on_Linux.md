---
layout: post
title:  "config devices on Linux use xinput"
date:   2019-05-01 14:00:00 +0800
categories: Linux
tags: Linux
author: SteveDevin
mathjax: true
---
* content
{:toc}



此工具可用于关闭笔记本的键盘



## install 
```bash
#Manjaro
sudo pacman -S xorg-xinput
```

## use

1. list all the input devices
    ```bash
    xinput list
    ```
    output:
    ```bash
    [jarvis@jarvis-pc ~]$ xinput list
    ⎡ Virtual core pointer                       id=2    [master pointer  (3)]
    ⎜   ↳ Virtual core XTEST pointer            id=4    [slave  pointer  (2)]
    ⎜   ↳ ETPS/2 Elantech Touchpad              id=15   [slave  pointer  (2)]
    ⎣ Virtual core keyboard                      id=3    [master keyboard (2)]
    ↳ Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    ↳ Power Button                              id=6    [slave  keyboard (3)]
    ↳ Video Bus                                 id=7    [slave  keyboard (3)]
    ↳ Power Button                              id=8    [slave  keyboard (3)]
    ↳ Heng Yu Technology Poker                  id=9    [slave  keyboard (3)]
    ↳ Heng Yu Technology Poker Consumer Control id=10   [slave  keyboard (3)]
    ↳ Heng Yu Technology Poker System Control   id=11   [slave  keyboard (3)]
    ↳ Lenovo EasyCamera: Lenovo EasyC           id=12   [slave  keyboard (3)]
    ↳ Ideapad extra buttons                     id=13   [slave  keyboard (3)]
    ↳ AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]

    ```

2. find the devices [id]
3. config
    ```bash
    #list properties that can be set for the given devices
    xinput list-props [id]

    #disable
    xinput set-prop [id] 'Device Enabled' 0

    #enable
    xinput set-prop [id] 'Device Enabled' 1


    ```


## reference
1. [xinput](https://www.x.org/archive/current/doc/man/man1/xinput.1.xhtml)