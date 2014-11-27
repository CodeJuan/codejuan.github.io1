---
layout: post
title: 学习gtest&gmock
comments: true
---

### UT
单元测试是代码的第一道防线，尽量将问题在前期暴露出来，发现到越早，解决的成本就越低。
所以，作为码农，必须掌握单元测试的方法，并将UT集成到本地构建及CI服务器上，这样无论是新开发，还是维护重构等等，都能对我们的改动进行检测，及时反馈。
以前用过JUnit和CppUnit，已不太适合当前开发。很多同僚都推荐gtest，我自然不能错过。

### 下载
1. [csdn](http://www.csdn.net/)下载，有好人一生平安，不用积分。
2. [googlecode](code.google.com)

### make
有帖子说1.5之后的版本无法用make构建，其实并不是这样。
1.7版本还是支持make的，cd到make文件夹，然后make即可。

