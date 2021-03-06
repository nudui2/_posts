---
title: 刷某体育票务app短信验证码接口-接口安全考究
date: 2016-11-25 23:03:43
tags: [api,app,接口规则]
categories: app-api
top: true
---
### 观察某体育票务app的接口结构
此app内有某语言大神，余心诚向往，隐去app名讳。
短信接口如下：

![短信验证码](http://7q5c85.com1.z0.glb.clouddn.com/api3333.png)
圈1：
- 参数s：应该是对url进行签名
- 参数t：时间戳
- 参数mobile：接收短信验证码的手机
- http/1.1 : http协议
<!--more-->
圈2：
- cookie：该团队应该是原做web，习惯于cookie、session的模式（当然，这个路子是正确的，只是这个名字...暴露了自己的历史包袱）。在app中通过在header中添加参数来实现。此处与本题无关。

圈3：
- ChannelId：一个对于业务相关的参数，无甚可说。
- token：应该是对设备的唯一标识吧。应该不是auth，毕竟还没登录，何来auth。

从上可知，模拟这个【发送短信验证码】请求，最多需要这么几个参数即可。笔者用postman实践，cookie可以不用管它（话说，这个cookie真的有价值吗？），传不传都无所谓。参数t，对方只用于签名算法。

综上，需要参数s、t、参数mobile、参数Channel（放在header中）、参数token（放在header中）。

### 模拟开始
**某月24日：**

![image description](http://7q5c85.com1.z0.glb.clouddn.com/%E6%A8%A1%E6%8B%9Fapi.png)

诸位应当看到，笔者已经告知对方（通过一个多余的参数“tip”），该接口（或者整个app的所有接口），都有可能被模拟，希望对方能够进行修改。**注：**笔者手机号也在区间内，收到了通过程序发送的短信验证码。

**次日：**

![image description](http://7q5c85.com1.z0.glb.clouddn.com/ciri.png)

对方完全任由刷。

### 模拟后话
1. 次日的再次模拟，依然请求成功（笔者的手机号在此序列）。
2. 对方将笔者ip做了特殊处理（此项排除，笔者手机收到了验证码）。
3. 对方没有看到相应日志，没有发现接口已经被模拟。（不太可能，毕竟不是小team，就算是小team，也早该发现）
4. 对方没有看到tip参数，没有在日志中记录收到的全部参数。（感觉还是不可能，都不是小作坊，我这一个岗位一个人的小摊子还会注意到这点。。）
5. 原因究竟是什么呢？

### 结语
1. 笔者毕业三年，路已偏歪，没在大型厂子待过。
2. 可能笔者的整篇文章会见笑于大方家（大神甲：这年轻人太嫩，自以为破解了这个app，其实。。）
3. 不是hacker（水平真的达不到，差的不是一点），却心向往之。
4. ****个人对于接口安全的方案****（方案师承毕业时的团队）：[http://nudui.online/2015/05/16/api接口规则/](http://nudui.online/2015/05/16/api接口规则/)。
5. 求明白人告诉我，我这到底是不是班门弄斧。


