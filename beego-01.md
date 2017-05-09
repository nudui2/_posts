---
title: beego(01)
date: 2016-11-21 16:52:21
tags: beego
category: beego
---
### start
get beego : https://my.oschina.net/ichendong/blog/761467

gov docs : https://beego.me
### sublime

mac环境下快速启动工作目录


```
rm /usr/local/bin/subl

ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

```
在 ~/ 目录下创建.sh

```
vim work_hello.sh

```
work_hello.sh ：
```
#!/bin/bash
subl /Users/jack/gopath/src/hello
```
对该sh赋予执行权限

```
chmod 777 work_hello.sh
```

开始工作


```
cd
./work_hello.sh
```

自动在sublime中打开工作空间。如有多个工作空间，则在~/目录下创建多个sh即可
