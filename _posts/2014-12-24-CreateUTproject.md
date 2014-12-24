---
layout: post
title: 一键式给VC工程创建UT工程
comments: true
---

# VLD简介

> Visual Leak Detector is a free, robust, open-source memory leak detection system for Visual C++. 

windows下VC常用开源内存泄露检测工具，代码在[codeplex](http://vld.codeplex.com/)

## 原理
代码中include了vld.h，在开始运行时构建一个VisualLeakDetector g_vld的全局变量，接管申请内存和释放内存的操作。
此后会记录每次申请内存，并将地址及call stack存到一个set；
释放内存时会删除set中与之相匹配的内存申请记录。
在程序结束时，vld会遍历此set，如果set不为空，说明有内存泄露，会将泄露地址及call stack输出到report中。

## 简单用法
0. 下载及安装，假设安装在`VldPath`
1. 配置VC的include路径：右键-属性-directory-include directory，增加`VldPath\include`
2. 配置lib路径：右键-属性-directory-lib directory，，增加`VldPath\lib\win32`，如果是x64的系统，那么选择win64即可。
3. 根据需要配置vld.ini
4. 声明

