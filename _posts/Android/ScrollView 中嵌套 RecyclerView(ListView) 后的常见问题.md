---
title: "ScrollView 中嵌套 RecyclerView(ListView) 后的常见问题"
date: 2016-09-07 15:53:00
categories: Android
permalink: scrollView-nested-problems
---

### 1. 显示不全
> 被嵌套的 RecyclerView(ListView) 显示不全，有多个 item，则只显示第一个。

解决方法目前常见的有两种：
  1. ~~动态计算 RecyclerView(ListView) 高度~~
  2. 直接展示所有的 item，让其不滚动了 (推荐)

<!-- more -->

> 2 是嵌套 ListView 示例，嵌套 GridView等类似

``` java
public class ScrollViewWithListView extends ListView {

    public ScrollViewWithListView(android.content.Context context, android.util.AttributeSet attrs) {
        super(context, attrs);
    }

    /**
     * 设置不滚动
     */
    public void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        int expandSpec = MeasureSpec.makeMeasureSpec(Integer.MAX_VALUE >> 2,
                MeasureSpec.AT_MOST);
        super.onMeasure(widthMeasureSpec, expandSpec);
    }
}
```


### 2. 自动滚动

场景1:
> ScrollView 中嵌套的组件 RecyclerView(ListView) 在内容加载之后，ScrollView 会自动下滚。

解决方法：

在 ScrollView 包裹的 LinearLayout 中添加：
  
``` xml
android:focusable="true"
android:focusableInTouchMode="true"
```
  
``` xml
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:scrollbars="none">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:focusable="true"
            android:focusableInTouchMode="true">
            ...
            ...
        </LinearLayout>
</ScrollView>
```

[更多描述请查看这篇](http://blog.csdn.net/icyfox_bupt/article/details/15026299)

场景2:
> 在 1 的基础上, Fragment 中的 ScrollView 在初次加载会停留在顶部，可是切换到其它 Fragment 再切换回来的时候，又会自动下滚。

解决方法：

在 ScrollView 包裹的 LinearLayout 中多添加：
  
``` xml
android:focusableInTouchMode="true"
```

``` xml
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:scrollbars="none">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical"
            android:focusable="true"
            android:focusableInTouchMode="true"
            android:focusableInTouchMode="true">
            ...
            ...
        </LinearLayout>
</ScrollView>
```
[是从这里知道的](http://stackoverflow.com/questions/9842494/how-to-prevent-a-scrollview-from-scrolling-to-a-webview-after-data-is-loaded)