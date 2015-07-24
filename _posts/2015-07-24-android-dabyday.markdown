---
layout:     post
title:      "andorid手记"
subtitle:   "android"
date:       2015-07-24
author:     "weijuner"
header-img: "img/20150722.jpg"
categories: [android]
tags:
    - android
---
# andorid手记

###关于读取文件中文乱码问题解决

    new InputStreamReader(new FileInputStream(file),"GB2312");

 **在ViewGroup里面 scrollTo，scrollBy方法移动的是子View
 在View里面scrollTo，scrollBy方法移动的是View里面绘制的内容**

###正则表达式

“\\[”匹配“\[”，先将\转义出来,"\["再由正则表达式阅读
小数点可以匹配除了换行符“\n”以外的任意一个字符，如要匹配小数点本身，用“\”进行转义“\.”。



**国际惯例**


![img](/img/20150724.jpg)