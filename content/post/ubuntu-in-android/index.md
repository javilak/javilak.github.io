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



Welcome to Hugo theme Stack. This is your first post. Edit or delete it, then start writing!

For more information about this theme, check the documentation: https://docs.stack.jimmycai.com/

Want a site like this? Check out [hugo-theme-stack-stater](https://github.com/CaiJimmy/hugo-theme-stack-starter)

> Photo by [Pawel Czerwinski](https://unsplash.com/@pawel_czerwinski) on [Unsplash](https://unsplash.com/)
