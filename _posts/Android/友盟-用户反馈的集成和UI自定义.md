---
date: 2015-06-28 19:58
categories: Android
tags: 友盟
title: 友盟-"用户反馈"的集成和UI自定义
---

### 1. 对比
<img src="http://ww4.sinaimg.cn/mw690/62ed8609jw1etk3hqcje6j20lc0zkq5i.jpg" width="250" />
> 注: 友盟用户反馈SDK中默认的用户反馈页，功能大而全(联系方式可以选择电话、QQ、邮箱;用户可以用发送语音反馈;可发图片;回复后推送消息给用户...)，可这设计实在是丑到没朋友，且友盟集成的方式很难在原基础上对UI进行自定义...

<img src="http://ww3.sinaimg.cn/mw690/62ed8609jw1etk2r6ohbrj20lc0zktah.jpg" width="250" />  <img src="http://ww2.sinaimg.cn/mw690/62ed8609jw1etk2r62351j20lc0zkaav.jpg" width="250" /> 
> 注: app中"用户反馈"功能常见的页面是长这个样子的: 图1 截自大众点评   图2 截自豆瓣FM

<img src="http://ww4.sinaimg.cn/mw690/62ed8609jw1etk2r5d49oj20lc0zk0uz.jpg" width="250" />
> **注: "联系方式 (EditText) ＋ 反馈内容 (EditText) ＋ 发送 (Button)"这种意见反馈实现起来很简单，也满足大部分app的反馈的需求了，可目前在做的项目因为产品定位上需要，希望对用户的反馈的及时性还是高一点好，所以集成了友盟的意见反馈(它提供了一个后台回复平台)，且对原始页面进行UI自定义，初步样式如上**

### 2.集成(只介绍Android Studio方式)
1) 一贯的申请开发者账号，注册应用，下载SDK、Demo
2) 在应用对应module下的build.gradle文件中添加:
``` Java
repositories {
        // others
        jcenter()
        maven { url "https://raw.githubusercontent.com/umeng/mvn-repo-umeng/master/repository" }
    }
    
dependencies {
    // others
    compile 'com.umeng:fb:5.3.0'
    compile 'com.android.support:support-v4:21.+'
}
```
3) "AndroidManifest.xml", 在<application>标签中添加对应的Activity, APPKEY, 和权限，注意替换其中的"YOUR_APP_KEY" 和"Channel ID"。
``` Java
<manifest>
    // others
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <application>
        // others
        <activity
            android:name=".x.me.FeedBackActivity"
            android:screenOrientation="portrait"/>
        <meta-data
        android:value="YOUR_APP_KEY"
        android:name="UMENG_APPKEY"/>
        <meta-data
        android:value="Channel ID"
        android:name="UMENG_CHANNEL"/>
    </application>
</manifest>
```
4) 自定义页面布局、参照开发文档和官方demo实现页面功能
> 这里不细讲实现细节了，待当前项目完成后我将我的意见反馈模块抽出来做成demo放到github上，看demo会更清楚