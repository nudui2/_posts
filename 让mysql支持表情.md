---
title: 让mysql支持表情
date: 2016-06-16 16:00:57
tags: [mysql,emoji]
categories: mysql
toc: true
---
### 修改 /etc/my.cnf

```
[client] 
default-character-set = utf8mb4

[mysql] 
default-character-set = utf8mb4
<!--more-->
[mysqld] 
character-set-client-handshake = FALSE 
character-set-server = utf8mb4 
collation-server = utf8mb4_unicode_ci 
init_connect='SET NAMES utf8mb4'

```
### 代码中
tomcat 6 + 、jetty 6 + 均在内部支持emoji，无须做任何代码上的修改即可


