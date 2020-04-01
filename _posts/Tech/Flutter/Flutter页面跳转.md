---
title: Flutter 路由管理（页面跳转）
categories: 
    - Tech
    - Flutter
date: 2019-08-07 15:06:44
tags:
permalink: flutter_route_manager
---

# 1. 概述

Flutter 中的路由管理（页面跳转）其实和原生是类似的，无论是 Android 还是 iOS（Android 中的页面通常指一个 `Activity`，在 iOS 中指一个 `ViewController`），路由管理都会维护一个路由栈，路由入栈（push）操作对应打开一个新页面，路由出栈（pop）操作对应关闭一个页面，而路由管理主要是指如何来管理**路由栈**。

Flutter 中的页面跳转有两种方式，一种是构建式路由，另一种是命名式路由。下面我们结合实际例子来介绍一下这两种路由的使用方式和它们的异同。

<!-- more -->

# 2. 构建式路由

先介绍一下构建式路由。所谓构建式路由，是指通过我们自定义构建出来一个路由来供页面跳转使用。下面通过一个简单的示例先看下效果：

预览：

<img src='https://i.loli.net/2019/08/09/DxF9trOzUfGiNHu.gif' width='300' alt='使用构建式路由进行页面跳转' />

代码：

`page_first.dart`: 页面很简单，在中间显示一个按钮，用于点击后跳转到下一页。
``` dart
import 'package:flutter/material.dart';

import 'page_two.dart';

class PageFirst extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page one'),
      ),
      body: Center(
        child: RaisedButton(
          onPressed: () => Navigator.push(context, MaterialPageRoute(builder: (context) => PageTwo())),
          child: Text('下一页'),
        ),
      ),
    );
  }
}
```
`page_two.dart`：点击中间按钮，返回上一页。

``` dart
import 'package:flutter/material.dart';

class PageTwo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page two'),
      ),
      body: Center(
        child: RaisedButton(
          onPressed: () => Navigator.pop(context),
          child: Text('返回'),
        ),
      ),
    );
  }
}
```

## 2.1 Navigator

我们在页面1中间的 `RaisedButton` 的点击事件是 `Navigator.push(context, MaterialPageRoute(builder: (context) => PageTwo()))`。通过查看`Navigator.push`的源码知道，下面这两种写法效果是一样的。其实不但是 `push`，Navigator 类中第一个参数为 context 的静态方法都对应有一个 Navigator 的实例方法。比如，`Navigator.of(context).pop()` 也等价于 `Navigator.pop(context)`。

``` dart
// push 源码
// navigator.dart 

  @optionalTypeArgs
  static Future<T> push<T extends Object>(BuildContext context, Route<T> route) {
    return Navigator.of(context).push(route);
  }
```

``` dart
Navigator.push(context, MaterialPageRoute(builder: (context) => PageTwo()))

Navigator.of(context).push(MaterialPageRoute(builder: (context) => PageTwo()))
```

`Navigator` 是一个路由管理的组件，它提供了打开和退出路由页方法。`Navigator`通过一个栈来管理活动路由集合。Navigator 提供了一系列方法来管理路由栈，这里只介绍其最常用的两个方法：

- `Future<T> push<T extends Object>(BuildContext context, Route<T> route)`
  - 将给定的路由入栈（即打开新的页面），返回值是一个 `Future` 对象，用以接收新路由出栈（即关闭）时的返回数据。
- bool pop<T extends Object>(BuildContext context, [ T result ])
  - 将栈顶路由出栈，`result` 为页面关闭时返回给上一个页面的数据。

## 2.2 MaterialPageRoute

它们都需要传入一个`Route`对象，在 Flutter 中我们可以使用 PageRouteBuilder 来构建这个 Route 对象，或者直接使用整合好了的 MaterialPageRoute。 MaterialPageRoute 很方便，因为它会使用平台特定的动画跳转到新的页面（Android和IOS屏幕切换动画会不同）。

下面我们看一下 MaterialPageRoute 构造函数及其各个参数的意义：

``` dart
MaterialPageRoute({
    @required this.builder,
    RouteSettings settings,
    this.maintainState = true,
    bool fullscreenDialog = false,
})
```

