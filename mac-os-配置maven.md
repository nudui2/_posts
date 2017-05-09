---
title: mac os 配置maven
date: 2014-07-16 16:29:03
tags: maven
categories: maven
toc: true
---

### 下载maven
http://maven.apache.org/download.cgi


### 解压
解压到 /usr/local   重命名为maven


### 新建（如无）.bash_profile
编辑内容：

```
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home

M3_HOME=/usr/local/maven3

PATH=$M3_HOME/bin:$PATH

export JAVA_HOME

export M3_HOME

export PATH
```

### 测试
`mvn -version`

### 如未生效 
`source .bash_profile ` 使之生效


