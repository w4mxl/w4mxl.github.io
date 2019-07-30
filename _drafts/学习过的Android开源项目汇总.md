---
title: 学习过的Android开源项目汇总
date: 2015/08/30 17:36:00
categories: 
    - Tech
    - Android
---

利用周末整理下之前工作中、学习中使用过的 Android 开源项目，通过整理好之后，能每周抽出些时间去对这些开源项目的源码进行解析，以期通过这种方式能更深层次的学习这些优秀的 Android 开源项目。

**View 篇**
- Android-ConvenientBanner
项目描述:通用的广告栏控件，让你轻松实现广告头效果。支持无限循环，可以设置自动翻页和时间(而且非常智能，手指触碰则暂停翻页，离开自动开始翻页。你也可以设置在界面onPause的时候不进行自动翻页，onResume之后继续自动翻页)，并且提供多种翻页特效。 对比其他广告栏控件，大多都需要对源码进行改动才能加载网络图片，或者帮你集成不是你所需要的图片缓存库。而这个库能让有代码洁癖的你欢喜，不需要对库源码进行修改你就可以使用任何你喜欢的网络图片库进行配合。
项目地址:[https://github.com/saiwu-bigkoo/Android-ConvenientBanner](https://github.com/saiwu-bigkoo/Android-ConvenientBanner)
项目效果:  
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkt6q7j62g20bd0hykjq.gif)

- Android ViewPagerIndicator
项目描述: 配合 ViewPager 使用的 Indicator，支持各种位置和样式
项目地址: [https://github.com/JakeWharton/ViewPagerIndicator](https://github.com/JakeWharton/ViewPagerIndicator)
项目效果:   
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkurq6dl3j20no0gok0a.jpg)  