- `builder` ：是一个 WidgetBuilder 类型的回调函数，它的作用是构建路由页面的具体内容，返回值是一个 widget。我们通常要实现此回调，返回新路由的实例。
- `settings`：包含路由的配置信息，如路由名称、是否初始路由（首页）。
- `maintainState`：默认情况下，当入栈一个新路由时，原来的路由仍然会被保存在内存中，如果想在路由没用的时候释放其所占用的所有资源，可以设置 maintainState 为 false。
- `fullscreenDialog`：表示新的路由页面是否是一个全屏的模态对话框，在 iOS 中，如果 `fullscreenDialog`为 true，新页面将会从屏幕底部滑入（而不是水平方向）。

## 2.3 构建式路由的参数传递

页面跳转很多时候是伴随着参数传递的，比如从话题列表跳到话题详情页，需要传一个话题id。又比如购买电影票跳转到选择城市页，选择城市后要把选好的城市带回上一页作为过滤条件。

下面在前面代码基础上扩展一个传参示例，Page one 跳转到 Page two 时带一个参数，同时当从 Page two 返回时也带上一个返回参数。我们看下效果：

预览：

<img src='https://i.loli.net/2019/08/09/bWIVc3ixMUl1Q2t.gif' width='440' alt='使用构建式路由进行页面跳转并传参' />

代码：

`page_first.dart`: 点击后跳转到下一页，并传递一个参数：“我是来自p1的参数”。当接收到返回结果时打印到控制台上。

``` dart
import 'package:flutter/material.dart';
import 'page_two.dart';

class PageFirst extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page one'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            RaisedButton(
              onPressed: () async {
                // 跳转到 page two，等待返回结果
                var result = await Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) => PageTwo(
                      text: '我是来自p1的参数',
                    ),
                  ),
                );
                // 输出 page two 返回来的结果
                print(result);
              },
              child: Text('下一页：传参数'),
            ),
          ],
        ),
      ),
    );
  }
}
```

`page_two.dart`: 接收上一页过来的参数显示。点击“返回”按钮回到上一页带上结果：“我是来自p2的返回值”。

``` dart
import 'package:flutter/material.dart';

class PageTwo extends StatelessWidget {
  final String text;

  const PageTwo({Key key, this.text}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page two'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(text != null ? text : ''),
            RaisedButton(
              onPressed: () => Navigator.pop(context, '我是来自p2的返回值'),
              child: Text('返回'),
            ),
          ],
        ),
      ),
    );
  }
}
```
这里有一点需要注意的是，page two 有两种方式可以返回到上一页；第一种方式是直接点击状态栏返回箭头（iOS 的侧滑返回和 Android 底部虚拟返回按钮也属于这一种），第二种方式是点击页面中的“返回”按钮。这两种返回方式的区别是，前者不会返回数据给上一个路由（接收到的是 `null`），而后者会。

# 3. 命名式路由

”命名式路由“是指我们可以先给路由页面起一个名字，然后把这个”名字“注册到路由表中，后面就可以通过路由名字直接打开新的路由页面了。这种路由管理的方式会显得更统一些。

下面我们还是先通过一个示例看下效果：

预览：

<img src='https://i.loli.net/2019/08/12/GY4nX8BCZ2euPqU.gif' width='300' alt='命名式路由'/>

代码：

```dart

/// main.dart

// 已省略其它无关代码
MaterialApp(
    home: HomePage(),
    routes: <String, WidgetBuilder>{
        // 已省略其它路由注册
        // 把 PageTwo2()  路由页面注册到路由表中，名字设为 'page_two_2'
        'page_two_2': (BuildContext context) => PageTwo2(),
    },
);

/// page_first.dart 

import 'package:flutter/material.dart';

class PageFirst extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page one'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            RaisedButton(
              onPressed: () {
                Navigator.pushNamed(context, 'page_two_2');
              },
              child: Text('下一页：命名式路由'),
            ),
          ],
        ),
      ),
    );
  }
}

/// page_two_2.dart

import 'package:flutter/material.dart';

class PageTwo2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {

    return Scaffold(
      appBar: AppBar(
        title: Text('Page two'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            RaisedButton(
              onPressed: () => Navigator.pop(context),
              child: Text('返回'),
            ),
          ],
        ),
      ),
    );
  }
}

```

