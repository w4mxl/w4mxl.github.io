---
title: （翻译）Flutter Release Preview 2 像素级别完美适配 iOS
categories: 
    - Tech
    - Flutter
date: 2018-09-21 10:27:43
permalink: flutter-release-preview-2-pixel-perfect
---

> 原文:  [Flutter Release Preview 2: Pixel-Perfect on iOS](https://developers.googleblog.com/2018/09/flutter-release-preview-2-pixel-perfect.html)
> Posted by the Flutter Team at Google

Flutter 是谷歌发布的新的移动应用开发工具包(`译者注: 2017.05.17 Google I/O 2017 - Flutter 首次公布，Alpha (v0.0.6) `)，用于快速在iOS和Android上制作漂亮的原生界面。今天，在上海谷歌开发者日的主题演讲中，我们宣布了**Flutter Release Preview 2**： Flutter 1.0 前的最后一个重要里程碑。

![Flutter Release Preview 2](https://i.loli.net/2019/07/29/5d3ec13ba989726993.png)

我们在今年2月份的[初始测试版本](https://medium.com/flutter-io/announcing-flutter-beta-1-build-beautiful-native-apps-dc142aea74c0)到今年夏天早些时候的[首个发布预览版](https://developers.googleblog.com/2018/06/flutter-release-preview-1-live-from.html)的可用性基础上,此版本继续完成核心方案和提高质量的工作。我们Flutter团队现在完全专注于完成我们的1.0版本。

<!-- more -->

## Release Preview 2中的新功能

此版本的主题是**完美适配iOS应用程序**。虽然我们为Flutter设计了高度品牌驱动的定制体验，但我们也听到了一些想要构建严格遵循[Apple界面指南](https://developer.apple.com/design/human-interface-guidelines/ios/overview/themes/)的应用程序的反馈。因此，在这个版本中，我们大大扩展了对Flutter中“Cupertino”主题控件的支持，其中[包含大量的小部件和类库](https://docs.flutter.io/flutter/cupertino/cupertino-library.html)，使得在构建iOS应用程序时比以往任何时候都更容易。

![使用Flutter构建的iOS设置页](https://s1.ax1x.com/2018/09/21/inwage.gif)

<center>[👆项目链接](https://github.com/xster/flutter-test/tree/master/t95_ios_settings_page)</center>  
   

以下是Flutter Release Preview 2中添加的一些新的iOS主题小部件：

- [CupertinoApp](https://docs.flutter.io/flutter/cupertino/CupertinoApp-class.html)：用于创建iOS样式应用程序的顶级窗口小部件;
- [CupertinoTimerPicker](https://docs.flutter.io/flutter/cupertino/CupertinoTimerPicker-class.html) 倒数计时选择器;
- [CupertinoSegmentedControl](https://docs.flutter.io/flutter/cupertino/CupertinoSegmentedControl-class.html) 用于水平分段控制;
- [CupertinoActionSheet](https://docs.flutter.io/flutter/cupertino/CupertinoActionSheet-class.html) 适用于iOS风格的底部弹出式表格。

还有更多更新：

- [CupertinoNavigationBar](https://docs.flutter.io/flutter/cupertino/CupertinoNavigationBar-class.html) 和 [CupertinoSliverNavigationBar](https://docs.flutter.io/flutter/cupertino/CupertinoSliverNavigationBar-class.html)
    - 在页面之间切换时平滑过渡。
    - 根据[CupertinoPageRoute.title](https://docs.flutter.io/flutter/cupertino/CupertinoPageRoute/title.html)自动填充标题和后退按钮标签。
- [CupertinoPageScaffold](https://docs.flutter.io/flutter/cupertino/CupertinoPageScaffold-class.html)
    - 键盘显示时插入内容。
- [CupertinoScrollbar](https://docs.flutter.io/flutter/cupertino/CupertinoScrollbar-class.html)
    - 在过度滚动期间提高视觉保真度。
- [CupertinoPicker](https://docs.flutter.io/flutter/cupertino/CupertinoPicker-class.html)
    - 添加了对无限滚动和循环滚动的支持。
    - 为轴外圆柱投影添加多列支持。

与以往一样，[Flutter 文档](https://docs.flutter.io/flutter/cupertino/cupertino-library.html)是获取有关`Cupertino*`类的详细信息的地方。（请注意，在撰写本文时，我们仍在努力将一些新的Cupertino小部件添加到[可视窗口小部件目录](https://flutter.io/widgets/cupertino/)中）。

我们也在完成其他方案方面取得了进展。看一下底层，我们添加支持以在后台执行Dart代码,即使在应用程序暂停时也毫无问题。插件作者可以利用此功能创建新的插件，在触发事件时执行代码，例如触发计时器或接收位置更新。有关更详细的介绍，请阅读此[文章](https://medium.com/flutter-io/executing-dart-in-the-background-with-flutter-plugins-and-geofencing-2b3e40a1a124)，该文章演示了如何使用后台执行来创建地理围栏插件。

另一项改进是在Android和iOS上[我们的应用程序包大小减少了高达30％](https://github.com/flutter/flutter/issues/16833#issuecomment-410103493)。我们在Android上的[最小Flutter应用程序](https://github.com/flutter/flutter/tree/60d223c20c44424e3c8031d019270d22bab35df6/examples/hello_world)正式打包出来的大小仅为4.7MB，比我们开始优化前小少了2MB - 我们将继续努力,找出进一步的潜在优化的可能性。（请注意，虽然这些改进对iOS和Android都适用，但[由于iOS软件包的构建方式](https://github.com/flutter/flutter/issues/16833#issuecomment-410103493)，您可能会在iOS上看到不同的结果）。

<iframe width="594" height="315" src="//player.bilibili.com/player.html?aid=32140785&cid=56229899&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen> </iframe>

## 增长势头

随着许多新开发人员陆续发现和关注Flutter，我们注意到Flutter现在是GitHub上50大活跃库之一：

![](https://i.loli.net/2019/07/29/5d3ec1999ec7b37699.png)

我们今年在Google I / O上宣布Flutter“准备就绪”; 随着Flutter越来越接近稳定的1.0版本，许多新的Flutter应用程序正在发布，已经有数千个基于Flutter的应用程序出现在Apple和Google Play商店中。其中包括一些使用最广泛的应用程序，如阿里（[Android](https://play.google.com/store/apps/details?id=com.taobao.idlefish)，[iOS](https://itunes.apple.com/cn/app/%E9%97%B2%E9%B1%BC-%E6%8C%82%E9%97%B2%E9%B1%BC-%E9%97%B2%E7%BD%AE%E8%83%BD%E6%8D%A2%E9%92%B1/id510909506?mt=8)），腾讯现在（[Android](https://play.google.com/store/apps/details?id=com.tencent.now)，[iOS](https://itunes.apple.com/us/app/%E8%85%BE%E8%AE%AFnow%E7%9B%B4%E6%92%AD-%E8%BF%99%E6%98%AF%E6%88%91%E7%9A%84%E6%97%B6%E5%88%BB/id1097492828?mt=8)）和谷歌广告（[Android](https://play.google.com/store/apps/details?id=com.google.android.apps.adwords)，[iOS](https://itunes.apple.com/us/app/google-ads/id1037457231?mt=8)）。这是一段关于阿里巴巴如何使用Flutter构建他们的闲鱼应用程序（Android，iOS）的视频，目前中国有超过5000万客户使用它：

<iframe width="594" height="315" src="//player.bilibili.com/player.html?aid=32140486&cid=56229199&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen> </iframe>

我们十分重视客户满意度并定期对我们的用户进行调查。我们承诺与社区分享调查结果，我们[最近的一次调查](https://medium.com/flutter-io/what-weve-learned-from-the-july-2018-flutter-user-survey-cbbf1e04370c)显示，92％的开发者对Flutter感到满意或非常满意，并会向其他人推荐Flutter。在快速开发和漂亮的用户界面方面，79％的受访者认为Flutter在提高开发效率和实现理想UI方面非常有帮助或有帮助。82％的Flutter开发人员对[Dart编程语言](https://medium.com/dartlang/dart-2-stable-and-the-dart-web-platform-3775d5f8eac7)感到满意或非常满意，Dart编程语言最近也迎来了一个新的里程碑:Dart 2的发布。

Flutter强大的社区增长也可以通过其他方式感受到。在[StackOverflow](https://stackoverflow.com/questions/tagged/flutter)上，我们看到对Flutter的兴趣日益增长，发布，回答和查看了许多新问题，如下图所示：

<center>![随着时间的推移用四个流行的UI框架中的每一个标记的StackOverflow问题视图的数量](https://i.loli.net/2019/07/29/5d3ec1c77082394551.png)
</center>

Flutter[从第一天开始](https://github.com/flutter/engine/commit/20cc569f5961d4e896cb2f4651fd2049066bd47c)就是开源的。这是我们的设计初衷,我们的目标是用户能透明地了解我们的进展，并鼓励那些希望在所有平台上看到美好的用户体验的个人和公司为Flutter项目贡献一份力。

## 入门

你可能想问如何[升级](https://flutter.io/upgrading/)到Flutter Release Preview 2？如果你已经在用beta版本，它只需要一个命令：`flutter upgrade`

您可以通过`flutter --version`从命令行运行来检查是否已安装Release Preview 2 。如果您使用的是0.8.2或更高版本，那么您将拥有本文中描述的所有内容。

如果你尚未尝试Flutter，现在是你开始的最佳时间，并且[flutter.io](https://flutter.io/get-started/install/)拥有下载Flutter的所有细节，并开始开发您的第一个应用程序。

当你准备好了，Flutter有一整套生态系统的示例应用程序和代码片段可以帮助你开始。您可以在GitHub上的[flutter/samples](flutter/samples) repo中找到Flutter团队的样本，包括如何使用Material和Cupertino，反序列化以JSON编码的数据等方法。还有一个[精心策划的示例清单](https://github.com/flutter/samples/blob/master/INDEX.md)，链接到Flutter社区创建的一些最佳示例。

您还可以通过我们的[动手视频](https://www.youtube.com/playlist?list=PLOU2XLYxmsIJ7dsVN4iRuA7BT8XHzGtCr)，[新闻通讯](https://flutterweekly.net/)，[社区文章](https://medium.com/flutter-community)和[开发者show](https://www.youtube.com/watch?v=yr8F2S3Amas)来了解Flutter的最新信息。在您构建应用程序时，您可以使用[讨论组](https://groups.google.com/forum/#!forum/flutter-dev)，[聊天室](https://gitter.im/flutter/flutter)，[社区支持](https://stackoverflow.com/questions/tagged/flutter)和[每周在线视频群](https://medium.com/flutter-community/humpdayqanda-live-help-for-flutter-00-00-23-59-utc-every-single-wednesday-5864fb417838)来帮助您。Release Preview 2是我们的上一次发布预览版。下一站：1.0！
　　
　　
-------

　　
**译者注: 这是我第一次将自己平时阅读一些英文文章时的翻译放出来,有很多地方翻译的还很粗糙,整体翻译水平离“信达雅”还很遥远,不过相信我会不断进步我的翻译水平的。**
　　
另外,我对这篇文章的主要观点进行总结如下:
1. Flutter 进入到 RP 2 阶段,正式发布1.0版本指日可待
2. Flutter RP2主要更新有下面3点:
     *     为iOS app开发做了更好的适配:Pixel-Perfect
     *     支持后台执行dart代码,甚至app退到后台也可以
     *     安装包大小对比之前减小30%
1. Flutter 发展势头特别好
2. Flutter 入门容易,文档健全