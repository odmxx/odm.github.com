---
layout: post
title: java 中无用的部分
description: 吐嘈文
categories:
- java
tags:
- java
---

Java已经很庞大了，充斥了很多不常用的功能

const，goto

索引化的Jar

Jar包中META-INF/INDEX.LIST 指定该Jar中有哪些包

Ant中可用index="true" 为了Applet和Webstart延迟加载Jar文件，提高类加载的速度

bin目录中的多数exe文件

例如，javah.exe，javadoc.exe，jdb.exe，jar.exe。它们已被Ant，Maven和IDE取代了。

Applet
10年前很流行，从那开始，它的流行度就一直在下降

CORBA
该API可能会从开发者的"你最想从Java中删除的API"竟选中胜出

javax.accessibility和accessibility
这个包始于Java 1.2，但就没怎么被用过。一方面，Swing确实能为你做很多事，但另一方面，它不能为你做每一件事。特别是，空的文本框和文本域需被说明。

MIDI库
Java有内建的MIDI API。从1.1开始，就能够播放音乐。当时，他们加入了一个音源库，音质听起来比较好。而现在，音源库就没声卡听起来那么好了。
在谈到模块化JRE时，多数时候，CORBA被认为是不需要被下载的，而音源库API则可能是最不需要的。


short数据类型
你在使用它？我不相信。每个人当他想使用整型时，都会使用int，即便他们并不需要32位的范围。

八进制字面量
<pre class="prettyprint">
int a = 60;
int b = 060;
System.out.println(a + b); // Prints 108.
</pre>

内部类
Java有4种内部类，其中的3种被广泛使用

如同静态内部类，命名的内部类，以及匿名内部类，也可以在方法内部定义命名的类，尽管在现实中很少看到这一情况

<pre class="prettyprint">
public class TopLevelClass
{
    public void someMethod()
    {
        class LocalClass
        {
            // Some fields and methods here.
        }
  
        LocalClass forLocalPeople = new LocalClass();
    }
}
</pre>

严格的浮点数
strictfp关键字
