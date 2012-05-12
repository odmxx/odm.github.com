---
layout: post
title: ajax 框架比较
description: jQuery,Prototype<br/>Ext-JS,Dojo,Dorado 7<br/>ZK,Backbase,IceFaces<br/>DWR,GWT
categories:
- ajax
tags:
- ajax
---

现今所谓 Web 2.0 网站或多或少有 AJAX 影子 

功能面分类

**浏览器端底层链接库**

- Prototype
- jQuery

**浏览器端UI组件库**

- Ext-JS
- Dojo,Dorado 7 Client API

**整合式框架**

- ZK
- Backbase
- IceFaces

# 

底层链接库应用最广、轻巧、易整合，但功能有限

整合式框架则包括浏览器端及服务器端

DWR和GWT较难分类

DWR基本是JavaScript-to-Java 的 RPC框架，而GWT则是在RPC 加上浏览器端开发工具

# 

应用面粗分

- 网站应用
- 企业应用

底层链接库多用于网站应用或当其它框架的基础

UI组件库则二者都有

整合式框架侧重在企业应用

从系统架构可分Client-centric和Server-centric

Client-centric 指程序代码(UI部份)主要执行的地方在客户端 (即浏览器)

Server-centric 则在服务器端

大部份框架多是 Client-centric 如

- Dojo
- Prototype
- GWT
- Ext-JS
- Backbase

# 

Server-centric以ZK为代表

架构的差别是决定开发及维护成本的关键

没有单一个框架适合所有应用。对于强调简易直觉接口的Web 2.0网站而言，通常只有几个需要 AJAX化的功能，可藉由浏览器端的底层链接库的帮助，并投入相当资源，以使这些AJAX 化出众夺目才是最重要的

对于现有Web应用程序，如架构于Struts、JSP或JSF等，则可依其对JavaScript熟悉度而选择浏览器端UI组 件库或整合式框架

使用浏览器端 UI组件库，需要较多定制化JavaScript程序代码才能整合到原应用程序中

而使用整合式框架，则要视其是否支持现已使用的架构

例如，若使 用.NET平台，则只能使用 Microsoft的框架
若使用JSP则可使用ZK和Backbase。若使用JSF则可使用ZK，Backbase和IceFaces

现在几乎已经没有人手工与XMLHttp对象打交道，绝大多数的开发者都使用
- Buffalo
- DWR
- Prototype
-JQuery

等辅助库、框架进行开发

# 

##AJAX框架的选择

**偏重展现**：YUI, Qooxdoo, Dojo 

- YUI    目前设计比较完整，美观，全面的界面工具库 
- Qooxdoo:    开源的另一种选择 
- Dojo    比较完善的库结构，丰富的界面控件

# 

**偏重传输**：Buffalo, DWR

# 
### Buffalo特性

- 基于prototype
  
不重复加载prototype，编程概念一致

- Bind

直接将数据绑定到页面对象并展示，能将值直接绑定到表单元素、表格、 DIV/Span、甚至整个表单上

关键是这种绑定是无侵入并且与buffalo整体结构完全整合，对外表现只有一个简单的 {{buffalo.bindReply}}或者{{Buffalo.Bind.bind}}即可 

- 序列化

Buffalo支持任意对象，任意深度，任意数据结构的Java到JavaScript以及JavaScript到Java的双向序列化，并且支持引用

生命周期对象访问：引入了线程安全的 BuffaloContext对象，只需要通过BuffaloContext.getContext()即可获得一个线程安全的引用，并且对 Request的各种属性进行操作。 

对Collection/Array的模糊处理：Buffalo中提供了对Collection/Array对象的模糊识别能力。例如：服务器端有一个方法需要List参数，客户端传递过去一个javascript数组就可以了，不需要费心的组装对象

客户端组装对象：支持在客户端组装对象，甚至可以直接将整个表单序列化为一个对象作为参数传给远程客户端 

对重载方法的处理能力：由于Java与JavaScript之间类型的不匹配，DWR的代码生成无法对重载方法进行处理。例 如，sum(double,double), sum(int, int) DWR很可能不知道你要调用哪一个。从2.0开始Buffalo支持了对重载的处理

# 

### DWR特性 

支持Batch，可以将多个Service函数调用放在一个XMLHttpRequest请求中完成

Converter：可以转换任意类型的Java对象到JavaScript，并允许直接使用。例如：Customer类包含一个 address变量，当AjaxCall返回Customer对象的时候，可以直接在Javascript中使用customer.address来获得 Address的信息

允许Expose部分函数和属性。（Buffalo无限制，可以访问Service中的任意函数） 

DWR2.0中提出了Reverse Ajax，提供在Java代码中来处理页面上元素的功能。

# 


#### 工具型 ：Prototype, JQuery, Dojo 

- Prototype

得益于Ruby语言的设计，它使得你能够以几乎类似于编写Ruby的方式编写JavaScript。由于绑定在 Ruby On Rails的发行包中，它成为近两年最流行的AJAX工具。早期它小巧灵活，现在由于加入太多的特性，日渐臃肿。目前1.6版本大小已经超过120K

- JQuery

Prototype的主要竞争者。简单是它最大的优点
大多数常见的复杂操作、效果，JQuery的代码量能够比Prototype少50%以上

- Dojo

采用类似于Java包的管理方式，实现按需加载JS。提供了全面的AJAX、DOM操作支持
然而需要在HTML TAG中嵌入额外的属性，使得网页不能遵守W3C标准，不少开发者对此耿耿于怀

# 

   Web领域几乎已经不存在技术壁垒，能做哪些，那些不适合，负载均衡等等已经有充分的资源可以参，各种模式都可以灵活的应用到其中，各种测试工具（如Selenium网页 测试工具）、开发工具支持得非常出色

   而RIA框架要考虑的问题远远要比现在的Web应用多得多

   除了RIA所承诺的更容易的实现华丽的效果──在多种 JS库的支持下这些效果在Web下并非难事──他们有更多的问题需要考虑：资源的获取和释放，测试的支持，本地存储的问题，事件机制，状态的同步，客户机、服务器数据交互机制（序列化反序列化）等等

   RIA想如同现在的Web应用般大规模，远不到时候

   大多数基于RIA应用的考虑是让应用能够离线运行， 然而与此同时浏览器也在发展，基于网页的本地存贮已经在Google Reader中可以实际使用

   也许某一天浏览器就是一个完美的RIA平台，Web应用只需添加本地存贮支持就可以离线使用──类似于Flex、 Silverlight的RIA技术，与Web应用，哪个更容易被接受，还真难见分晓
