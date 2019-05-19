---
title: 使用Intl包让Flutter app支持多语言
categories: Flutter
date: 2019-1-26 11:16
permalink: flutter-Intl-Localizations
---

# 步骤

1. 在项目根目录下创建一个i10n-arb目录，该目录用于保存arb文件
2. 在lib目录下创建一个i10n的目录，该目录用于保存从arb文件生成的dart代码文件。
3. 在i10n目录下面，创建一个localization_intl.dart 文件，用来实现Localizations和Delegate类
4. 在localization_intl.dart 文件中添加需要国际化的属性
5. `flutter packages pub run intl_translation:extract_to_arb --output-dir=i10n-arb lib/i10n/localization_intl.dart` 通过这个intl_translation命令把项目中Intl API标识的属性和字符串生成arb文件
6. 基于上面生成的arb文件，创建其它我们想支持的语言对应的arb文件
7. `flutter packages pub run intl_translation:generate_from_arb --output-dir=lib/i10n --no-use-deferred-loading lib/i10n/localization_intl.dart i10n-arb/intl_*.arb`  根据arb生成dart文件

<!-- more -->

# 说明

官方的教程中第五步和第七步有用到两个命令：

`flutter packages pub run intl_translation:extract_to_arb --output-dir=i10n-arb lib/i10n/localization_intl.dart`

<image src="https://ws3.sinaimg.cn/large/006tNc79gy1fzjtjsxczgj30rw05w3ys.jpg" width="200"/>

``` json
{
  "@@last_modified": "2019-01-26T11:14:10.582986",
  "login": "Login",
  "@login": {
    "description": "Title for left drawer login text",
    "type": "text",
    "placeholders": {}
  }
}
```

这个是生成的默认的Locale资源文件，如果我们现在要支持中文简体，只需要在该文件同级目录创建一个"intl_zh_Hans.arb"文件。

<image src="https://ws2.sinaimg.cn/large/006tNc79gy1fzjukxbm55j30pg08gjrv.jpg" width="200"/>

然后将"intl_messages.arb"的内容拷贝到"intl_zh_Hans.arb"文件，接下来将英文翻译为中文即可，翻译后的"intl_zh_Hans.arb"文件内容如下：

``` json
{
  "@@last_modified": "2019-01-26T11:27:30.905630",
  "@@locale":"zh-Hans",
  "login": "登录",
  "@login": {
    "description": "Title for left drawer login text",
    "type": "text",
    "placeholders": {}
  }
}
```

-------

`flutter pub pub run intl_translation:generate_from_arb --output-dir=lib/i10n --no-use-deferred-loading lib/i10n/localization_intl.dart i10n-arb/intl_*.arb`

<image src="https://ws4.sinaimg.cn/large/006tNc79gy1fzjunwho55j30gk0gejsl.jpg" width="300" />


# 感受

经过学习实践官方的国际化方案后，我觉得相对还是有点复杂了。需要dart转arb，arb再转一次dart。对于没有开发过原生app的新手来说，也不是很直观的理解其中的逻辑。

基于上面原因，我目前发现了一些其它方案，

* 基于 Flutter i18n IDE插件，按照插件提供的文档去实现国际化。
    * 这样步骤和逻辑都相对简单些。这个插件也是基于官方的教程逻辑实现的，只是将一些步骤通过插件替代了，主要的作用是省略dart转arb这步。
* 基于 [fluintl](https://github.com/Sky24n/fluintl) 库实现
    

# 参考链接

* [Flutter 国际化 （官方英文）](https://flutter.io/docs/development/accessibility-and-localization/internationalization)
* [Flutter 国际化 （中文，基于官方英文翻译）](https://book.flutterchina.club/chapter12/)
* [讓 Flutter App 支援多國語系的開發流程](https://medium.com/@zonble/%E8%AE%93-flutter-app-%E6%94%AF%E6%8F%B4%E5%A4%9A%E5%9C%8B%E8%AA%9E%E7%B3%BB%E7%9A%84%E9%96%8B%E7%99%BC%E6%B5%81%E7%A8%8B-ceb31532e2e1)
* [Flutter i18n](https://github.com/long1eu/flutter_i18n)