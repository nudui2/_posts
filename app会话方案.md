---
title: app会话方案
date: 2015-05-16 16:04:45
tags: [app,auth]
categories: app-api
top: true
---
### 与web开发不同点
- web中有浏览器角色，保持用户登录状态可以根据cookie、sessionid等策略来实现。
- 而app不能（或不方便、不能自定义内容），开发者需要进行面向app的模拟session实现。
    

---

### 借助工具
- memcached\redis或其他进程外缓存。
    
### 实现过程 
1. 在db中创建auth表，须包含字段：id , userid(或mobile), auth , createtime。
2. 注册时，user表中添加数据后，auth表中也添加记录，auth可自行选择加密方案。
3. 登录时：
 * 1，user表中查找成功。
 * 2，服务端从db中获取auth，放入缓存中。
 * 3，将auth返回给移动端。
4. 移动端每次请求服务端，均须将auth信息放入header中。服务端在拦截器中校验auth（先从缓存中取，如无则取db，然后放入缓存）是否正确、定位是哪个用户。

### 注释
1. web中默认未登录状态。移动端默认为登录状态（每次打开app只要有auth信息就默认为登录）。
2. 在缓存中，auth要设有效时长。
3. 缓存中的数据结构为  auth:userid(mobile)。
4. 当下多数app将注册与登录合二为一，使用手机号+短信验证码实现注册即登录，此时实现方案应相应作出修改，在此不述。
5. web开发也可类似上述方案进行开发，不使用httpsession，原因不述。



