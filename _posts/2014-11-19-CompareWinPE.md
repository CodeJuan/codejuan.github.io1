---
layout: post
title: 比较WinPE文件(忽略时间戳)
comments: true
---
## 背景
项目组出现过比较有意思的情况：在同一台CI服务器，从同一个SVN上取指定版本的代码进行打包，但生成的两个版本有差异，即有DLL不相同导致运行结果不正确。经过定位，推测可能是update代码的过程中出现了异常，没有获取到期望的代码。
因此，CI工程师需要一种方法能够对DLL，EXE等二进制文件进行比对，以验证其正确性。但是即使用普通二进制比较工具（BeyondCompare）进行比较，发现总是有几个字节不相同。于是向我求助。

## 过程
我曾看过windows的PE文件结构，依稀记得里边会有几个字节存放TimeStamp和CheckSum，所以会有这么几个字节的差异。为避免误人子弟，特找来微软的定义看看：

{% highlight cpp  %}
typedef struct _IMAGE_NT_HEADERS {  
    DWORD Signature;  
    IMAGE_FILE_HEADER FileHeader;  
    IMAGE_OPTIONAL_HEADER32 OptionalHeader;  
} IMAGE_NT_HEADERS32, *PIMAGE_NT_HEADERS32;
{ endhighlight }

其中FileHeader的定义是

{% highlight cpp  %}
typedef struct _IMAGE_FILE_HEADER {  
    WORD    Machine;  
    WORD    NumberOfSections;  
    DWORD   `timeDateStamp`;  //timeDateStamp
    DWORD   PointerToSymbolTable;  
    DWORD   NumberOfSymbols;  
    WORD    SizeOfOptionalHeader;  
    WORD    Characteristics;  
} IMAGE_FILE_HEADER, *PIMAGE_FILE_HEADER;
{ endhighlight }
