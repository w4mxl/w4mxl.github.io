---
title: 在 VS Code 上显示 Flutter icons 和 color 预览
categories: 
    - Tech
    - Flutter
permalink: show-flutter-icons-in-vscode
---

之前在用 Android Studio 开发 Flutter 的时候，有个比较好用的功能是，在代码中引用的颜色和图标会在代码编辑器左边缘相应的显示出对应的颜色和图标预览。就像下面截图中那样。

![Android Studio 上引用颜色和图标会自动显示预览](https://i.loli.net/2019/11/25/fnCoJmHchazSWEZ.png)

但是在切换到 VS code 后发现默认并不会这样了。经过 Google，发现有人已经在 Dart 仓库下提了 issue，并有开发者合并了解决方案。所以如果你的 Dart 插件已经更新到 3.6.0 版本，只需要在 VS code 设置中搜索 "Flutter gutter"，勾选上 Dart: Preview Flutter Gutter Icons 选项后重启一下 VS code 就好。这样，熟悉的颜色和图标预览功能就又回来了～

![勾选上 Dart: Preview Flutter Gutter Icons 选项](https://i.loli.net/2019/11/25/SYA2tmO5QVrP7Z6.png)

相关链接：

- [color and icon preview extension in VSCode for Flutter #1181](https://github.com/Dart-Code/Dart-Code/issues/1181)
- [Show Flutter icons in the editor gutter #807](https://github.com/Dart-Code/Dart-Code/issues/807)
- [Show Flutter icons in the gutter #2040](https://github.com/Dart-Code/Dart-Code/pull/2040)