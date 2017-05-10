---
title: 多客户端使用hexo方案
date: 2017-05-10 10:57:16
tags: [hexo]
categories: [hexo,jack]
---

### 痛点

```
hexo搭建在本机，单一客户端编辑固然ok，然不方便在多台终端中同时使用。
```
### 方案


- 1，选取云服务器作为中心服务器，此服务器上安装hexo并配置好github账号。
- 2，在github上创建项目“_posts”，将其pull到hexo的source目录下。
- 3，在服务器中通过脚本，每15min执行如下操作:

```
1，github上pull最新_posts。
2，hexo clean
3，hexo g
4，hexo d
```
- 4，每个客户端都将_post项目pull在本机，每次书写玩md直接提交即可。

### 注意

```
第三步中的脚本书写，最好能加入一个running的标记，以防crontab的定时任务与手动部署冲突
```

