---
layout: post
title: 通过Goagent, github https push
description:
- Goagent 访问github
categories:
- git
tags:
- github
---
github中建好库,会提示添加远程

`git remote add origin git@github.com:ddatsh/blog.git`
上海联通20M，发现git协议时经常无响应
所以想通过代理(翻墙)出去提交

网上文章  在windows上通过代理访问github.com
关键词
git:// 协议 cygwin socat

connect.exe

https:// 协议 http(s) proxy

另外一篇文里涉及另一个软件  corkscrew

##我的办法
####GoAgent代理,直接https操作

#### _netrc文件(*nix下是.netrc)
machine github.com
login zhangthe9
password xxxxxxxx

machine github.com
login ddatsh
password xxxxx

####git remote add
`git remote add origin git@ddatsh.github.com:ddatsh/blog.git`
改成
`git remote add origin https://ddatsh@github.com/ddatsh/blog.git`

####git config http.proxy
`git config http.proxy http://127.0.0.1:8087/`
或者直接加进全局
`git config --global http.proxy http://127.0.0.1:8087/`
