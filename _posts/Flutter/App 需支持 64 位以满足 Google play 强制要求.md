---
title: App 需支持 64 位以满足 Google play 强制要求
date: 2019-07-10 16:59:50
categories: Flutter
permalink: provide-64-bit-for-google-play
---

## Google play 推进 64位应用
![111562745745_.pi](/image/111562745745_.pic.jpg)

从今年1月份开始，Google 就陆续通过邮件等方式发通知，鼓励 Android 开发者尽快将已经上传到 Google play 的 app 对 64 位做兼容处理。并告知开发者，在今年 8 月 1 日开始，将强制要求新上架的 App 或老应用更新，除了提供 32 位的版本之外，还必须要提供 64 位的版本。

![141562750828_.pi](/image/141562750828_.pic.jpg)

今年 5 月份，我上传了一款用 Flutter 开发的 App（**[V2LF](https://play.google.com/store/apps/details?id=io.github.w4mxl.v2lf)**）到Google play 上，那时候打包出来的 APK 大小是 9.1 MB，默认只有 armeabi-v7a 一种 CPU 架构。后来陆续有收到通知邮件，提示我再提供一个 64 位的版本。

![121562749707_.pi](/image/121562749707_.pic.jpg)

## Flutter stable 1.7 支持了 Android app bundles 和 64-bit Android apps

今天上午看到 Flutter 官方在 medium 上新发布的一篇文章：[Announcing Flutter 1.7](https://medium.com/flutter/announcing-flutter-1-7-9cab4f34eacf)。

![flutter1.7](/image/flutter1.7.png)

文章在 “Support for Android app bundles and 64-bit Android apps” 一节中也有提到关于 8 月 1 号 Google play 的强制包含 64 位版本的要求，并说这次发布的 Flutter 1.7 的 SDK， Android App Bundles 也已经支持单独创建 32 位和 64 位的包了。

如果还是使用原先的命令 `flutter build apk` 来打包 APK，Android studio 会给出下面的提示，告知这种方式会将 android-arm 和 android-arm64 两种CPU架构都打包到一个apk中，app打包出来的apk会是一个 **“fat APK”**。
![151562812574_.pic_hd](/image/151562812574_.pic_hd.jpg)

![131562749760_.pi](/image/131562749760_.pic.jpg)

也会给出提示告知，如果打包是为了上传到 Google play 上的，建议使用 app bundles 的方式或者对不同架构 CPU 分别打包。提示原文如下：

To generate an app bundle, run:

```
flutter build appbundle --target-platform android-arm,android-arm64
```
Learn more on: [https://developer.android.com/guide/app-bundle](https://developer.android.com/guide/app-bundle)

To split the APKs per ABI, run:

```
flutter build apk --target-platform android-arm,android-arm64 --split-per-abi
```
[https://developer.android.com/studio/build/configure-apk-splits#configure-abi-split](https://developer.android.com/studio/build/configure-apk-splits#configure-abi-split)



## 相关链接

* [https://github.com/flutter/flutter/issues/31922#issuecomment-490185953](https://github.com/flutter/flutter/issues/31922#issuecomment-490185953)
* [https://github.com/flutter/flutter/issues/18494#issuecomment-489807239](https://github.com/flutter/flutter/issues/18494#issuecomment-489807239)
* [让您的应用做好准备，以符合 64 位要求](https://juejin.im/post/5c467c28e51d455243768284)
* [8月不支持 64 位，App 将无法上架 Google Play！需要怎么做？](https://juejin.im/post/5cff1843e51d4510774a8844)