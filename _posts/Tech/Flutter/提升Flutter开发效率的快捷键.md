---
title: 提升 Flutter 开发效率的快捷键
date: 2019-02-12 11:14:12
categories: 
    - Tech
    - Flutter
permalink: flutter-shortcuts-for-fast-development
---


## 创建一个新的 Stateless 或者 Stateful widget

只需输入`stless`即可创建一个像这样的Stateless widget：

![快速创建一个 Stateless Widget](https://i.loli.net/2019/02/12/5c623f4ea52fb.gif)

或者输入`stful`来快速创建一个Stateful widget：

![快速创建一个 Stateful Widget](https://i.loli.net/2019/02/12/5c623f4ebc6a0.gif)

如果想从已经建好的Stateless widget转换成Stateful widget，该怎么做呢？我之前的做法是快速新建一个同名的Stateful widget，然后手动copy、paste之前的代码。虽然也可以，就是有点慢。这里其实有个更高效的办法实现。

您可以将光标放在`StatelessWidget`上，按`Alt + Enter`快捷键（Windows和Mac一样）并单击`Convert to StatefulWidget`就可以了。

![](https://i.loli.net/2019/02/12/5c624124e1b2e.gif)

<!-- more -->

## `Alt + Enter`快捷键的其它用法

您可以单击选中任何 widget，然后按`Alt + Enter`查看您对该特定widget的可选项。例如：

- Add a Padding Around a Widget
![](https://i.loli.net/2019/02/12/5c624124d4e97.gif)

- Center a Widget
![](https://i.loli.net/2019/02/12/5c624123bfd70.gif)

- Wrap with a Container, Column, Row or any other Widget
![](https://i.loli.net/2019/02/12/5c62412406b6b.gif)
![](https://i.loli.net/2019/02/12/5c624123ec46a.gif)
![](https://i.loli.net/2019/02/12/5c624123c47c9.gif)

- Don’t like a widget? Remove it with the Magic Wand.
![](https://i.loli.net/2019/02/12/5c6243c21f5a6.gif)

总而言之，`Alt + Enter`快捷键在flutter开发中特别有用，在您想要对特定widget进行某些操作时，请习惯尝试使用这个快捷。相信我，一定能提升开发效率的。

## 查看widget的源码

对于新手来说，对widget的属性方法等都还不是很了解，查看源码是件高频的事情。加上flutter官方为每个widget添加了很详细的注释说明，方便开发者查阅学习。

之前我都是手动按住command（Mac）或control（Windows）键再click跳转过去查看源码的，其实可以通过快捷键`Ctrl + B`（Windows）或`Command + B`（Mac），也可以使用`F4 / Control + Enter`（Windows）或`F4 / Command + Down Arrow`（Mac），达到同样目的。

![](https://i.loli.net/2019/02/12/5c6264c4c5c44.gif)

## 在当前页面查看 Widget 的构造方法包含的属性

上面介绍的通过快捷键`Ctrl + B`（Windows）或`Command + B`（Mac）来查看widget的源码，如果您只是想快速看一下widget的有哪些属性，可以通过另一个快捷键`Ctrl+Shift+I`（Windows）或`Command + Y`（Mac）做到。

![](https://i.loli.net/2019/02/12/5c6264c57f89f.gif)

## 快速选择整个widget

![](https://i.loli.net/2019/02/12/5c626567c0175.gif "一般操作。如果widget包含的代码比较多，嵌套深的话这样操作就会显得很麻烦且容易错")

![](https://i.loli.net/2019/02/12/5c62656805b00.gif "推荐使用快捷键操作。`Ctrl + W`（Windows）或`Option + Up`（Mac）")

## 代码格式化

这个快捷键就跟其它使用时没啥区别了：
`Control + Alt + L`（Windows）或`Command + Option + L`（Mac）

![](https://i.loli.net/2019/02/12/5c62677c483f8.gif)

## 重构重命名（Refactor Renaming）

这个快捷键也跟其它时候使用时没区别，大家应该很熟悉了：
`Shift + F6`（Windows和Mac一样）。

![](https://i.loli.net/2019/02/12/5c626824df656.gif)

## 移除没用的 imports（Optimize imports）

`Control + Alt + O`（Windows）或`Control + Option + O`（Mac）

![](https://i.loli.net/2019/02/12/5c6268249128e.gif)


# Flutter Outline

Flutter Outline 不是快捷键了，它是IDE给开发者提供的一个非常有用的工具。所以我这里也一并列出来。

首先打开Outline窗口后，我们可以统览整个dart文件的结构，包括widget树的子孙层级，清晰明了。
![](https://i.loli.net/2019/02/12/5c626b24de53a.png)

开发过程中，您可以使用Alt + Enter执行大部分操作，例如使用Center a Widget，但Flutter Outline选项卡下还有更多可用的东西！如下图中红色区域的三个按钮提供的功能。

![](https://i.loli.net/2019/07/29/5d3ec0dc8ad8f42413.png)

##  将代码提取到方法中（Extract code into a method）

如果你觉得你正在编写一个很长而且应该是自定义Widget的Widget，那么你可以使用这个工具为你提供的方法，而不是手动将代码移到一个方法中。

![](https://i.loli.net/2019/02/12/5c626b261b4e1.gif)

## 上下移动widget

Outline可以做的另一个很效率的事情是，如果widget中有多个子widget，您可以轻松地重新排列它们的顺序：

![](https://i.loli.net/2019/02/12/5c626b255c53b.gif)


**附注：**

写这篇文章其实是想对刚刚在Medium上阅读到的[另一篇文章](https://medium.com/flutter-community/flutter-ide-shortcuts-for-faster-development-2ef45c51085b)的完善，那篇文章总结的快捷键对新手来说已经很好，gif动图让读者也浅显易学，我文章里的gif图也是挪用自那里。其中有个别操作我之前也不知道，从她那里学到了很开心。不过有个问题是，她文章中提及的所有快捷键都仅基于Windows提供的，并没有相对应的Mac版本，因此我在她基础上作补充完善，希望能方便到更多的读者。

同样，如果您有其它的上面未列出的快捷操作，欢迎评论告知我，谢谢。后面我也会将我知道的更多flutter提升开发效率的方法记录在这篇文章中。


-------

延伸阅读：

[Flutter: My favourite keyboard shortcuts](https://medium.com/coding-with-flutter/flutter-my-favourite-keyboard-shortcuts-63f6474afc8c)