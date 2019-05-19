---
date: 2015-07-06 20:03
categories: Android
title: Intent的Flag属性
permalink: Intent-Flag
---

这篇是想接着上篇[「Activity的启动模式」](http://wml.farbox.com/post/activity-launchMode)，从实际需求场景的出发介绍下Intent与启动模式相关的Flag使用。(注:并为将所有 Flag 介绍完全，因为有些我没实际用过可能还没有理解足够深刻，只写个人实际使用过并觉得理解到位了的，后续会补充)

### 常见需求场景
**需求1:**
> 前提: 下面的 Activity A B C D 都没有显式的指明launchMode 和 taskAffinity 属性。

已经启动了四个 Activity: A，B，C和D。在 D Activity里，我们想要跳到 B Activity，同时希望C Activity finish掉。
**实现:**: FLAG_ACTIVITY_CLEAR_TOP
``` JAVA
Intent intent = new Intent(this, B.class);
intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);// D Activity
startActivity(intent);
```
**结果:**
D、C、B Activity 依次调用各自的 onDestroy 方法出栈 －> B Activity 重新启动(onCreate)
栈中为: A B
***
**需求2:**
在需求1的基础上，只是不想重新再创建一个新的B Activity，而是重用原来的实例。
**实现:**: Intent.FLAG_ACTIVITY_CLEAR_TOP | Intent.FLAG_ACTIVITY_SINGLE_TOP
``` JAVA
Intent intent = new Intent(this, B.class);
// intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);// D Activity
intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP | Intent.FLAG_ACTIVITY_SINGLE_TOP);// D Activity
startActivity(intent);
```
**结果:**
依次，C onDestroy -> B Activity onNewIntent onRestart -> D onDestroy
栈中为: A B
***
**需求3:**
> 前提: 下面的 Activity A B C D 都没有显式的指明 launchMode 和 taskAffinity 属性。

已经启动了四个Activity：A，B，C和D。在D Activity里，想再启动一个Actvity B，但不变成A,B,C,D,B，而是希望是A,C,D,B。
**实现:**: Intent.FLAG_ACTIVITY_REORDER_TO_FRONT
``` JAVA
Intent intent = new Intent(this, B.class);
intent.setFlags(Intent.FLAG_ACTIVITY_REORDER_TO_FRONT);// D Activity
startActivity(intent);
```
**结果:**
依次，B Activity onNewIntent onRestart
栈中为: A C D B
***
### 其他常见 FLAG 说明
**FLAG_ACTIVITY_NO_HISTORY**
例如现在栈情况为：A B C。C 通过 intent 跳转到 D，这个intent添加 FLAG_ACTIVITY_NO_HISTORY 标志，则此时界面显示D的内容，如果此时D中又跳转到E，栈的情况变为: A B C E，此时按返回键会回到C，因为D根本就没有被压入栈中。

**FLAG_ACTIVITY_NEW_TASK**
例如现在栈1的情况是：A B C。C 通过intent跳转到 D，并且这个 intent 添加了 FLAG_ACTIVITY_NEW_TASK 标 记，如果 D 这个 Activity 在 Manifest.xml 中的声明中添加了 Task affinity，并且和栈1的 affinity 不同，系统首先会查找有没有和 D 的 Task affinity 相同的 task 栈存在，如果有存在，将 D 压入那个栈，如果不存在则会新建一个 D 的 affinity 的栈将其压入。如果 D 的 Task affinity 默认没有设置，或者和栈1的 affinity 相同，则会把其压入栈1，变成：A B C D，这样就和不加 FLAG_ACTIVITY_NEW_TASK 标记效果是一样的了。

**FLAG_ACTIVITY_NO_ANIMATION**
这个标志将阻止系统进入下一个 Activity 时应用 Acitivity 迁移动画。