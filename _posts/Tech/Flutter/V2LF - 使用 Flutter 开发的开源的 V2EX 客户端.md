---
title: V2LF - 使用 Flutter 开发的开源的 V2EX 客户端
date: 2019-05-14 07:33:12
categories: 
    - Tech
    - Flutter
permalink: v2lf-open-source
---

## V2LF 正式开源

GitHub 地址：https://github.com/w4mxl/V2LF

如果您不知道 V2LF 是啥，可以先看我之前在 v2ex 发的贴子来了解：

[邀请体验： V2LF - 用 Flutter 开发的 V2EX App
](https://www.v2ex.com/t/548936#reply164)

自从发了体验邀请之后，挺多用户给了我宝贵建议和反馈，**感谢你们**。其中有一位，他算是 v2ex 重度用户了，在 iMessage 上断断续续给我提“需求”，我们交流的还挺欢乐。

本次开源采用了 **[GPL v3.0 开源许可](https://www.wikiwand.com/zh/GNU%E9%80%9A%E7%94%A8%E5%85%AC%E5%85%B1%E8%AE%B8%E5%8F%AF%E8%AF%81)** ，期待得到大家更多的参与。只要我还会逛 v2ex，就会继续完善 V2LF 这个项目。

我相信这次开源会是一个新的开始！

<!-- more -->

## 上架说明

我原本是打算上架了App Store 和 Google play 之后就开源出来的，play那边很快搞定，奈何 App Store 那边审核遇到些阻碍，和审核人员来回沟通了几次。目前账号审核状态，迟迟没有进展，只能等等看了 ¯\\_(ツ)_/¯ 。我希望能早点审核好，然后顺利上架。

![App Store 审核过程（左） & 最近一次 reject （右）](https://i.loli.net/2019/05/14/5cda1b956a21156246.jpeg)

App Store 和 Google play 我都是定价 ¥12 的。当然我没有指望从这个 app 可以赚钱，我很清楚它的受众群其实很有限的。之所以设置付费，纯粹是好奇，想试试看会有多少用户真的喜欢这个app到愿意付费支持的程度。如果有，哪怕个位数，我也会很开心。当然我也提供了完全免费使用的途径，酷安、TestFlight，或者直接编译运行源码。

我在开发 V2LF 的时候也陆续体验了一些其它同类app，列在下面，你们感兴趣也可以去下载使用，多尝试挺好的。不爱尝试的同学，手机浏览器用网页版v2ex体验也是不错的。

* [V2EX+ (android)](https://play.google.com/store/apps/details?id=com.czbix.v2ex)
* [V2er - 好用的V2EX客户端 (android)](https://play.google.com/store/apps/details?id=me.ghui.v2er)
* [V2er - Best client for V2EX (iOS)](https://itunes.apple.com/cn/app/v2er-best-client-for-v2ex/id1308118507?mt=8)
* [V2EX - 创意工作者们的社区。(iOS)](https://itunes.apple.com/cn/app/v2ex-%E5%88%9B%E6%84%8F%E5%B7%A5%E4%BD%9C%E8%80%85%E4%BB%AC%E7%9A%84%E7%A4%BE%E5%8C%BA/id1078157349?mt=8)
* [VeXplore Lite - V2EX第三方开源客户端 (iOS)](https://itunes.apple.com/cn/app/vexplore-lite-v2ex%E7%AC%AC%E4%B8%89%E6%96%B9%E5%BC%80%E6%BA%90%E5%AE%A2%E6%88%B7%E7%AB%AF/id1191058321?mt=8)

## 下载链接

* V2LF iOS TestFlight： https://testflight.apple.com/join/cvx4MQuh
* V2LF 酷安：https://www.coolapk.com/apk/221879
* V2LF Google Play：https://play.google.com/store/apps/details?id=io.github.w4mxl.v2lf

## 一点想法

日常在公司工作，只管写代码实现功能就好。而到开发个人项目的时候就会发现，实现功能前得自己设计 UI/UX，起码是一个框架图。公司要上架时可能只负责打好包就行，文案、截图、预览啥的找产品或者找设计张口要就好。而到自己项目都得亲力亲为，初次弄这些的时候往往觉得比写代码更辛苦，隔行如隔山。当然了，也好的一面，比如用了好些年macOS，为了做预览，第一次用上了iMovie app。