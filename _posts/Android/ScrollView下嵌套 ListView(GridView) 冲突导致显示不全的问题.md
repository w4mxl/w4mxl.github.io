---
date: 2015-06-17 11:35
categories: Android
title: ScrollView下嵌套 ListView(GridView) 冲突导致显示不全的问题
url: ScrollView-with-ListView-or-GridView'
---

## 问题描述
为了满足功能需求，界面布局中常常需要用到 ScrollView 下嵌套 ListView(GridView) 的情况，ScrollView 可以滚动，而 ListView(GridView) 只作数据展示不能滚动。而写完调试时会发现，ListView(GridView) 只显示了一行数据，自身滚动后能看到剩余数据。原因是ScrollView 中嵌套 ListView(GridView)，无法正确的计算ListView(GridView)的高度。

## 解决方法一
原理:`setAdapter后，获取到每一项item的高度，再动态设置listview或者gridview的高度。`
``` Java
    /**
     * 解决scrollview 嵌套 gridview
     *
     * @param gridView
     * @param columns  gridview的列数
     */
    public static void setGridViewHeightBasedOnChildren(GridView gridView, int columns) {
        ListAdapter listAdapter = gridView.getAdapter();
        if (listAdapter == null) {
            return;
        }
        int totalHeight = 0;
        int count = listAdapter.getCount();
        View listItem = listAdapter.getView(0, null, gridView);
        listItem.measure(0, 0);
        totalHeight = listItem.getMeasuredHeight() + 9;

        int yu = count % columns;

        ViewGroup.LayoutParams params = gridView.getLayoutParams();

        if (yu > 0) {
            params.height = (count - yu) / columns * (totalHeight + 9) + totalHeight;
        } else {
            params.height = count / columns * totalHeight + (count / columns - 1) * 9;
        }

        gridView.setLayoutParams(params);
    }

    /**
     * 解决scrollview 嵌套 listview
     *
     * @param listView
     */
    public static void setListViewHeightBasedOnChildren(ListView listView) {
        ListAdapter listAdapter = listView.getAdapter();
        if (listAdapter == null) {
            return;
        }
        int totalHeight = 0;
        int count = listAdapter.getCount();
        for (int i = 0; i < count; i++) {
            View listItem = listAdapter.getView(i, null, listView);
            listItem.measure(0, 0);
            totalHeight += listItem.getMeasuredHeight();
        }
        ViewGroup.LayoutParams params = listView.getLayoutParams();
        params.height = totalHeight + (listView.getDividerHeight() * (count - 1));
        // listView.getDividerHeight()获取子项间分隔符占用的高度
        // params.height最后得到整个ListView完整显示需要的高度
        listView.setLayoutParams(params);
    }
```
此方法需要注意:
一、是Adapter中getView方法返回的View的必须由LinearLayout组成，因为只有LinearLayout才有measure()方法。
二、有时是需要手动把ScrollView滚动至最顶端。

## 解决方法二
原理:`重写 ListView、GridView 的 onMeasure 方法`
``` Java
public class MyListView extends ListView {
    public MyListView(Context context) {
        super(context);
    }

    @Override
    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        int expandSpec = MeasureSpec.makeMeasureSpec(Integer.MAX_VALUE >> 2,
                MeasureSpec.AT_MOST);

        super.onMeasure(widthMeasureSpec, expandSpec);
    }

} 
- - - - - - - -
public class MyGridView extends GridView{
    public MyGridView(Context paramContext, AttributeSet paramAttributeSet) {
        super(paramContext, paramAttributeSet);
    }

    @Override
    public void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        int expandSpec = MeasureSpec.makeMeasureSpec(Integer.MAX_VALUE >> 2,MeasureSpec.AT_MOST);
        super.onMeasure(widthMeasureSpec, expandSpec);
    }
}
```
修改xml布局文件，代码中不用改动:
``` Xml
<xx..MyGridView(MyListView)
    xxx
    xxx
</xx..MyGridView(MyListView)>
```
这种方法虽然能够显示完整，但是ListView(GridView)边缘滑动仍会有阴影，如果需要去掉边缘滑动阴影（这些效果耗内存）:
``` Xml
android:overScrollMode="never"
```
> 此方法更详细的理论分析可以参见:
[http://blog.csdn.net/aqswde35025/article/details/41863203](http://blog.csdn.net/aqswde35025/article/details/41863203)