- MVCHelper
项目描述: 实现下拉刷新，滚动底部自动加载更多，分页加载，自动切换显示网络失败布局，暂无数据布局，支持任意view，支持切换主流下拉刷新框架，真正的android MVC架构,refresh,loadmore
项目地址: [https://github.com/LuckyJayce/MVCHelper](https://github.com/LuckyJayce/MVCHelper)
demo地址: [Demo APK](https://github.com/LuckyJayce/MVCHelper/blob/master/raw/MVCHelper_Demo.apk?raw=true)

- EmojiChat
项目描述: 一个聊天界面，包括从网络下载大表情并使用，图片发送，文字发送，Emoji表情发送，自定义表情键盘，Emoji表情键盘，仿QQ功能键盘等等……
项目地址: [https://github.com/kymjs/EmojiChat](https://github.com/kymjs/EmojiChat)
项目效果:  
![](http://ww1.sinaimg.cn/mw690/62ed8609jw1evkv3kl160j205k09wq43.jpg)

- Emojicon
项目描述: Emojicon 是一个用于在 TextView, EditText (like WhatsApp) 显示 emoji 表情的开源库。
项目地址: [https://github.com/rockerhieu/emojicon](https://github.com/rockerhieu/emojicon)
项目效果:  
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkvbd2w7lj20b00ibjss.jpg)  

- Material
项目描述: MaterialLibrary is an Open Source Android library that back-port Material Design components to pre-Lolipop Android.
项目地址: [https://github.com/rey5137/material](https://github.com/rey5137/material)
demo地址: [https://play.google.com/store/apps/details?id=com.rey.material.demo](https://play.google.com/store/apps/details?id=com.rey.material.demo)

- SwipeMenuListView
项目描述: A swipe menu for ListView.
项目地址: [https://github.com/baoyongzhang/SwipeMenuListView](https://github.com/baoyongzhang/SwipeMenuListView)
项目效果:  
![](http://ww3.sinaimg.cn/mw690/62ed8609jw1evkvipk41sg20ar0i146f.gif)

- PhotoCrop
项目描述: A Library which can be used to crop images in Android similar to Facebook and Telegram
项目地址: [https://github.com/albinmathew/PhotoCrop](https://github.com/albinmathew/PhotoCrop)
项目效果:  
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkwzqlb3oj20a00hsdjw.jpg)

- RoundedImageView
项目描述: A fast ImageView (and Drawable) that supports rounded corners (and ovals or circles) based on the original [example from Romain Guy](http://www.curious-creature.org/2012/12/11/android-recipe-1-image-with-rounded-corners/). RoundedImageView is a full superset of [CircleImageView](https://github.com/hdodenhof/CircleImageView) (which is actually just a subset based on this lib) with many more advanced features like support for ovals, rounded rectangles, ScaleTypes and TileModes.
项目地址: [https://github.com/vinc3m1/RoundedImageView](https://github.com/vinc3m1/RoundedImageView)
项目效果:  
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkxf8ngpoj208c0etn2e.jpg)
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkxf7h5m4j208c0etq81.jpg)

- CircleImageView
项目描述: A fast circular ImageView perfect for profile images. This is based on [RoundedImageView from Vince Mi](https://github.com/vinc3m1/RoundedImageView) which itself is based [on techniques recommended by Romain Guy](http://www.curious-creature.org/2012/12/11/android-recipe-1-image-with-rounded-corners/).
项目地址: [https://github.com/hdodenhof/CircleImageView](https://github.com/hdodenhof/CircleImageView)
项目效果:  
![](http://ww2.sinaimg.cn/mw690/62ed8609jw1evkxjr8znvj20f00qotat.jpg)  

- ASimpleCache 
项目描述: ASimpleCache 是一个为android制定的 轻量级的 开源缓存框架。轻量到只有一个java文件（由十几个类精简而来）。 
项目地址: [https://github.com/yangfuhai/ASimpleCache](https://github.com/yangfuhai/ASimpleCache)

- Logger 
项目描述: Simple, pretty and powerful logger for android
项目地址: [https://github.com/orhanobut/logger](https://github.com/orhanobut/logger)
项目效果:  
![](http://ww2.sinaimg.cn/mw690/62ed8609jw1evkxpqa492j20uk0smafu.jpg)

- LeakCanary
项目描述: Android 和 Java 内存泄露检测。
项目地址: [https://github.com/square/leakcanary](https://github.com/square/leakcanary)
项目demo: [https://github.com/liaohuqiu/leakcanary-demo](https://github.com/liaohuqiu/leakcanary-demo)
项目效果:  
![](http://ww2.sinaimg.cn/mw690/62ed8609jw1evkynk1l3ij20jg0a4ac1.jpg)

- Android ViewBadger
项目描述: A simple way to "badge" any given Android view at runtime without having to cater for it in layout.
项目地址: [https://github.com/jgilfelt/android-viewbadger](https://github.com/jgilfelt/android-viewbadger)
项目效果:   
![](http://ww4.sinaimg.cn/mw690/62ed8609jw1evkyrta511j20a00h476e.jpg)

- pinned-section-listview
项目描述: Easy to use ListView with pinned sections for Android 2.1 and higher. Pinned section is a header view which sticks to the top of the list until at least one item of that section is visible.
项目地址: [https://github.com/beworker/pinned-section-listview](https://github.com/beworker/pinned-section-listview)
项目效果:  
![](http://ww2.sinaimg.cn/mw690/62ed8609jw1evkyvpsit5j20660abaae.jpg)

- Dynamicbox
项目描述: DynamicBox is a library which inflates custom layouts to indicate :loading content、show an exception or even a custom view.
项目地址:  [https://github.com/medyo/dynamicbox](https://github.com/medyo/dynamicbox)

- Sweet Alert Dialog
项目描述: Android版的SweetAlert，清新文艺，快意灵动的甜心弹框
项目地址: [https://github.com/pedant/sweet-alert-dialog](https://github.com/pedant/sweet-alert-dialog)
项目效果:  
![](http://ww2.sinaimg.cn/mw690/62ed8609jw1evkze1hmwig20al0h5age.gif)

( 未完... )