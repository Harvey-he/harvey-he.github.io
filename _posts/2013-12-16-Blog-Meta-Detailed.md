---
layout: post
title: "Meta标签详解"
categories:
- HTML5
tags:
- Meta


---
   
Meta标签详解
====================

###meta简介

meta的英文翻译为“元”，是metainformation，顾名思义，代表他所携带的信息是网页的元信息，这个在单独出现在head标签中的meta标签，可以为HTML文档提供额外信息；

###meta属性

meta属性主要分为两组,新的HTML5标准中，将charset单独拿出来作为了一个属性；这里就不为它单独分组了。示例： `<meta charset="utf-8" />`

**name属性与content属性组合**

name属性用于描述网页,它是以名称/值形式的名称，name属性的值所描述的内容（值）通过content属性表示，便于搜索引擎机器人查找、分类。其中最重要的是description,keywords,robots.
     
**http-equiv属性与content属性**

http-equiv属性用于提供HTTP协议的响应头报文（MIME文档头），它是以名称/值形式的名称，http-equiv属性的值所描述的内容通过content属性表示，通常为网页加载前提供给浏览器等设备使用，其中最重要的是content-type charset提供编码信息，refresh刷新与跳转页面，no-cache页面缓冲，expires网页缓存过期时间。
     
###meta属性详解

我们还是分为两组去做详细阐释
    
**http-equiv属性**   
     
1. content-type属性值
	* 用以定义文件的MIME类型，以及编码信息
	* 示例： ```<meta http-equiv="content-type" content="text/html; charset=UTF-8" />```
        
2. content-language属性值
	* 用以定义页面所使用的语言代码
	* 示例：```<meta http-equiv="content-language" content="zh-CN" />```

3. refresh属性值
	* 用以刷新与跳转(重定向)页面
	* 示例：5秒之后刷新本页面```<meta http-equiv="refresh" content="5" />```
	* 示例：5秒之后转到百度首页```<meta http-equiv="refresh" content="5; url=http://www.baidu.com/" />```
     
4. expires属性值
	* 用以网页缓存过期时间
	* 示例：```<meta http-equiv="expires" content="Sunday 26 October 2008 01:00 GMT" />```
     
5. pragma属性值
	* 只有一个属性值no-cache，浏览器默认是缓存页面的，加上这条信息禁止浏览器缓存页面
	* 示例：```<meta http-equiv="pragma" content="no-cache" />```
     
**name属性** 
     
1. keywords
	* 用以定义页面关键词
	* 示例： ```<meta name="keywords" content="HTML XHTML" />```

2. description
	* 用以定义页面简单描述
	* 示例：```<meta name="description" content="meta详解，描述meta的所有属性使用" />v```
     
3. author
	* 用以定义网页的作者
	* 示例：```<meta name="author" content="harvey-he" />```
     
4. copyright
	* 用以定义网页的版权所有
	* 示例： ```<meta name="copyright" content="© harvey-he" />```

5. date
	* 用以定义网页的制作时间
	* 示例： ```<meta name="date" content="2008-07-12T20:50:30+00:00" />```
     
6. robots
	* 定义网页搜索引擎的索引方式
	* 取值：
		* none：搜索引擎将忽略此网页。
		* noindex：搜索引擎不索引此网页。
		* nofollow：搜索引擎不继续通过此网页的链接索引搜索其他的网页。
		* all：搜索引擎将索引此网页与继续通过此网页的链接索引。
		* index：搜索引擎索引此网页
		* follow：搜索引擎继续通过此网页的链接索引搜索其它的网页。
	* 示例：```<meta name="robots" content="noindex" />```
     
7. viewport
	* 移动web开发关键meta标签，手机浏览器是把页面放在一个虚拟的“窗口”（viewport）中，通常这个虚拟的“窗口”（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。
	* 移动版的Safari浏览器最先引进了viewport这个meta标签，让网页开发者来控制viewport的大小和缩放，其他手机浏览器也基本支持。
	* 取值：
		* width：控制viewport的大小，可以指定一个数值（如：600）或特殊的值（如：device-width为设备的宽度）
		* height：和width相对应，指定高度
		* initial-scale：初始缩放比例，也即是当页面第一次 load 时的缩放比例
		* maximum-scale：允许用户缩放到的最大比例
		* minimum-scale：允许用户缩放到的最小比例
		* user-scalable：用户是否可以手动缩放
	* 作用：
		* viewport并非只是ios上的独有属性，在android、winphone上同样也有viewport。它们要解决的问题是相同的，即无视设备的真实分辨率，直接通过dpi，在物理尺寸和浏览器之间重设分辨率，这个分辨率和设备的分辨率无关。
		* 比如，你拿个3.5寸 640 * 960的iphone4，4.0寸 1280 * 720的小米2，9.7寸 1024*768的ipad，虽然设备的分辨率不同,物理尺寸也不同，但你可以通过设置viewport让它们在浏览器里有相同的分辨率。比如说，你的网站是800px宽，你可以通过设置viewport的width=800，来让你的网站在这三个不同的设备上都刚好满屏显示你的网站。
	* 示例：```<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0">```

###参考资料
[http://www.dreamdu.com/xhtml/tag_meta/](http://www.dreamdu.com/xhtml/tag_meta/)
[http://www.cnblogs.com/stay-foolish/archive/2013/05/06/3052452.html](http://www.cnblogs.com/stay-foolish/archive/2013/05/06/3052452.html)

     
    

