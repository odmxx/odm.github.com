---
layout: post
title: blog改造
categories:
- 无
description: 原型,评论,代码高亮,css,优化
---
原型参考
http://yihui.name/cn
下载地址
https://github.com/yihui/cn

# 
- 导航放上面
- 评论用**多说**,加个按钮，切换到disqus
- **jiathis**,现已不用
- 代码高亮用 **google-code-prettify**

###css主要变化
- 响应式CSS  
我的23寸显示器，1920*1080分辨率,需要把字体设大点

<pre class="prettyprint">
@media screen and (max-width:1920px){body{font-size:26px;}}
@media screen and (max-width:1280px){body{font-size:16px;}}
</pre>

- markdown忽略空格问题  
想让一些(非全部)段落(即p标签)首行缩进几个字符，用 pre-wrap,还不是很理想
<pre class="prettyprint">
p{padding:.3em 0;white-space:pre-wrap;}
</pre>

**圆角**  
标题 **text-shadow**,不用了

参考 **浩宇啸天** ,blog 首页换成分页式,加个Archives

将所有JS(jquery等)和CSS压缩至同一页面，发现输出的静态站点太大
除附件（图片），800k的东西，生成出来20M左右
不放在一起，就1.4M

~~页面最下面,统计脚本,只用百度~~
所有统计都不用了
