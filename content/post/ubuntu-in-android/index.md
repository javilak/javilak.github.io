---
title: 通过termux在安卓中部署ubuntu
description: 安装与踩坑之路
slug: ubuntu-in-android
date: 2023-04-26 00:20:00+0800
image: cover.jpg
categories:
    - androidplay
tags:
    - android
    - linux
    - ubuntu
    - termux
---

正值假期临近，如何在旅行中一边学习语言，一边维持轻量的携带便成了我所要考虑的问题，正巧手上有一台安卓平板，我便有了一个大胆的想法————在平板中部署一个linux系统

在安卓上部署linux的教程并不少见，大到aidlinux小到个人，基本都采用termux来进行部署。但是或大或小都有一点缺点，就是需要进行远程连接，并且大多使用vnc，虽然vnc也能传输视频并远程控制，但是

总体上说性能不算特别好。

这时候我就想到微软鼎鼎大名的远程控制协议——rdp，其占用之少，对窗口协议支持之好。于是我便去查找，果不其然，有让linux作为使用rdp协议作为服务端运行的程序xrdp。

经过一轮查找，我找到了一个教程。以下内容便是基于此和我踩的坑的总结：

> 视频来自[「termux + ubuntu + xrdp」你的下一台电脑，未必不是安卓平板 -- 联想小新 pad](https://www.bilibili.com/video/av850213693/)和他的[博客](https://dreamhunter2333.com/posts/linux/install-ubuntu-with-xrdp-in-termux.html#install-termux)

    ###Install dependencies
    # Update termux
    apt-get update && apt-get upgrade -y
    # Install ssh server
    apt install openssh -y
    # start ssh
    sshd
    # modify passwd and connect from client
    passwd
    # Install dependencies
    apt install zsh git wget neofetch -y
    apt-get install proot -y
    apt install proot-distro
    # Install ohmyzsh
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"//①
    # Install and login ubuntu
    proot-distro install ubuntu
    proot-distro login ubuntu

注意，如果在安装ohmyzsh过程中出现ssl错误，按以下方法即可解决：

    find /data/data/com.termux/files -name 'libssl.so.*'

添加环境变量

    echo "export LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/openssl-1.1" >> ~/.bashrc

使当前shell生效

    export LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/openssl-1.1

如果是提示找不到libcrypto.so，其实ubuntu里面已经自带更加高版本的，用上面ssl的语句如法炮制即可

    ##Install dependencies in ubuntu
    # Update termux
    apt-get update && apt-get upgrade -y
    # Install dependencies
    apt install zsh git wget neofetch -y
    # Install ohmyzsh
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    # Install xfce4 xrdp
    apt-get install xorg xfce4 xrdp -y
    apt install libexo-1-0
    # modify port of xrdp
    sed -i 's/port=3389/port=33389/g' /etc/xrdp/xrdp.ini
    echo xfce4-session > ~/.xsession
    service xrdp restart
    
 然后在安卓app rdp里连接33389即可
