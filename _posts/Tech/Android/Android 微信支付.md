---
title: Android 微信支付
date: 2015-06-07 19:51
categories: 
    - Tech
    - Android
permalink: Android-wechat-pay
---

### 1.相关术语 
- 微信开放平台
微信开放平台是商户APP接入微信支付开放接口的申请入口，通过此平台可申请微信APP支付。
平台入口：[http://open.weixin.qq.com](http://open.weixin.qq.com)。
- 微信商户平台
微信商户平台是微信支付相关的商户功能集合，包括参数配置、支付数据查询与统计、在线退款、代金券或立减优惠运营等功能。
平台入口：[http://pay.weixin.qq.com](http://pay.weixin.qq.com)。
- 商户证书
商户证书是微信提供的二进制文件，商户系统发起与微信支付后台服务器通信请求的时候，作为微信支付后台识别商户真实身份的凭据。
- 签名
商户后台和微信支付后台根据相同的密钥和算法生成一个结果，用于校验双方身份合法性。签名的算法由微信支付制定并公开，常用的签名方式有：MD5、SHA1、SHA256、HMAC等。

### 2.接入前期的准备工作和学习资源
-> 申请好微信开放平台账号
-> 创建好一个应用提交申请
-> 在应用详情中申请开通微信支付功能(审核要3-7天，建议提前安排人做好这件事)
![申请流程图](https://i.loli.net/2019/07/29/5d3e8f9129f7f89958.png)
前面三步都完成后，对于开发人员来说应该已经获得下面几个有用数据：
1. AppID (应用申请审核通过后获得)
2. AppSecret (应用申请审核通过后获得)
3. 商户号 (微信支付审核通过后获得)
4. 商户支付密钥key (微信支付审核通过后，通过邮件引导在商户平台设置后获得)

> 关于第4点可参考：[商户支付密钥key的生成与设置](http://help.ecmoban.com/article-2085.html)

-> [Android资源下载](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1419319164&lang=zh_CN)
![](https://i.loli.net/2019/07/29/5d3e8fd18913822222.png)

-> [微信APP支付资源下载](http://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=11_1)
![](https://i.loli.net/2019/07/29/5d3e8fe4e107c86008.png)

在上面两个链接中可以下载到要集成进项目的SDK、开发文档、和两个demo(一个接入demo和一个支付demo)，前期应好好根据文档学习demo，demo是eclipse下开发的，导入后还需将其改为GBK编码，以解决demo中文注释乱码问题。
另外开放平台提供的[Android接入指南](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&lang=zh_CN&token=1be847c3b5d715b3705ae6d7dbd243bd2c7d5a43)应该好好看。

### 3.开发步骤

![](https://i.loli.net/2019/07/29/5d3e90031a96753276.png)

我的项目中，在需要用到微信支付的activity中处理逻辑如下：
```JAVA
// TODO: 1.请求后台生成支付订单
GetPrepayIdTask getPrepayId = new GetPrepayIdTask();
getPrepayId.execute();
// 后台
// ->调微信统一下单API
// ->将从微信拿到的预付单信息(prepay_id)
// ->生成带签名的客户端支付信息
// ->返回信息给app(prepay_id,sign等)
// TODO: 2.根据后台返回的信息生成支付请求
// TODO: 3.发起微信支付请求
```

微信处理完返回给app的返回码对应关系：
![](https://i.loli.net/2019/07/29/5d3e9038af3f453623.png)

不过注意**“如果支付成功则去后台查询支付结果再展示用户实际支付结果。注意一定不能以客户端返回作为用户支付的结果，应以服务器端的接收的支付通知或查询API返回的结果为准。”**

其实只要你能将开始申请拿到的那几个字段替换到微信官方提供的[微信支付demo:wechat_sdk_sample_android_v3_pay.zip](http://pay.weixin.qq.com/wiki/doc/api/download/wechat_sdk_sample_android_v3_pay.zip)里的，然后成功跑通，流程就清楚了。不过需注意的是，官方文档里说的**“商户服务器生成支付订单，先调用统一下单API生成预付单，获取到prepay_id后将参数再次签名传输给APP发起支付。”**这一步，在demo中是在app端模拟实现的，实际开发中还是建议按文档中的来，会更加安全性。

> 我摸索阶段除了微信官方提供的文档和demo，下面文章给过我帮助，谢谢:

[Android微信支付](http://blog.fangjie.info/android%E5%BE%AE%E4%BF%A1%E6%94%AF%E4%BB%98/)
[Android学习之 移动应用<App>微信支付集成小结](http://blog.csdn.net/janice0529/article/details/38051987)
