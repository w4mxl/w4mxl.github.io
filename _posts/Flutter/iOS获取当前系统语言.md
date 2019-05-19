---
title: iOS上获取当前系统语言
categories: Flutter
date: 2019-1-25 15:23
permalink: ios-system-language
---

# 测试代码

``` ObjectiveC
    NSString *identifier = [[NSLocale currentLocale] localeIdentifier];
    NSString *displayName = [[NSLocale currentLocale] displayNameForKey:NSLocaleIdentifier value:identifier];
    
    NSString *udfLanguageCode = [[NSUserDefaults standardUserDefaults] objectForKey:@"AppleLanguages"][0];
    NSString *pfLanguageCode = [NSLocale preferredLanguages][0];
    NSString *localeLanguageCode = [[NSLocale currentLocale] objectForKey:NSLocaleLanguageCode];
    NSString *language =  [[NSBundle mainBundle] preferredLocalizations][0];
    
    NSLog(@"%@", identifier);
    NSLog(@"%@", displayName);
    
    NSLog(@"%@", [[NSUserDefaults standardUserDefaults] objectForKey:@"AppleLanguages"]);
    NSLog(@"%@", udfLanguageCode);
    
    NSLog(@"%@",[NSLocale preferredLanguages]);
    NSLog(@"%@", pfLanguageCode);
    NSLog(@"%@", localeLanguageCode);
    NSLog(@"%@", language);
```

<!-- more -->

# 系统设置 & 打印信息 (模拟器和真机情况一致)


<image src="https://ws2.sinaimg.cn/large/006tNc79gy1fzivcjdcaqj30n01ds42e.jpg" width="300" /> 

```
2019-01-25 15:20:35.580212+0800 TestLanguage[22878:188985] en_JP
2019-01-25 15:20:35.580373+0800 TestLanguage[22878:188985] 英文（日本）
2019-01-25 15:20:35.580545+0800 TestLanguage[22878:188985] (
    "zh-Hant-HK",
    "zh-Hant-TW",
    "zh-Hans-JP",
    "ja-JP",
    "en-JP"
)
2019-01-25 15:20:35.580653+0800 TestLanguage[22878:188985] zh-Hant-HK
2019-01-25 15:20:35.580870+0800 TestLanguage[22878:188985] (
    "zh-Hant-HK",
    "zh-Hant-TW",
    "zh-Hans-JP",
    "ja-JP",
    "en-JP"
)
2019-01-25 15:20:35.580977+0800 TestLanguage[22878:188985] zh-Hant-HK
2019-01-25 15:20:35.581092+0800 TestLanguage[22878:188985] en
2019-01-25 15:20:35.581192+0800 TestLanguage[22878:188985] en
```


-------

<image src="https://ws3.sinaimg.cn/large/006tNc79gy1fzivqut9zsj30n01dsadz.jpg" width="300"/>
```
2019-01-25 15:44:23.640336+0800 TestLanguage[30886:254351] en_CN
2019-01-25 15:44:23.640494+0800 TestLanguage[30886:254351] 英文（中國）
2019-01-25 15:44:23.640613+0800 TestLanguage[30886:254351] (
    "zh-Hant-HK",
    "zh-Hant-TW",
    "zh-Hans-CN",
    "ja-CN",
    "en-CN"
)
2019-01-25 15:44:23.640701+0800 TestLanguage[30886:254351] zh-Hant-HK
2019-01-25 15:44:23.640848+0800 TestLanguage[30886:254351] (
    "zh-Hant-HK",
    "zh-Hant-TW",
    "zh-Hans-CN",
    "ja-CN",
    "en-CN"
)
2019-01-25 15:44:23.640921+0800 TestLanguage[30886:254351] zh-Hant-HK
2019-01-25 15:44:23.640999+0800 TestLanguage[30886:254351] en
2019-01-25 15:44:23.641082+0800 TestLanguage[30886:254351] en

```