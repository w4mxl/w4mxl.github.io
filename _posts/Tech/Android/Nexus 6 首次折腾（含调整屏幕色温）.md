---
title: Nexus 6 首次折腾（含调整屏幕色温）
date: 2016-01-21 15:12
categories: 
    - Tech
    - Android
permalink: my-struggle-of-nexus6
---


15年的黑五( 2015.11.27)，在美国亚马逊海淘了一台 Nexus 6，当时看到促销价 $ 199.99 心里乐滋滋的，终于不会想到后来竟还有55刀的转运费，更有被税后需补缴18.5刀税。此机到手价实为：199.99＋55＋18.5 ＝ 273.49 刀，转成人民币大约是 ¥1800。不过这价格能买到亲儿子我已经很满意。

 翘首以待了一个多月，在2016.01.18终于摸到真机。期间此货也算「开心的」在路上垮了个年。拆箱开机，屏幕上的保护膜明显很多气泡，更重要的是那屏幕暖的啊 =_=||，实在接受不能，于是开始搞屏幕色温。

一番谷歌之后收获了两种解决方案：
- 刷带屏幕色温调节功能的第三方ROM，如CM
- 刷能调节屏幕色温的内核

最终我的搞法是刷[Chroma ROM](http://forum.xda-developers.com/nexus-6/development/rom-chroma-01-11-2015-t3000003)(一个基于AOSP的第三方ROM)，然后再刷[Franco Kernel](http://forum.xda-developers.com/nexus-6/orig-development/kernel-franco-kernel-r1-t2987173)(可以调节屏幕色温的内核)。
我的大致流程是：([这里有更详细的](http://forum.xda-developers.com/nexus-6/general/how-to-nexus-6-one-beginners-guide-t2948481))
1. Unlock The Bootloader
2. Install TWRP recovery
3. Flash CHROMA ROM (include SuperSU )
4. Flash Franco Kernel
5. Install [KCAL app](http://downloads.codefi.re/savoca/kcal)

我的KCAL配置(参考xda上):
```JAVA
R · 230
G · 222
B · 253
Sat · 40
Val · 135
Con · 120
```
