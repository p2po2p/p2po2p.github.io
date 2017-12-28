---
layout: post
title: Android手机ndk-stack常用命令
date: 2017-12-28
categories: blog
tags: [Android]
description: Android手机ndk-stack常用命令
---


## 背景

- 崩溃在库里的堆栈不好看，需要解析下

## 常用相关命令
```
adb logcat | ndk-stack -sym armeabi-v7a/
```
```
adb logcat | ndk-stack -sym /data/data/com.uniview.app.smb.phone.en.ezview/lib/libNDPlayer.so
```
- 先获取日志再分析
```
ndk-stack -sym D:/obj/local/armeabi -dump d:/sdklog/1.log
```

## 对于以下信号都是致命的信号:
	• SIGABRT：abort退出异常
	• SIGBUS：硬件访问异常
	• SIGFPE：浮点运算异常
	• SIGILL：非法指令异常
	• SIGSEGV：内存访问异常
	• SIGSTKFLT：协处理器栈异常
	• SIGTRAP：陷阱异常
