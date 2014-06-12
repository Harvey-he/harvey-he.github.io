---
layout: post
title: "Nginx 搭建流媒体服务器（centOS）"
categories:
- Nginx
tags:
- nginx,流媒体,服务器


---
##Nginx 搭建流媒体服务器（centOS）##

###1. 安装gcc###

命令：  

```bash
yum –y install wget tar gcc*
```

等待安装完毕………………

###2. 安装libssl###

命令：  

```bash
yum –y install wget tar libssl*
```

等待安装完毕………………

###3. 安装pcre###

命令：  

```bash
yum –y install wget tar pcre*
```

等待安装完毕………………

###4. 安装openssl###

命令：  

```bash
yum –y install wget tar openssl*
```

等待安装完毕………………

###5. 安装popt###

命令：  

```bash
yum –y install wget tar popt*
```

等待安装完毕………………

好！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！

到此为止；所有的nginx依赖包安装完毕！

接下来开始编译安装流媒体服务器

==============================================================================

###1. 下载nginx源码包###

命令：  

```bash
wgethttp://www.nginx.org/download/nginx-1.0.11.tar.gz  
tar zxvf nginx-1.0.11.tar.gz
```
###2. 添加h.264支持模块包###

下载nginx_mod_h264_streaming包；

命令： 
 
```bash
wget http://h264.code-shop.com/download/nginx_mod_h264_streaming-2.2.7.tar.gz
tar zxvfnginx_mod_h264_streaming-2.2.7.tar.gz
```
修改解压文件下

src文件夹下的ngx_http_streaming_module.c文件

将此语句块注释掉；

修改后将此模块文件夹拷贝到nginx解压后的文件夹中；

###3. 添加防盗链模块###

下载NginxHttpAccessKeyModule

命令： 
 
```bash
wget http://wiki.nginx.org/images/5/51/Nginx-accesskey-2.0.3.tar.gz  
tar -zxvf Nginx-accesskey-2.0.3.tar.gz
```
 

修改文件夹下修改下配置文件讲config文件中的“$HTTP_ACCESSKEY_MODULE”改成“ngx_http_accesskey_module”，不改的话没办法开启防盗链模块。

修改后的将此模块文件夹拷贝到nginx解压后的文件夹中；

###4. 开始编译安装：###

a)  
       
```bash
useradd stream
```
b)
 
```bash
./configure--prefix=/usr/local/nginx 
--user=stream 
--group=stream 
--with-http_stub_status_module 
--with-http_flv_module 
--add-module=./nginx-accesskey-2.0.3 
--add-module=./nginx_mod_h264_streaming-2.2.7 
--with-http_ssl_module 
--with-cc-opt='-O3' 
```
 
（注意：如上的命令都在一行内，每个--与前一句话都有一个空格隔开）

c) 
         
```bash
make && make install
```

安装完成后的默认路径为：/usr/local/nginx/

修改conf文件夹下的配置文件：nginx.conf
 

```bash
worker_processes  1;
#pid        logs/nginx.pid;
events {
    worker_connections  1024;
}
http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on;  
    keepalive_timeout  65;
    server {
        listen       80;
        server_name  192.168.203.149;
        #limit_rate_after 5m;    ####在flv视频文件下载了5M以后开始限速
        #limit_rate 512k;         ####速度限制为512K      
        location / {
            root   html;
            index  index.html index.htm;
        }
        location ~ \.flv$ {
            flv;
        }
        location ~ \.mp4$ {
            mp4;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }
}
```
 

###5. 将nginx做成Services；###

命令：

```bash
wget -c http://soft.vpser.net/lnmp/ext/init.d.nginx
cp init.d.nginx /etc/init.d/nginx
chmod +x /etc/init.d/nginx
/etc/init.d/nginx start
```
 

===============================================================================

安装yamdi
yadmi的作用是为flv文件添加重要帧，才能完成拖动播放
###下载yadmi###

```bash
wget http://sourceforge.net/projects/yamdi/files/yamdi/1.4/yamdi-1.4.tar.gz/download
```

###安装yadmi###
```bash
tar xzvfyamdi-1.4.tar.gz
cd yamdi-1.4
make &&make install
```
运用方法：

```bash
yamdi -i input.flv -o out.flv
```