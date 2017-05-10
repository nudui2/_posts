---
title: ssh免密
date: 2016-12-04 00:00:50
tags: [jack,ssh]
---
### ssh免密登录
1. 将本地.ssh目录下的id_rsa.pub文件内容拷贝。
2. 远程登录，到相应的.ssh目录下，将1中内容拷贝至authorized_keys中。
<!--more-->
### 注
1. chmod 700 ~/.ssh
2. chmod 600 ~/.ssh/authorized_keys 

### 测试
本机，ssh git@1.1.1.1

### 搭建git

https://segmentfault.com/a/1190000002729796#articleHeader7