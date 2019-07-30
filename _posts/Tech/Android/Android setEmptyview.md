---
title: Android setEmptyview
date: 2015-08-22 22:25
categories: 
    - Tech
    - Android
permalink: Android-setEmptyview
---

### 1. 介绍

使用 listview、gridview 等列表形式的 view 时，如果后台server返回的数据为空，通常我们需要为页面增加 empty view （俗称空页面），使得页面显示起来更友好，这个时候就用到了 setEmptyView() 方法。

<center>
![setEmptyView() 是 AdapterView 中的一个方法，而我们常用到的ExpandableListView, GridView, ListView等都是继承之 AdapterView 的，可以直接调用 setEmptyView() 方法](https://i.loli.net/2019/07/29/5d3e8dd42555511590.png)</center>  


<center>![setEmptyView() 官方描述](https://i.loli.net/2019/07/29/5d3e8e1f1472182998.png)</center>

### 2. 使用方法

下面以一个简单实例的描述 setEmptyview() 的两种常见的使用方法。

<center><img src='https://i.loli.net/2019/07/29/5d3e8e6bb5f8075733.png' width="280"/>
▲ 实例的最终效果。“暂无常用回答哦”这个 TextView 就是我们设定好的 empty view 。</center>

**方法一**

如果页面是继承 ListActivity，只要在布局文件中这样:
```java
...
<ListView android:id="@id/android:list".../> 
<TextView 
    android:id="@id/android:empty 
    android:text="暂无常用回答哦"
    .../>
...
```
这样当列表为空时就会自动显示这个 TextView 了。

如果页面不是继承 ListActivity 的话，
```java
...
<ListView android:id="@+id/list".../> 
<TextView 
    android:id="@+id/empty 
    android:text="暂无常用回答哦"
    .../>
...
ListView listView = (ListView)findViewById(R.id.list);
listView.setEmptyView(findViewById(R.id.empty));
```

**方法二**

setEmptyView()这个方法是有限制的，这个 empty view 必须在当前的 View hierarchy 的节点上，所以需要把empty view 添加到当前的 View hierarchy 的节点上。布局文件中不作额外配置，在页面中实现如下:
```java
TextView emptyView = new TextView(activity);
emptyView.setLayoutParams(new LayoutParams(LayoutParams.FILL_PARENT, LayoutParams.FILL_PARENT));
emptyView.setText("暂无常用回答哦");
emptyView.setVisibility(View.GONE);
((ViewGroup) list.getParent()).addView(emptyView);
list.setEmptyView(emptyView);
```
同理，如果 empty view 不简单是一个 TextView 而是其他一个较复杂的自定义 View，则可以通过 inflate:
```java
View emptyView = View.inflate(R.layout.empty_view, null);
emptyView.setVisibility(View.GONE);
((ViewGroup) list.getParent()).addView(emptyView);
list.setEmptyView(emptyView);
```

### 3. 尾巴
ViewStub 在很多时候也是可以实现我们空页面的需求，在页面中的数据不是动态变化的情况下，使用 ViewStub 也是不错的选择。