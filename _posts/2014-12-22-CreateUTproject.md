---
layout: post
title: һ��ʽ��VC���̴���UT����
comments: true
---

## ǰ��
��Ŀ��Ҫ������еļ�ʮ��VC����������׵�UT���̣���Ҫ���ǵ�ÿ����(��ÿ��CPP��Ҫ�ж�Ӧ��TEST)���򵥹۲���һ�£�����ѡ��add existing item to project���.cpp.h�ķ�����Ϊ�򵥡�

## ���ⴴ��
��֤�˷����Ƿ����

1. ��ĳ���̵�vcxproj��filter������UTĿ¼
2. �滻��vcxproj���CIinclude, resourceInclude��·��Ϊ���·��
3. additional path����gtest��gmock��ͷ�ļ���lib
4. defҲҪ�ĳ����·��
5. additional Include path Ҫ����ԭ�й��̵�·��
6. application type ��Ϊ exe
7. link-system-subsystem��Ϊconsole
8. gtest gmock��runtime lib����Ϊ/mdd

#### ��Ȼ����

Ч����ͼ

![](https://github.com/CodeJuan/codejuan.github.io/raw/master/images/blog/ut_migrate/UT_gtest.png)


## powershell �ű�

˵���˾����ýű�����vcxproj(��ʵ��xml)���������ᵽ�ļ������趼�ýű�ʵ�֡�

{% highlight ps %}  

$path= gi .\abc.xml
$xmldata = [xml](Get-Content $path)
$xmldata.rss.channel.title
$xmldata.rss.channel.title="abc"
$xmldata.save($path.fullname)

{% endhighlight %}  

## conclusion

���˰����ʱ��Ѵ����������ű�д�ã�ʡȥN���˵��ظ��Ͷ���ͨ���ű�ʵ�֣��������׳���
YEAH!!