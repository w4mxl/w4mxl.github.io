---
title: Android Studio中新建一个文件时插入作者、日期
date: 2014-11-21 01:04:12
categories: Android
tag: Android Studio
permalink: insert-author-and-date-in-android-studio-new-file
---

### 需求描述：

在使用android studio过程中，想在新创建的文件（activity、service...）头部添加上author、date信息。
　　
### 解决过程：

<img src="/image/图/Android Studio中新建一个文件（Activity...）时插入作者、日期01.png" width="700" />

我先是按照之前使用eclipse对这个需求的配置方法，这个方法是通过配置Eclipse－Preferences－Java-Code Templates里Comments模板来实现，如果可行的话会在每次创建完新的文件后自动在文件头插入配置上的信息。但是折腾完发现在这里行不通。

之后就想到把想配置的这个模板做成一个快捷键，当新建完一个文件后，在文件的头部通过快捷键的方式插入前面配置好的信息。测试后发现可以行的通。

<img src="/image/图/Android Studio中新建一个文件（Activity...）时插入作者、日期02.png" width="700" />


<img src="/image/图/Android Studio中新建一个文件（Activity...）时插入作者、日期03.png" width="600" />
<img src="/image/图/Android Studio中新建一个文件（Activity...）时插入作者、日期04.png" width="600" />