## 3.1 注册路由表，打开注册好的页面

可以看见效果和上面的构建式路由没什么区别。在 `main.dart` 代码中，我们把 PageTwo2()  路由页面注册到路由表中，名字设为 'page_two_2'。

我们在 page_first.dart 中通过路由名字 'page_two_2' ，使用 `Navigator` 的 `pushNamed` 方法打开新路由时，应用会根据路由名字在路由表中查找到对应的 WidgetBuilder 回调函数，然后调用该回调函数生成路由 widget 并返回。

在上面 `main.dart` 代码中，HomePage() 没有使用命名式路由，而是使用的 `MaterialApp` 的 `home` 属性指定的，如果我们也想将它注册为命名式路由应该怎么做呢？其实很简单，代码如下：

```dart

/// main.dart

// 已省略其它无关代码
MaterialApp(
    initialRoute:"/", // 名为"/"的路由作为应用的首页
    home: HomePage(),
    routes: <String, WidgetBuilder>{
        '/': (BuildContext context) => HomePage(),
        // 已省略其它路由注册
        // 把 PageTwo2()  路由页面注册到路由表中，名字设为 'page_two_2'
        'page_two_2': (BuildContext context) => PageTwo2(),
    },
);
```

另外，因为 `initialRoute` 默认值即为 "/"，所以如果下面 `routes` 中的首页命名也设为 "/"时，可以省略` initialRoute:"/",`。

## 3.2 命名式路由参数传递

**在 Flutter 最初的版本中，命名式路由是不能传递参数的。** 其实在 Flutter 的 Issues 中16年就有人提出[这个问题](https://github.com/flutter/flutter/issues/6225)，但是这个Issue一直到今年才有 [PR](https://github.com/flutter/flutter/pull/27058) 被提交，后来命名式路由才支持了传参。下面我们演示一下命名式路由如何传递并获取路由参数：

预览：

<img src='https://i.loli.net/2019/08/12/TNMyBbYFAOmj1ln.gif' width='300' alt='命名式路由 & 传参'/>

代码：

``` dart

/// page_first.dart

import 'package:flutter/material.dart';

class PageFirst extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Page one'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            RaisedButton(
              onPressed: () async {
                // 跳转到 page two 2，等待返回结果
                var result = await Navigator.pushNamed(context, 'page_two_2', arguments: '我是来自p1的命名式路由的参数');
                // 输出 page two 返回来的结果
                print(result);
              },
              child: Text('下一页：命名式路由 & 传参'),
            ),
          ],
        ),
      ),
    );
  }
}

/// page_two_2.dart

import 'package:flutter/material.dart';

class PageTwo2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    //获取路由参数
    var text = ModalRoute.of(context).settings.arguments;

    return Scaffold(
      appBar: AppBar(
        title: Text('Page two'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(text != null ? text : ''),
            RaisedButton(
              onPressed: () => Navigator.pop(context, '我是来自p2的返回值'),
              child: Text('返回'),
            ),
          ],
        ),
      ),
    );
  }
}
```

逻辑很简单，page_first 跳转时通过 `arguments` 传参（上面示例是一个文本，也可以是任意自定义的数据对象），page_two_2 接收参数。和 Android 中通过 Intent 传递参数类似。

另外我们也可以将 onGenerateRoute() 函数中的参数并将它们传递给路由页面，而不必直接在路由页面中手动提取参数。这里不再细说，可以看下[官方的示例](https://flutter.dev/docs/cookbook/navigation/navigate-with-arguments)。

# 4. 总结

本文分别介绍了构建式路由和命名式路由的使用方式，包括如何传递参数和接收返回参数。大家在实际项目使用过程中，可以根据自己的喜好选择。如果纠结到底该选择哪种方式好，我这里会更推荐在项目中统一都使用命名式这种路由管理方式。这样的好处是：

1. 写在一处很清晰，方便统一管理
2. 可以通过 `onGenerateRoute` 做一些全局的页面跳转前置处理逻辑

# 5. 参考链接

[flutter.dev/docs/cookbook/navigation/navigate-with-arguments](flutter.dev/docs/cookbook/navigation/navigate-with-arguments)
[flutter.dev/docs/cookbook/navigation/returning-data](flutter.dev/docs/cookbook/navigation/returning-data)