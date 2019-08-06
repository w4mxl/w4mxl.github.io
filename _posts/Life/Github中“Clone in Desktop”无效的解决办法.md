---
title: Github中 “Clone in Desktop” 无效的解决办法
date: 2014-10-27 19:48:01
categories: Life
permalink: Github中“Clone-in-Desktop”无效的解决办法
---

### 问题描述：

<img src="/image/图/Make “Clone in Desktop” down01.png" width="180" />

在你想对Github中感兴趣的项目实践自己想法的时候，需要去“Clone in Desktop”，然后进行自己的code。当你第一次点击“Clone in Desktop”按钮，会跳转到Github for Mac的下载页面。当你下载、安装及登录好客户端之后，再去点“Clone in Desktop”发现还是同上，页面又跳转到Github for Mac的下载页面。
　　
### 解决：
Google搜索一番之后，找到了[这篇文章](https://help.github.com/articles/github-conduit)。大体意思是，如果一切就绪你查看这个[https://ghconduit.com:25035/status](https://ghconduit.com:25035/status)，返回的json格式应该是：

	{"capabilities":["status","unique_id","url-parameter-filepath"],"running":true,"server_version":"5"} 

而当我点击的时候并没有返回这些，所以我试着把“127.0.0.1       ghconduit.com”添加到 private/etc/hosts 文件的末尾，保存之后，刷新页面（我用的chrome dev浏览器）发现还是不行。然后我打开Safari试了下（在没往hosts中添加“127.0.0.1       ghconduit.com”前也用Safari试过，是不行的），发现这下可以了正常把想要的项目“Clone in Desktop”了。

