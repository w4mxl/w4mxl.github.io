---
title: 使用 SparseArray 替代 HashMap
date: 2015/06/14 13:51:00
categories: 
    - Tech
    - Android
permalink: use-sparse-array
---

今天在用 Android Studio > Analyze > Inspect Code 对目前项目进行检查后给出了很多优化建议，其中一类是关于用SparseArray替代HashMap的。

![用SparseArray<E>来替代，以获取更好性能](https://i.loli.net/2019/07/29/5d3e98da0efef38754.png)

![对应的实际代码块](https://i.loli.net/2019/07/29/5d3e99185af4130533.png)

老实说我之前开发中用HashMap比较多，还真没用过SparseArray，当看到建议后就去google了解它。

> SparseArray是android里为<Interger,Object>这样的Hashmap而专门写的类，目的是提高效率，其核心是折半查找函数（binarySearch）。

我这里就结合我自己项目说下当我知道了SparseArray优势后是怎么用SparseArray替代HashMap的。至于SparseArray更具体的原理介绍网络上写的很好的已经很多，比如[这篇](http://liuzhichao.com/p/832.html)。

#### 修改之前(HosBuildingFloorAdapter.java)：
``` JAVA
HashMap<Integer, String> hashMap;//buildingId、buildingName的捆绑

// Adapter构造方法中对hashMap实例化
hashMap =  new HashMap<Integer, String>();
for (int i = 0; i < buildings; i++) {
    hashMap.put(buildingListEntities.get(i).getBuildingId(), buildingListEntities.get(i).getBuildingName());
}

// Adapter的getHeaderView中取值
for (Map.Entry<Integer, String> entry : hashMap.entrySet()) {
    if (floorListEntities.get(position).getBuildingId() == entry.getKey()) {
        holder.text.setText(entry.getValue());
    }
}
```
#### 修改之后:
``` JAVA
SparseArray<String> stringSparseArray;

// Adapter构造方法中对stringSparseArray实例化
stringSparseArray = new SparseArray<>();
for (int i = 0; i < buildings; i++) {
    stringSparseArray.put(buildingListEntities.get(i).getBuildingId(), buildingListEntities.get(i).getBuildingName());
}

// Adapter的getHeaderView中取值
for (int i = 0; i < stringSparseArray.size(); i++) {
    int key = stringSparseArray.keyAt(i);
    if (floorListEntities.get(position).getBuildingId() == key) {
        holder.text.setText(stringSparseArray.get(key));
    }
}
```