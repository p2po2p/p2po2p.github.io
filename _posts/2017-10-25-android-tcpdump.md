---
layout: post
title: Android手机端抓包
date: 2017-10-25
categories: blog
tags: [Android]
description: Android手机端抓包软件
---


## 背景

- 有些业务需要抓包才能进一步定位，开发者又不能跑到现场，只能通过手机上自动抓包

## 网上方案
- 手机端使用tcpdum进行抓包
- 需要在手机端使用tcpdump，所以需要[下载该文件](http://oybmb6yjg.bkt.clouddn.com/tcpdump)
- 将该文件放入 /system/xbin目录下，并赋予chmod 777权限
- 手机端需要获取到root权限


- 代码地址：[https://github.com/p2po2p/tcpdump](https://github.com/p2po2p/tcpdump)
- apk版本下载地址：[https://fir.im/capture](https://fir.im/capture)

![](http://oybmb6yjg.bkt.clouddn.com/%E6%89%8B%E6%9C%BA%E7%AB%AF%E6%8A%93%E5%8C%85%E6%88%AA%E5%9B%BE2.png)


## 相关命令
- tcpdump -s 0 -w /sdcard/capture.pcap
- adb pull /sdcard/capture.pcap d:/log/
