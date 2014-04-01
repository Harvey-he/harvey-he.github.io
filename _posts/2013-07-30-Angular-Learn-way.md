---
layout: post
title: "AngularJs学习总结"
categories:
- Javascript
tags:
- AngularJs


---

##AngularJs学习总结##

>应项目的需要，一个月之前开始做WebComponents、Javascript MVC框架的技术调研，由于重点是想做组件化，所以就没有考虑Backbone（去年就小试牛刀，太难用了)及其他的mvc框架，所以重点看了Ploymer，ploymer也是google的库，这个实在是未来的未来，很多东西都没有成为标准，如shadow dom也就chrome可以很好的支持，所以最终放弃，再后看了facebook的react和twitter的flight，这俩个由于版本过低，还没有正式发布，也只好作罢，偶然的机会，结识了AngularJs,一下子被他的特性吸引

###五大特性###
1. 双向数据绑定；
2. 模板；
3. MVC，准确说是MVVM；
4. 依赖注入；
5. 指令（这个灰常强大，有了它我们就可以做组件了）；

关于着五大特性的介绍可以参考Gbin1的这篇文章：
[http://www.gbin1.com/technology/javascript/20120717-AugularJS-features/](http://www.gbin1.com/technology/javascript/20120717-AugularJS-features/)

看完这篇文章，也可以让自己对AngularJs有一个大体的了解！

>如果想要通过AngularJs的官方文档来学习Angular还是有一定困难的，而且官方的示例也不是很多，他的Tutorial倒是还不错，是以一个实际的项目做引导，一步步的了解AngularJs的种种特性，英文不错的话倒是可以看看，或者直接那Demo项目的源码来看也是不错地选择；

###学习AngularJs###
1. 开始学习之前应该先了解下AngularJs的原理及基本概念，达到知其然知其所以然；  
基本概念及原理：  
英文：[http://docs.angularjs.org/guide/concepts](http://docs.angularjs.org/guide/concepts)  
中文：[http://www.angularjs.cn/#/A00q](http://www.angularjs.cn/#/A00q)  

2.  学习完成AngularJs的原理及基本概念，就可以跟着官方出品的Tutorial小试牛刀了，Tutorial的Demo项目是一个类似与中关村等的电子类产品报价介绍网站，只包含基本的手机列表和手机详情！  
英文：[http://docs.angularjs.org/tutorial](http://docs.angularjs.org/tutorial)  
中文：[http://www.ituring.com.cn/minibook/303](http://www.ituring.com.cn/minibook/303)（中文的这份翻译的文档，在做单元测试的时候会有一点错误的说明，可以转回英文看一眼就好）  

3. 学习完成以上的AngularJs的知识，就可以clone一份angular-seed大展拳脚了！不过下山大展拳脚之前，总要听听师傅（过来人）的忠告，推荐以下这俩篇博文：  
尘埃落定的最佳实践：[http://www.lovelucy.info/angularjs-best-practices.html](http://www.lovelucy.info/angularjs-best-practices.html)   
破狼的经验总结：[http://www.cnblogs.com/whitewolf/archive/2013/03/24/2979344.html](http://www.cnblogs.com/whitewolf/archive/2013/03/24/2979344.html)  

4. 好了！可以下山了！  
下载seed，开始闯荡江湖吧！[https://github.com/angular/angular-seed](https://github.com/angular/angular-seed)  

>现在的前端开发，有非常好的构建工具选择，我首推grunt，grunt就像一个手动的IDE，闯荡江湖，拥有这样的上乘武功绝学，非常有必要；

###使用Grunt构建AngularJs项目###
使用grunt构建，让你拥有飞一般的感觉；

1. 学习Grunt  
如果你还不会使用Grunt，那这俩篇文章是很不错的入门选择：
[http://docs.spmjs.org/contrib/simple-grunt](http://docs.spmjs.org/contrib/simple-grunt)  
[http://www.jankerli.com/?p=1628](http://www.jankerli.com/?p=1628)  

 

2. 使用ng-Boilerplate，一个开源的基于AngularJs的Grunt构建  
[https://github.com/joshdmiller/ng-boilerplate](https://github.com/joshdmiller/ng-boilerplate)（强烈推荐）  

###其他资料补充###
AngularJs中文社区：[http://www.angularjs.cn](http://www.angularjs.cn)

Angular-UI：[http://angular-ui.github.io/](http://angular-ui.github.io/)  