---
date: 2015-08-17 09:41
categories: 
    - Tech
    - Android
title: Fragment 重叠（重影）问题
permalink: fragment-overlay-problem
---

在最近做的项目中，遇到了 Fragment 重叠的问题。具体的情况是，app 需要在多个 Fragment 间切换，并且保存每个 Fragment 的状态。官方的方法是使用 replace() 来替换 Fragment，但是 replace() 的调用会导致 Fragment 的 onCreteView() 被调用，所以切换界面时会无法保存当前的状态。因此一般采用 add()、hide()与 show()配合，来达到保存 Fragment 的状态。

正常情况下显示是对的，现象发生在我切换到其他的app，操作一会之后，再回到当前的app，有一定几率会出现 Fragment 重叠的现象。

可以通过下面的方式进行手动重现这个BUG:
1. 手机的 "设置" - "开发者选项" - 打开"不保留活动"（主要用于模拟Activity被及时回收）
2. 把 app 切换到后台，再重新打开，通过点按不同的 tab 来切换 Fragment

<center><img src="https://i.loli.net/2019/07/29/5d3e90bb2629751126.png" width="280" alt="重现 Fragment 的重叠"/></center>


起初我以为是我在使用add()、hide() 、show() 切换 Fragment 的时候有什么地方使用的不对，尝试去解决重叠的 bug，无果后，还是通过 google 找出了原因和解决方案。

#### 原因
使用 Fragment 的状态保存，当系统内存不足，Fragment 的宿主 Activity 回收的时候，Fragment 的实例并没有随之被回收。Activity 被系统回收时，会主动调用 onSaveInstance() 方法来保存视图层（View Hierarchy），所以当 Activity 通过导航再次被重建时，之前被实例化过的 Fragment 依然会出现在 Activity 中，此时的 FragmentTransaction 中的相当于又再次 add 了 fragment 进去的，hide()和show()方法对之前保存的fragment已经失效了。综上这些因素导致了多个Fragment重叠在一起。

#### 解决
**方案一:**

1.给每个 Fragment 加一个 Tag
2.在 onCreate(Bundle savedInstanceState) 中判断 Bundle savedInstanceState 是否不为空
3.不为空则进行 find Tag，重新给几个 frament 赋值
这样子仍是对之前保存的 fragment 操作，成功解决了重叠的问题。

**方案二:**

Activity 中的 onSaveInstanceState() 里面有一句*super.onSaveInstanceState(outState);*，Google 对于这句话的解释是 “Always call the superclass so it can save the view hierarchy state”，大概意思是“总是执行这句代码来调用父类去保存视图层的状态”。通过注释掉这句话，这样主 Activity 因为种种原因被回收的时候就不会保存之前的 fragment state，也可以成功解决重叠的问题。