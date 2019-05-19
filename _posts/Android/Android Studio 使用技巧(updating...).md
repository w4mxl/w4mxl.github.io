---
title: Android Studio 使用技巧(updating...)
date: 2015-04-17 00:00
categories: Android
tags: Android Studio
permalink: tips-of-Android-Studio
---

Android Studio,从13年Google I/O发布后（还记得那时候翻墙在YouTube上看Google产品经理I/0现场演示Android Studio新特性，那黑色的theme[Darcula]，好酷），和它一路从早期开发者预览版、beta版、稳定版走来。开始很不稳定，每次一更新不出意外总遇到问题，然后只好不断通过google来填坑，再后来随着一版版更新，坑也填的差不多了，稳定版就发布了（2014/12/08），用起来也越来越顺手，说起来满满的都是爱。

下面是我使用Android Studio过程中累计到一些技巧(工具)，希望通过这篇博客分享出来，如果你有其他关于Android Studio的使用上的技巧，也特别希望你能分享给我。

#### 下面提到的工具安装方法
1. Android Studio:  `Preferences → Plugins → Browse repositories` 搜索工具的名字
2. 去工具的开源地址下载工具打好的zip包: `Preferences → Plugins → Install plugin from disk`

* 设置鼠标移到变量、方法、类等上弹出说明框。[在Settings(windows)或者Preferences(OSX)里搜索“show quick doc”]。如果你想只是在需要的时候查看，而它不想总是弹出，可以不设置上面的，通过快捷键 control + J(或者F1)调出。

![](/image/as_tip_show_quick_doc.png)

![](/image/as_tip_show_quick_doc_simple.png)

* [Android Code Generator Plugin](http://tmorcinek.github.io/android-codegenerator-plugin-intellij/)。这个插件可以根据xml文件内容自动生成对应的java code，可生成的包括activity、fragment、adapter、menu等，具体使用可点进网站查看GIF动画演示。

![](/image/Android Code Generator Plugin.png)

![](/image/generate_activity.gif)

* [Android Parcelable code generator](https://github.com/mcharmas/android-parcelable-intellij-plugin)。插件在github上的说明是：This tool generates an Android Parcelable implementation based on fields in the class.

![](/image/Android Parcelable code generator.png)

![](/image/Android Parcelable code generator_simple.png)

* [GsonFormat](https://github.com/zzz40500/GsonFormat)。这是一个根据JSONObject格式的字符串,自动生成实体类参数的插件。实在是很方便好用。

![](/image/GsonFormat.png)

![](/image/GsonFormat_simple.gif)
---
`更新: 2015/6/11`
* [ButterKnife Zelezny](https://github.com/avast/android-butterknife-zelezny)。`Android Studio plugin for generating ButterKnife injections from selected layout XML.`

![](http://ww3.sinaimg.cn/mw690/62ed8609gw1et09ls3nl5g20js0gfq8q.gif)