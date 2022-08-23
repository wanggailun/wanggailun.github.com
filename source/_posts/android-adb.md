---
title: adb 无线连接教程
date: 2021-09-22 09:40:00
categories: 
- 记录
tags:
- adb
- 无线
- android
---
adb 无线连接教程
<!--more-->
[adb下载](/images/adb.zip)
*   开启手机无线连接(手机关机需要重新开启) 
1. 数据线连接设备到电脑2.  执行adb devices 检测设备
2. 执行adb tcpip 5555  开启设备无线连接
*   adb无线连接设备 
1. 手机和设备在统一局域网
2. 电脑执行连接设备命令     adb connect 手机ip地址:5555
