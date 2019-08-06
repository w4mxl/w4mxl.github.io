---
date: 2016-10-23 15:12
title: 小米Max 换屏及刷国际版 Rom
categories: Life
permalink: 小米Max换屏及刷国际版Rom
---


### 背景介绍

这次折腾的这台小米Max是我父亲的。早两年我给他买的是一华为手机配一翻合式的保护套，稳稳当当用了两年多还不错。因为保护套用久后有点破烂了，上个月我就给他拿下来扔了。之后没多久的，啪，手机掉地上屏幕给摔碎了。

今年父亲平时没啥事会出去开开 Uber 和滴滴，找补点事情做，4寸的华为机用来导航看着是有点累。刚好乘着这次碎屏事件想给他直接换一屏幕大点的手机。在一系列大屏手机中最后入了今天的主角小米Max配一钢化膜。可曾想，才用一个多月摔了两次，第一次侥幸是钢化膜裂了，第二次屏幕成功 big bang 。ヽ( ´ー｀)ノ

<!-- more -->

### 换屏

大致 Google 了解了下小米Max的换屏成本：送小米售后换屏大概需要 ¥440，某宝单买屏幕总成 ¥150～400不等。最后，选择在某宝买了小米Max的屏幕总成，加运费 ¥258。选他家原因是，店家给在售的每种型号的屏幕都做了换屏教学视频并会赠送买家相应自己换屏需要的材料。提醒：某宝水深，选屏谨慎。

2016.10.20  晚上11点左右开始自己动手拆机换屏，到完全换好大概花了1小时30分钟。效果不错，心满意足。

![](http://ww1.sinaimg.cn/large/006y8lVagw1f927suleeij31kw23u4qp.jpg)
换屏前


![](http://ww2.sinaimg.cn/large/006y8lVagw1f927tac4q3j31kw23uhdt.jpg)
换屏

### 刷Rom

MIUI 发展成 ADUI 由来已久了，虽然手机不是我在用，但是每次帮我父亲在上面弄点东西的时候，系统中随处可见的广告还是很难忍，小米全家桶对我父亲来说也几乎用不到。考虑刷个其他 Rom 给父亲用着舒服点。起先去 xda 论坛看了下，是有基于 android aosp 开发的原生型 Rom。不过有点担心太原生父亲用着不习惯，后来就决定给他刷 MIUI 国际版 Rom。国际版是完全告别了 ADUI 的称号，因为系统完全没广告。

1. 申请解锁 [小米手机解锁申请页面](http://www.miui.com/unlock) (大概10分钟后就收到解锁已经通过的短信)
2. 下载解锁工具 [地址](http://www.miui.com/unlock/done.html)
3. 按照上面页面提示的步骤操作 （操作前要保证当前系统中登录上小米账号并且与申请解锁的账号一致）
4. 卡刷：http://en.miui.com/a-232.html (卡刷教程看着更简单，但是实测后发现不行，会提示“更新包验证失败，无法正常更新”)
5. 线刷：http://en.miui.com/a-234.html 注意线刷是要在windows电脑上操作的。然后按链接中的教程一步步走。（大体是，先下载安装Miflash刷机工具，再安装这个工具的时候，如果没pc上没安装过 .net framwork version 3.5 会提示要先安装。下载对应手机的线刷包（我下载的是 Xiaomi Mi Max 32GB Latest Global Stable Version Fastboot File Download ）。然后通过Miflash进行刷机就好了。）
6. 刷好之后手机会自动重启进入新系统。
7. 最后通过帖子http://en.miui.com/thread-318850-1-1.html，给手机换了思源黑体字体。

![](http://ww1.sinaimg.cn/large/006y8lVagw1f927up0vxdj30kv08hgmu.jpg)
刷机


![](http://ww3.sinaimg.cn/large/006y8lVagw1f927vgmpc7j31kw1kw1if.jpg)
最终成果

：）

