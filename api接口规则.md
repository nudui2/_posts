---
title: api接口规则
date: 2015-05-16 16:07:48
tags: [api,app,接口规则]
categories: app-api
top: true
---
### 如想看如何防刷请求，请看【防刷】


### header
```
"client":{
    "appnm" : "XXX", （app name）
    "appVer" : "1.0.0",    （app版本）
    "clientType" : "ios",   （系统类型）
    "os" : "iPhone OS 10.0.3",（系统版本）
    "model" : "iPhone Simulator",（手机型号）
    "screen" : "320x568",（屏幕分辨）
    "channel" : "app_store",
    "deviceid" : "E96B0235-F60C-49F4-B2F9-F1B1041C7E51"（设备号）
}
```
<!--more-->
```
"auth":{
    "auth": "audbbiuf7q74asdh8fa0s9dqjashdugfasd",（用户唯一标识，如有则认为已登录）
    "sign": "fad22321acbd122121",  （签名）
    "ts" : "1231231283213"（时间戳）
    "rand" : "12121212"（一个随机数）
}
```

### url签名

可随意定义，别都是MD5
`sign = MD5 ( url + ts + "自定义一个key" + rand )`
 
服务端每次请求必须校验sign

### 备注
1. 移动端与服务端交互的每个请求，header必须加上client\auth中参数。
1. 接口服务端返回为json类型，为方便移动端，json中数据类型全部为string。
1. 如果sign不正确，服务端不处理该请求，直接返回错误码。

### **防刷：**
- 校验sign，hack看到有ts，可能以为每次请求更换ts即可，实则不然，sign的算法里还有个自定义的key，如此sign很难正确。
- 如对方使用与上一次请求相同的sign，sign正确则url、ts、rand都与上一次相同。此时服务端开辟一个LRU缓存，对请求进行**是否重复**的判断。map.get(k)是否有值，如有，则为重复请求，返回错误码。我的k：url + ts + rand;
- **短板**：在访问量超大的情况下，ts必定重复（毫秒），rd也可能重复，此时只能建议用多个rand来去重，用以保障请求的唯一性。
- **短板**：且这个LRU缓存会越来越臃肿。所以，建议对不同的url，开辟不同的缓存。






    

