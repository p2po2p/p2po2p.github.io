---
layout: post
title: 多设备连接下adb命令使用
date: 2017-11-01
categories: blog
tags: [Android]
description: 多设备连接下adb命令使用
---


## 方案

- 单个设备直接使用adb <command>
- 多个设备连接时，需要 adb -s <serial number> <command>

- 如何获取serial number?
    - 通过 adb devices获取

![](http://oybmb6yjg.bkt.clouddn.com/adbdevices.png)
