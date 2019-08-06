---
title: Pushbullet-实时的跨设备、跨平台的复制粘贴及推送工具
date: 2014-8-25 11:23:55
categories: Life
permalink: Pushbullet-introduce
---

一. 简单介绍
二. 应用场景
三. 安装使用

##简单介绍　
Pushbullet是为数不多的跨平台应用中一款简单实用型应用。我已经不记得是从什么时候从哪里了解到这个工具的。不过从我的app使用记录中可以查到最早的一条推送日期是2013-04-01，当时是把电脑上的一条笔记推送到我的米1上的。过程中我曾将早期版本升级后出现的bug发邮件反馈给Pushbullet开发者Ryan，他也很快答复说下个版本更新会将bug修复。
　　
简单来说通过使用Pushbullet，1.可以将文字、图片、链接、小文件从电脑即时推送到手机，反之亦可。2.在电脑端接收查看android手机端的app通知。3.android端跟windows电脑端，一端复制内容后，另一端直接即时粘贴。（8.21新版本添加的实用功能）
<img src="/image/图/Pushbullet001.png" width="320" />
<center>▲ 第一次使用 Pushbullet 推送</center>

##应用场景
* **应用场景一：从电脑推送文字、图片、链接、文件到手机**

比如我们在电脑上有个地址想发到手机上，然后方便出门后随时查看。通过下面的方式就可以很快完成。如果你不是使用的Chrome或者Firefox浏览器，也可以通过安装Pushbullet的windows版本（mac osx以后会推出）来非常方便的实现这个需求。甚至可以将电脑中某个小文件右键直接发送到手机上。

还记得在北京面试工作的那段时间，我就常常会将电脑上收到的面试通知邮件中公司详细地址、乘车路线、联系电话等有用信息，用Pushbullet推送到手机上备用。（有时也用手机端邮件app，只是离线使用不是很方便）
![](/image/图/Pushbullet002.png)
<center>▲ 使用电脑端 Pushbullet 应用推送给手机</center>
![](/image/图/Pushbullet003.png)
<center>▲ 使用Chrome Pushbullet 插件推送给手机</center>
<div style="clear: both;">
<img src="/image/图/Pushbullet004.png" width="320" imageanchor="1" style="float:left;margin: 0 1em;"/>
<img src="/image/图/Pushbullet005.png" width="320" imageanchor="1" style="margin: 0 1em;"/>
</div>

![](/image/图/Pushbullet006.png)
<img src="/image/图/Pushbullet007.png" width="320" />


* **应用场景二：从手机推送文字、图片、链接、文件到电脑**

比如想讲手机上拍摄的一张照片保存到电脑上而手边刚好没有数据线，这时在手机端用用Pushbullet推送就能很好的解决这个需求。

在手机端选择一张图片推送之后，Pushbullet会先将图片上传到Amazon S3云存储服务器上，然后用浏览器在Pushbullet网页端下载下来就可以查看了。
<div style="clear: both;">
<img src="/image/图/Pushbullet008.png" width="320" imageanchor="1" style="float:left;margin: 0 1em;"/>
<img src="/image/图/Pushbullet009.png" width="320" imageanchor="1" style="margin: 0 1em;"/>
</div>
<img src="/image/图/Pushbullet010.png" width="320" />
![](/image/图/Pushbullet011.png)

* **应用场景三：从电脑端接收查看android手机端的app通知**
除了在设备之间推送指定的内容外，Pushbullet还可以在电脑上接收android手机收到的app、短信、电话等的通知。当我们在电脑前，手机开了静音或者不在手边，不用解锁手机也可以在电脑屏幕上看到手机的各类通知。
![](/image/图/Pushbullet012.png)
<center>▲ 手机端音乐切换的通知被显示在电脑上</center>

* **应用场景四：电脑端和手机端，一端复制内容后，另一端直接即时粘贴**
这是最近一次更新后添加的超级好用的功能。在新版的Pushbullet Android App 与 WIndows 软件之间，实现了复制、粘贴的跨设备即时推送同步，在电脑复制的內容，你可以立刻在手机上粘贴，反之亦可！让你感觉就好像是在同一台设备间操作一样，体验很棒。
<img src="/image/图/Pushbullet013.png" width="320" />
![](/image/图/Pushbullet014.png)
<center>▲ 手机端复制一段文本，电脑端立刻可以粘贴</center>

##安装使用
* 安裝 Windows 电脑版的Pushbullet：[Windows电脑版下载](https://update.pushbullet.com/pb_install.exe)，安装好之后用google账号登录后基本不需要额外设置即可以了。
* 安装 android 版的Pushbullet app：[Pushbullet Android 下载](https://play.google.com/store/apps/details?id=com.pushbullet.android)，第一次启动时根据app 向导打开是否允许通知同步的选项，然后在Pushbullet的设置 - 高级设置中，开启 Universal copy & paste 选项。

<div style="clear: both;">
<img src="/image/图/Pushbullet016.png" width="320" imageanchor="1" style="float:left;margin: 0 1em;"/>
<img src="/image/图/Pushbullet015.png" width="320" imageanchor="1" style="margin: 0 1em;"/>
</div>

* [Pushbullet ios 下载](https://itunes.apple.com/us/app/pushbullet/id810352052)
* [Pushbullet Chrome 下载](https://chrome.google.com/webstore/detail/pushbullet/chlffgpmiacpedhhbkiomidkjlcfhogd)
* [Pushbullet Firefox 下载](https://addons.mozilla.org/en-US/firefox/addon/pushbullet/)

*ps.因为GFW的存在，想要流畅并优雅的使用 Pushbullet，常常还得走VPN*