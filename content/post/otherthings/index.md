---
title: 杂项
description: 仅备份
slug: otherthings
date: 2023-05-21 03:40:00+0800
image: cover.webp
categories:
    - other
tags:
    - bilibili
    - 坚果云
---
# B站网页端cookie

| Name                    | Value | Description |
| :---------------------- | :---: | :---------: |
| i-wanna-go-feeds        |  -1   |   内测页    |
| go-back-dyn             |   1   |   动态页    |
| go-old-ogv-video        |   1   | 番剧/影视页 |
| go_old_video            |   1   |   视频页    |
| i-wanna-go-back         |   1   |    主页     |
| i-wanna-go-channel-back |   1   |   频道页    |
| nostalgia_conf          |   1   |   搜索页    |
| opus-goback             |   1   | 动态/专栏页 |
| ogv_channel_version     |  v1   | 番剧频道页  |

 

# 坚果云角标

## 同步状态图标

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\SyncRootManager` 

`ThumbnailProvider` 删去数值或设为 $0$，但不能删去该值；重启坚果云重获角标

## Explorer右栏图标

`HKEY_CURRENT_USER\Software\Classes\CLSID\{...}`
`HKEY_CURRENT_USER\Software\Classes\WOW6432Node\CLSID\{...}` 

`System.IsPinnedToNamespaceTree` 数值由 $1$ 改为 $0$，甚至直接删去项
