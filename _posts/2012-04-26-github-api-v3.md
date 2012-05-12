---
layout: post
title: github API v3 使用
description:
- github API v3 使用
categories:
- Git
tags:
- github API
---
想用github api提供的功能建个 repo
http://developer.github.com/v3/repos/


<pre class="prettyprint">
curl -d "{\"name\": \"aabb\" }"  -u "用户名:密码" https://api.github.com/user/repos -v
</pre>


>参照 http://www.anttna.com/archives/354.html
>使用curl测试GeolocationAPI接口
>
>下面我们通过curl测试该格式是否正确。
>
>命令格式: curl -d ‘post的数据’ http://www.google.com/loc/json
>
>这里只需要用到curl的-d参数，-d后面跟的是post的数据内容
>
>在命令行下输入 curl -d ‘ 后回车，粘贴上面的json格式数据回车，再输入 ‘ http://www.google.com/loc/json”回车，就可以看到google的返回结果了。
>
>windows版curl和linux有点小区别，因为windows cmd对 ” ‘ 符号处理和linux不一样，windows版curl发送时要把 ” 换成 \”,而且整个命令要写成一行
>如下所示:
>
>curl -d "{\"version\": \"1.1.0\" ,\"host\": \"maps.google.com\",\"access_token\": \"2:k7j3G6LaL6u_lafw:4iXOeOpTh1glSXe\",\"home_mobile_country_code\": 460,\"home_mobile_network_code\":0,\"address_language\": \"zh_CN\",\"radio_type\": \"gsm\",\"request_address\": true ,\"cell_towers\":[{\"cell_id\":36526,\"location_area_code\":14556,\"mobile_country_code\":460,\"mobile_network_code\":0,\"timing_advance\":5555}]}"  http://www.google.com/loc/json
>
>通过curl可以方便的测试各种json参数组合