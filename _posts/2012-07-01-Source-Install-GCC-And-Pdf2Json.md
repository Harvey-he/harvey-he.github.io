---
layout: post
title: "Centos6.0 源码编译安装gcc4.6.1并安装pdf2json"
categories:
- Linux
tags:
- linux,gcc,服务器,pdf2json


---
##Centos6.0 源码编译安装gcc4.6.1并安装pdf2json##

>这几天接到个任务，要在Centos上源码编译安装PDF2JSON[http://code.google.com/p/pdf2json/](http://code.google.com/p/pdf2json/)，试了很多次都编译通不过，总是出错，于是决定在ubuntu上装一把，结果一次性通过，思考良久，如果pdf2json不依赖系统的库函数的话，那么在整个安装过程中，唯有俩者的编译器不一样，ubuntu是gcc-4.6.1而Centos是gcc-4.4.6，因为是yum安装的 所以没有最新版本的，于是我猜想是编译器版本太低，最后经过测试果不其然，还真是centos的gcc编译器版本太低了！下面是我的整个安装过程，作为自己的笔记！

```bash
yum install gcc*

wget http://ftp.gnu.org/gnu/mpfr/mpfr-3.1.0.tar.bz2
wget http://ftp.gnu.org/gnu/gmp/gmp-5.0.4.tar.bz2
wget http://www.multiprecision.org/mpc/download/mpc-0.9.tar.gz
wget http://ftp.gnu.org/gnu/gcc/gcc-4.6.1/gcc-4.6.1.tar.bz2

tar -vjxf gmp-5.0.4.tar.bz2 -C /usr/src/
tar -vjxf mpfr-3.1.0.tar.bz2 -C /usr/src/
tar -vxf mpc-0.9.tar.gz -C /usr/src/
tar -vjxf gcc-4.6.1.tar.bz2 -C /usr/src/


=============================================================================

cd ~

mkdir gmp-build

cd gmp-build

/usr/src/gmp-5.0.4/configure --prefix=/usr/local/gmp-5.0.4

make

make check

make install

=============================================================================

cd ~

mkdir mpfr-build

cd mpfr-build

/usr/src/mpfr-3.1.0/configure --prefix=/usr/local/mpfr-3.1.0 --with-gmp=/usr/local/gmp-5.0.4

make

make check

make install

=============================================================================

cd ~

mkdir mpc-build

cd mpc-build

/usr/src/mpc-0.9/configure --prefix=/usr/local/mpc-0.9 --with-mpfr=/usr/local/mpfr-3.1.0 --with-gmp=/usr/local/gmp-5.0.4

make

make check

make install

=============================================================================

cd ~

mkdir gcc-build

cd gcc-build

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/mpc-0.9/lib:/usr/local/gmp-5.0.4/lib:/usr/local/mpfr-3.1.0/lib

/usr/src/gcc-4.6.1/configure --prefix=/usr/local/gcc-4.6.1 --with-mpc=/usr/local/mpc-0.9 --with-mpfr=/usr/local/mpfr-3.1.0 --with-gmp=/usr/local/gmp-5.0.4 --enable-languages=c,c++ --enable-threads=posix --disable-checking --disable-multilib

make && make install


==============================================================================

cd /usr/bin

ln -s /usr/local/gcc-4.6.1/bin/gcc gcc46
ln -s /usr/local/gcc-4.6.1/bin/g++ g++46

cd /etc

vi bashrc

行尾添加：
LD_LIBRARY_PATH=:/usr/local/mpc-0.8.1/lib:/usr/local/gmp-4.3.2/lib:/usr/local/mpfr-2.4.2/lib:/usr/local/gcc-4.5.0/lib

export LD_LIBRARY_PATH

重启

==============================================================================

wget http://pdf2json.googlecode.com/files/pdf2json-0.52-source.tar.gz

tar zxvf pdf2json-0.52-source.tar.gz

./configure

make && make install
```