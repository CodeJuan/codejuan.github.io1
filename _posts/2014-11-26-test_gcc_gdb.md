---
layout: post
title: 学习GCC & GDB
comments: true
---

### 前言
工作是在windows下开发，业余时间才能玩自己喜欢的东东，一段时间不用就会生疏。随便写两段，加深记忆。

### GCC
从代码到可执行文件，会经历四个阶段，对应的命令是

> gcc -E  test.c -o test.i 中间文件

> gcc -S test.i -o test.s  ASM

> gcc -c test.s -o test.o  OBJ

> gcc test.o -o test       可执行文件

当然，可以用一行命令搞定

> gcc -o test test.c


### GDB
回忆一下GDB的常用命令吧`l, b, r, watch, bt, n, step`
从[陈皓巨巨](http://coolshell.cn/)那A了段教程
{% highlight cpp %}
#include <stdio.h>
     
int func(int n)
{
    int sum=0,i;
    for(i=0; i<n; i++)
    {
        sum+=i;
    }
    return sum;
}

main()
{
    int i;
    long result = 0;
    for(i=1; i<=100; i++)
    {
        result += i;
    }
    printf("result[1-100] = %d /n", result );
    printf("result[1-250] = %d /n", func(250) );
}
{% endhighlight %}

> gcc -g -o test test.c

> gdb ./test

> l

> b linenum

> b function_name

> i b

> r

> n

> p var_name

> step

> info locals

> watch i

> d 1

> c

> q

### conclusion
还是要多写呃，拳不离手，曲不离口。。。。
