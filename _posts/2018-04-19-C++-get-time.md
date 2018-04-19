---
layout: post
title: C++获取系统时间
date: 2018-04-19
categories: blog
tags: [C++]
description: C++获取系统时间
---


## C++获取系统时间


Java中以毫秒级别返回系统时间的函数是:System.currentTimeMillis()，返回类型时64位的长整形数字。

 

而C++中有很多选择可以用来表示时间，这里选用了 gettimeofday() -- 获取当前时间(保存在结构体timeval中)

 

具体实现如下:
```C++
#include <sys/time.h>  
#include <time.h>  
  
typedef long long int64;  
  
class LogTimeMM  
{  
public:  
    static int64 getSystemTime(){  
        struct timeval tv;         //获取一个时间结构  
        gettimeofday(&tv, NULL);   //获取当前时间  
        int64 t = tv.tv_sec;  
        t *=1000;  
        t +=tv.tv_usec/1000;  
        return  t;  
    }  
};  
```

具体使用过程:

```C++
printf("%lld",LogTimeMM::getSystemTime());  
```


转载至[C++中获取系统时间类似于Java中的System.currentTimeMillis()](http://qianjigui.iteye.com/blog/1332858)