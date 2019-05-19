---
title: Volley study
date: 2015-05-31 21:59
categories: Android
permalink: Volley-study
---

Volley 是 Android 开发中跟网络操作相关的一个开源库，这个库的官方介绍是：

>Volley is a library that makes networking for Android apps
easier and most importantly, faster.

Android 几乎所有项目在开发中都会涉及到网络操作（基于 HTTP 协议发送和接收网络数据）。系统提供的通信方式有两种: HttpURLConnection 、HttpClient 。关于HttpURLConnection及HttpClient对比可见： [Android’s HTTP Clients](http://android-developers.blogspot.com/2011/09/androids-http-clients.html)

Android 网络通信相关的框架（开源库）有:
有轻量的[android-async-http](http://loopj.com/android-async-http/)
Universal-Image-Loader
谷歌官方的[volley](https://android.googlesource.com/platform/frameworks/volley/)。集合了前面两个的优点。
Square提供的[Retrofit](http://square.github.io/retrofit/)
基于Volley实现的http [Netroid](https://github.com/vince-styling/Netroid)

Volley 的使用可以简述为三步:
1.建一个请求队列对象
2.建一个请求对象 StringRuester、JsonRequest -> JsonObjectRequest 和 JsonArrayRequest、ImageRequest
3.将请求对象add到请求队列中

至于项目中volley的具体使用方法我就不在这里分步骤贴代码了。我推荐下面两个github开源实例，囊括了volley大部分使用方法，fork后仔细看代码学习下，就很好在自己的项目中上手volley了。
[ogrebgr/android_volley_examples](https://github.com/ogrebgr/android_volley_examples)
[smanikandan14/Volley-demo](https://github.com/smanikandan14/Volley-demo)

>计划

我在之前项目使用volley的过程中，遇到过一些坑还有就是为了满足实际需求对volley库进行了增强，我后续会陆续整理添加到这篇博客中...