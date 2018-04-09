---
layout: post
title: JNI侧YUV数据写入文件
date: 2018-04-09
categories: blog
tags: [Android]
description: JNI侧YUV数据写入文件
---


## 常用到要在jni侧把yuv数据写入文件

写入前打印下宽高，用于yuv播放器播放

[yuv播放期下载](http://www.yuvplayer.com/)

LOGE("hqr--- w[%d] h[%d]",pPictureData->u32PicWidth,pPictureData->u32PicHeight);

```C      
        FILE* file_hqr=0;
        int sum=0;

        char *start = "/sdcard/EFiles/";
        char *end = ".yuv";
        int ithis = 1234;

        char path[256] = {0};
        sprintf(path,"%s%d%s",start,ithis,end);

        //LOGE("hqr fileName [%s]", path);

        //file_hqr=fopen(path,"wb");
        file_hqr=fopen(path,"ab+");

        int ylen=((pPictureData->u32LineSize[0])*(pPictureData->u32PicHeight));
        int ulen=((pPictureData->u32LineSize[1])*(pPictureData->u32PicHeight))/2;
        int vlen=((pPictureData->u32LineSize[2])*(pPictureData->u32PicHeight))/2;

        sum+=vlen;
        sum+=ulen;
        sum+=ylen;
        fwrite(pPictureData->pucData[0],1,ylen,file_hqr);
        fwrite(pPictureData->pucData[1],1,ulen,file_hqr);
        fwrite(pPictureData->pucData[2],1,vlen,file_hqr);

        fclose(file_hqr);
```