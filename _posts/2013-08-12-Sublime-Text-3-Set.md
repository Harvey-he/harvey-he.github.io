---
layout: post
title: "Sublime Text 3设置指南"
categories:
- IDE
tags:
- Sublime


---

##Sublime Text 3设置指南##

###安装package control###

下载package control源码安装包，并解压：  

[http://yun.baidu.com/share/link?shareid=1372495160&uk=3205258044&third=0&fid=2452604597](http://yun.baidu.com/share/link?shareid=1372495160&uk=3205258044&third=0&fid=2452604597)  

启动sublime text 3，打开菜单Preferences—>Browse Packages...,将解压所得的Package Control文件夹复制到此文件夹

重启Sublime Text 3，按下Ctrl + Shift + P，输入install，出现Package Control: Install Packages，安装成功；

###安装插件###

必安插件：

+ Emmet（原名Zen Coding）
+ Alignment
+ AngularJs Snippets
+ BracketHighlighter
+ jQuery
+ jQuery Snippets
+ JsFormat 
+ SideBarEnhancements
+ TrailingSpaces

###安装主题###

推荐主题：Flatland(这是我最喜欢的主题)  

下载主题包，并解压：[http://pan.baidu.com/share/link?shareid=1618915827&uk=3205258044](http://pan.baidu.com/share/link?shareid=1618915827&uk=3205258044)

启动sublime text 3，打开菜单Preferences—>Browse Packages...,将解压所得的Theme-Flatland文件夹复制到此文件夹

修改 Preferences 文件，通过 Sublime Text 3 的菜单 “Preferences > Settings - User” 可打开用户配置文件，在其中添加（或修改原来的设置）：

```bash
{
    "theme": "Flatland Dark.sublime-theme",
    "color_scheme": "Packages/Theme - Flatland/Flatland Dark.tmTheme"
}
```

保存便即刻生效；

###解决Ubuntu下不能输入中文问题###

第一步：安装开源字体，“文泉驿字体

```bash
sudo apt-get install xfonts-wqy
```

第二步：配置Sublime Text 3的Setting User,添加如下内容

```bash
"font_face": "WenQuanYi Micro Hei Mono"
```

第三步：最后安装一个sublime text 3的插件 InputHelper，用于输入中文

```bash
cd ~/.config/sublime-text-3/Packages
git clone https://github.com/xgenvn/InputHelper.git
```

到此，按下Ctrl + Shift + Z，输入中文；

