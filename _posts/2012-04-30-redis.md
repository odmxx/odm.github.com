---
layout: post
title: redis windows
description:
- redis
categories:
- redis 
tags:
- redis
---
https://github.com/dmajkic/redis/downloads
下载
redis-2.4.5-win32-win64.zip 

启动Redis服务 （conf文件指定配置文件，若不指定则默认）：
`redis-server.exe redis.conf`
另开窗口
`redis-cli.exe -h localhost -p 6379`
set key dd
get key

<hr/>
Redis官网上推荐的Java包是Jedis

<pre class="prettyprint">
import redis.clients.jedis.Jedis;

public class Client {

	public static void main(String[] args) {
		Jedis jj = new Jedis("localhost");
		jj.set("key1", "I am value 1");
		String ss = jj.get("key1");
		System.out.println(ss);
	}

}
</pre>

<hr/>
追溯NoSQL的历史
http://blog.nosqlfan.com/html/8.html