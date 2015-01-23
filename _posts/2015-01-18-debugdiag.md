---
layout: post
title: DebugDiag使用指南 
comments: true
---

# DebugDiag使用指南

## Foreword
一直都是用windbg进行调试，但是主要通过CLI操作，现在的小朋友被GUI带坏了，都说学不会用。为此，还得找个略微简单的工具。
恰好找到了`DebugDiag`，据说很简单，微软原文如下：
> The right debugging tool can dramatically simplify the isolation of these problem s and the provision of solutions. There are several types of these issues for which the Debug Diagnostic Tool  is a better choice than other debugging tools

> Using the Windows core debuggers (Windbg.exe or Cdb.exe) for post-mortem analysis is a time consuming process and requires many debugging skills.

试用之后，果然比较简单，功能也很强大。这么个挺好用的工具，还是值得安利一下的。鉴于帮助文档大多是英文版，我就顺手把`How to Use the Debug Diagnostic Tool (DebugDiag) to Debug User Mode Processes`翻译一下。

原文链接:[http://msdn.microsoft.com/en-us/library/ff420662.aspx](http://msdn.microsoft.com/en-us/library/ff420662.aspx)

以上。

## 简介
当用户面临程序稳定性及性能问题（如崩溃、挂死、不明觉厉的高内存占用）时，最佳补救措施就是在第一时间分析此程序的进程。不过，某些应用服务（如 IIS、Exchange、SQL Server、COM+、Biztalk）在运行出错和重启时，并没有提供UI信息，这样就增加了troubleshooting的难度。
