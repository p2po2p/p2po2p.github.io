---
layout: post
title: Android手机连接ipv6网络时，使用tcpdump抓包
date: 2017-11-03
categories: blog
tags: [Android]
description: Android手机连接ipv6网络时，使用tcpdump抓包
---


## 背景

- 之前遇到android侧需要抓包，直接进入shell，敲入tcpdump -s 0 -w /sdcard/keeplive.pcap就开始抓了
- 今天分析ipv6问题时需要抓包，惯例敲入命令后，却提示如下，报文抓出来也是空的
![](http://oybmb6yjg.bkt.clouddn.com/tcpdump_ipv6_problem.png)

## 解决方法

- 提示是没有分配ipv4地址，可是我要抓的是ipv6，是不是指定的网卡不对？
- 查了下， 通过 tcpdump -D 查看
    - 通过 adb devices列出所有网卡信息
    - 然后指定了网卡进行抓包，ok

![](http://oybmb6yjg.bkt.clouddn.com/tcpdump_ipv6.png)
