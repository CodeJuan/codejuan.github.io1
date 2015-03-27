---
layout: post
title: Linux C++性能调优笔记
comments: true
---

## 前言

上周领导在群里问谁会linux C开发，我曾在业余时间自己捣鼓过，于是回答略懂。这周就被派到别的项目组紧急支援开发。大体工作是开发一个so供前台调用，开发过程中对makefile、跨平台的理解越发深刻了。相比于自娱自乐，正规开发更能涨知识。
此后数据量较大，很快就出现性能问题，作为折腾砖家，我当仁不让地接下性能调优的活。
每当遇到难题，都是我比较开心的时候，因为又是一次get新技能的好机会。

## profiler

当系统的性能不能满足要求的时候，便要对其进行调优。方法有千千万万种，但无论如何，我们都要想办法精确识别到瓶颈，然后有的放矢进行优化。如何精确识别呢？这个时候profiler就闪亮登场了。

### linux常用profiler

gprofile & perf & sprof

#### gprofile

老牌劲旅，长久不衰，很多人用，功能也比较强大，使用简单。

- 在编译时加入参数 -pg就可以打开GProfile的开关
- 运行你的可执行文件，结束后会生成一个gmon.out
- 分析结果：gprof -b '你的可执行文件名' gmon.out
- 会按函数热度进行排序，百分比越大的函数就越热，可以针对TOPN函数进行分析。

但是由于我开发的是一个so，被其他进程调用。虽然在so的编译时加上了-pg，并且通过标志位将进程用exit退出，但是还是没有生成gmon.out，不知道怎么回事，姑且先放下，有机会再研究。


#### perf
perf功能很强大，而且被收录到内核(2.6.31)，可以记录page fault， cache miss，看起来真的很不错。
可惜我们的目标机内核版本太老，2.6.17，stackoverflow上有人回答说无法安装，

> Q: Does the old linux kernel support perf.
> A: No, it does not. The performance counters subsystem has undergone significant recent changes, and you are exceedingly unlikely to get perf working on any kernel below 2.6.31.

只好就此作罢。以后有机会再尝试。


#### sprof

继续搜索'Profiling shared library'，找到sprof。看了下简介，大概能满足需求，先拿来用用。
