---
title: nginx+rtmp服务器
date: 2017-03-21 21:20:26
tags:
    - Mac搭建nginx+rtmp服务器
---

1、查看是否已经安装了Homebrew

    $ man brew

2、如果没有安装Homebrew则安装
    
    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

3、卸载Homebrew安装

    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

4、安装nginx,先clone nginx项目到本地

    $ brew tap homebrew/nginx

<!--more-->

5、执行安装

    $ brew install nginx-full --with-rtmp-module

6、此时, nginx和rtmp模块就安装好了，输入命令:

    $ nginx
    $ 在浏览器里打开http://localhost:8080
