---
layout: post
title: 吐嘈一下 Redcarpet
description:
- 
categories:
- 无 
tags:
- 
---
http://www.worldhello.net/gotgithub/appendix/markups.html
GitHub使用Redcarpet作为Markdown的解析工具，并添加了额外的语法扩展。网址：http://github.github.com/github-flavored-markdown/

然后在_config.yml中
markdown: rdiscount
改成
markdown: redcarpet

gem install  redcarpet


C:/RailsInstaller/Ruby1.9.3/lib/ruby/gems/1.9.1/gems/jekyll-0.11.2/lib/jekyll/converters/markdown.rb:91:in `convert': undefined method `new' for Redcarpet:Module (NoMethodError)

去ruby.rb 91行看
       Redcarpet.new(content, *@redcarpet_extensions).to_html


http://www.ruby-taiwan.org/topics/39
Redcarpet 的 render 實作改變 ( 1.0 -> 2.0 )

<pre class="prettyprint">
#Redcarpet.new(content, *@redcarpet_extensions).to_html
html_renderer = Redcarpet::Render::HTML.new({
	:autolink => true,
	:fenced_code_blocks => true, 
	:tables => true,
	:strikethrough => true,
	:lax_htmlblock => true,
	:no_intraemphasis => true
})
markdown = Redcarpet::Markdown.new(html_renderer)
content = markdown.render(content)
</pre>
改了之后发现渲染结果非常的怪，放弃

