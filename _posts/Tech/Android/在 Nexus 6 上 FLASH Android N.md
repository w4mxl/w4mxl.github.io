---
title: "在 Nexus 6 上 FLASH Android N"
date: 2016-03-10 11:07:24
categories: 
    - Tech
    - Android
permalink: flash-N-to-nexus6
---
今天 Google 较之往年提前2个月发布了 Android N 的开发者预览版，按耐不住，折腾起来。

<!-- more -->

同时 [Android Beta Program](https://www.google.com/android/beta) 也被发布。通过注册这个预览体验项目来获取 Android N 。后续还可以通过 OTA 的方式来获取更新，再也不必像过去必须通过刷机的方式来获得了。在此之前，开发者想要安装预览版，必须要解锁 OEM 和 bootloader ，然后再刷入镜像。

可是当我 enrolled 我的 Nexus 6(在用的固件是 Pure Nexus) 手机后，等了好一会并没有收到推送！索性还是换我之前比较熟悉的刷固件的方式！

## 下载固件

之前 Nexus 6 正式版的固件下载地方是[这里](https://developers.google.com/android/nexus/images#shamu)。不过这次发布的预览版的固件是在[这里](https://dl.google.com/dl/android/aosp/shamu-mmb29v-factory-0b4a53f0.tgz)。

## 开始刷机

**`惯例，刷机前先备份好手机上个人重要数据！！！！`**

起初我按照原来刷正式包的过程刷的：  
1. adb reboot bootloader  
2. Execute the `flash-all` script  

报错了！

```
archive does not contain 'boot.sig'
archive does not contain 'recovery.sig'
...
```

后面在 XDA 论坛找到了针对此预览版固件正确的输入步骤：  

```
Boot into TWRP to wipe cache, dalvik, data (not internal storage/SD) and system. 

Reboot to bootloader and flash the following:
   fastboot flash bootloader <insert bootloader img name>
   fastboot reboot-bootloader
   
   fastboot flash radio <insert radio img name>
   fastboot reboot-bootloader
   
   fastboot flash system system.img
   fastboot flash vendor vendor.img
   fastboot flash boot boot.img // OR // fastboot flash boot <insert name of unecrypt boot.img>
   fastboot flash cache cache.img
   fastboot reboot
```  

最后是随手拍的几张图：

<center><img src="https://i.loli.net/2019/07/29/5d3e6aeb1888562687.png" width="280"/> <img src='https://i.loli.net/2019/07/29/5d3e6b22c6beb59558.png' width="280"/>

<img src='https://i.loli.net/2019/07/29/5d3e6b629daf987850.png' width="280"/> <img src='https://i.loli.net/2019/07/29/5d3e6b7c6ea5e57120.png' width="280"/></center>

