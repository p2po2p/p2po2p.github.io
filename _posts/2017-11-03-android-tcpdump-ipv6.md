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

![](http://oybmb6yjg.bkt.clouddn.com/android_tcpdump_ipv6_problem.png)

## 解决方法

- 提示是没有分配ipv4地址，可是我要抓的是ipv6，是不是指定的网卡不对？
- 查了下， 通过 tcpdump -D 列出所有网卡信息
- 然后指定了网卡进行抓包，ok

![](http://oybmb6yjg.bkt.clouddn.com/android_tcpdump_ipv6.png)


### 通用抓包流程
1.开发版手机开启root权限
安全中心-授权管理-ROOT权限管理（如果失败，请检查手机已登陆小米帐号/手机解锁）

2.下载tcpdump（百度云盘）
[下载该文件](https://github.com/p2po2p/tcpdump/raw/master/app/src/main/assets/tcpdump)

3.adb push 电脑中tcpdump的目录 /data/local/tcpdump

4.
```
   adb shell后Enter
   键入chmod 755 /data/local/tcpdump后Enter
   键入su - root后Enter
   键入cd /data/local后Enter
   键入tcpdump -i any -p -s 0 -w /sdcard/capture.pcap后Enter
   开始抓包
   命令参数：
                 # "-i any": listen on any network interface
　　             # "-p": disable promiscuous mode (doesn't work anyway)
　　             # "-s 0": capture the entire packet
　　             # "-w": write packets to a file (rather than printing to stdout)
　　             ... do whatever you want to capture, then ^C to stop it ...
```
5.问题复现后，同时按Ctrl+C 停止抓包；键入exit后按Enter退出

6.adb pull /sdcard/capture.pcap D:\\  
  生成的文件输出到电脑D盘
