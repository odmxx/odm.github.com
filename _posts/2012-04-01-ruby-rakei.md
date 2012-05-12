---
layout: post
title: ruby+gem常用命令
description: 常用命令
categories:
- ruby
tags:
- ruby
---
	ruby -v #查看ruby 版本
	ruby -e ''require"watir"; puts Watir::IE::VERSION''　#查看watir版本
	gem -v #gem版本
	gem update #更新所有包
	gem update --system #更新RubyGems软件
	gem install rake #安装rake,从本地或远程服务器
	gem install rake --remote #安装rake,从远程服务器
	gem install watir -v(或者--version) 1.6.2#指定安装版本的
	gem uninstall rake #卸载rake包
	gem list d #列出本地以d打头的包
	gem query -n ''[0-9]'' --local #查找本地含有数字的包
	gem search log --both #从本地和远程服务器上查找含有log字符串的包
	gem search log --remoter #只从远程服务器上查找含有log字符串的包
	gem search -r log #只从远程服务器上查找含有log字符串的包
	gem help #提醒式的帮助
	gem help install #列出install命令 帮助
	gem help examples #列出gem命令使用一些例子
	gem build rake.gemspec #把rake.gemspec编译成rake.gem
	gem check -v pkg/rake-0.4.0.gem #检测rake是否有效
	gem cleanup #清除所有包旧版本，保留最新版本
	gem contents rake #显示rake包中所包含的文件
	gem dependency rails -v 0.10.1 #列出与rails相互依赖的包
	gem environment #查看gem的环境


	1,
	ruby之间的引用全部是源代码的引用，为了规范类库的管理，gems出现了。
	gems是ruby源代码管理工具，代码按照一定的目录结构被组织成一个lib。
	详见http://www.javaeye.com/topic/320384
	Gem是第三方Ruby库，netbeans提供了Ruby Gems管理器，可以用来添加和维护gem,Tools > Ruby Gems。
	rails和rake等都被rubygems管理。


	  查看本机的gems:  gem list --local 
	  看看rubyforge.org上的gems:  gem list --remote
	  删除某个版本的gem，例如gem uninstall rails -v=2.3.4

	有一本书叫<Ruby Gems开发实战>

	2,
	Rake(http://rake.rubyforge.org)是一门构建语言，和make(www.gnu.org/software/make/)
	ant(http://ant.apache.org)很相像。Rake是用Ruby写的，它支持它自己的DSL用来处理和维护
	Ruby应用程序。Rails用rake的扩展来完成多种不同的任务.
	详见http://www.javaeye.com/topic/300375
	rake教程:http://railsenvy.com/2007/6/11/ruby-on-rails-rake-tutorial
	    翻译:http://hi.baidu.com/%D0%C7203/blog/item/ebda2dd09f1d698ea1ec9c7a.html