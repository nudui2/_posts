---
title: tomcat加载两次spring
date: 2016-07-16 15:57:16
tags: [tomcat,spring,疑难杂症]
categories: [疑难杂症,jack]
---

### 1，为了达到通过ip：端口进行访问 ，做了如下配置：
<!--more-->
 ![](http://img.blog.csdn.net/20160823131643542?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

### 2，然而，host标签加载一次webapps里面的项目 ， context标签加载一次docbase的项目，于是造成了两次加载。
### 3，解决办法：在host标签加一个 deployIgnore=".*项目名.*" ， 这样，host就不会加载。

