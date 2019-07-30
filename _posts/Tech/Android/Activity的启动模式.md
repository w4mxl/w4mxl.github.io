---
date: 2015-07-08 08:34
categories: 
    - Tech
    - Android
title: Activity 的启动模式
permalink: activity-launchMode
---

在实际项目中我们应该根据特定的需求为每个 Activity 指定适当的启动模式。这里根据个人理解和实际开发中的经验，做些总结。有四种启动模式，分别是 standard 、singleTop 、singleTask 和singleInstance 。可以在 AndroidManifest.xml 中通过给 &lt;activity> 对应的标签指定 android:launchMode 属性来设置启动模式。

![设定启动模式](https://i.loli.net/2019/07/29/5d3e6e0e587b651251.png)

为了介绍清这四种启动模式，我们应该先清楚下面两个概念: task、taskAffinity。

> task

task 是一组相互关联的 activity 的集合，存在于一个称为 back stack 的 "First In Last Out" 的栈结构中，控制着界面的跳转和返回。task 是可以跨应用的，有的 Activity，虽然不在同一个 app 中，但为了保持用户操作的连贯性，把他们放在同一个 task 中。例如，在我们的应用中的一个Activity A中点击发送邮件，会启动邮件程序的一个Activity B 来发送邮件，这两个 activity 是存在于不同app中的，但是被系统放在一个 task 中，这样当发送完邮件后，用户按 back 键返回，可以返回到原来的 Activity A 中，这样就确保了用户体验。

> taskAffinity

taskAffinity 是 Activity 的一个属性。它的作用是用来描述不同 Activity 之间的亲密关系。默认情况下（在  manifest 中没有对 Activity 的 android:taskAffinity 进行配置），Activity 的这个属性就等于 Application 指明的 taskAffinity，如果 Application 也没有指明，那么该 taskAffinity 的值就等于包名。而 Task 也有自己的 affinity 属性，它的值等于它的根 Activity 的 taskAffinity 的值。我们可以通过为 activity 设置不同的 taskAffinity 属性给 app 中的 activity 分组，也可以把不同的 app 中的 activity 的 taskAffinity 设置成相同的值。为一个 activity 的 taskAffinity 设置一个空字符串，表明这个 activity 不属于任何 task。

#### standard 模式
activity 的默认启动模式。activity A 设定为 standard 模式（不做任何设置默认就是 standard），即可以被多次实例化，在同一个 task 中可以存在多个 activity A 的实例，每个实例都会处理一个 Intent 对象。例，Activity A 的启动模式为 standard，并且A已经启动，在A中再次启动 Activity A，即调用startActivity(new Intent(this，A.class))，会在A的上面再次启动一个A的实例，即当前的桟中的状态为A --> A。
#### singleTop 模式
字面上**“顶部只能有一个”**。例，activity A 设定为 singleTop 模式后，并且A的一个实例已经存在于栈顶中，那么再调用 startActivity(new Intent(this，A.class)) 启动A时，不会再次创建A的实例，而是重用原来的实例，并且调用原来实例的 onNewIntent() 方法。这时任务桟中还是只有一个A的实例。如果 activity A 的一个实例已经存在于任务桟中，但是不在桟顶，那么再次调用的行为和 standard 模式相同，还会创建出一个实例。
#### singleTask 模式
字面上**“只容许有一个包含该 Activity 实例的 task 存在”**。使用 singleTop 模式可以很好的解决重复创建栈顶活动的问题。但是上面也说到，如果这个活动(activity)并没有处于栈顶的位置，还是会出现同一活动多个实例的现象。而 singleTask 模式正好就可以对上述问题就行补充解决。不过这里要注意的是，下面说的结论跟前面提到的概念:taskAffinity 就有关系了。例，以 activity A(standard模式)启动 activity B(singleTask模式)来说，
1. 当A和B的 taskAffinity 相同时(没有显式的指明该Activity的taskAffinity)，A要启动B活动时，*并不会启动新的task*，系统首先会在默认返回栈中检查是否存在B活动的实例，如果发现已经存在则直接使用该实例，会调用B的 onNewIntent()方法，并把在这个活动之上的所有活动统统出栈，如果没有发现就会创建一个新的B活动实例。
2. 当A和B的 taskAffinity 不同时，A要启动B活动时，*会有新的task*，系统首先会在新的task中检查是否存在B活动的实例，如果发现已经存在则直接使用该实例，会调用B的 onNewIntent() 方法，并把在这个活动之上的所有活动统统出栈，如果没有发现就会将新的B活动实例添加到新的task中。
#### singleInstance 模式
字面上**“任意时刻只允许存在唯一的 Activity 实例”**。设定为 singleInstance 模式的 Activity 会启用一个新的 task(返回栈)来管理这个活动。**该 task 只能容纳该 Activity 实例，不会再添加其他的 Activity 实例**。如果该 Activity 实例已经存在于某个 task，则直接跳转到该 task。
它与 singleTask 有相同之处，也有不同之处。
**相同:**任意时刻，最多只允许存在一个实例。
**不同:**
- singleTask 受 android:taskAffinity 属性的影响，而 singleInstance 不受 android:taskAffinity 的影响。
- singleTask 所在的 task 中能有其它的 Activity，而 singleInstance 的 task 中不能有其他 Activity。
- 当跳转到 singleTask 类型的 Activity，并且该 Activity 实例已经存在时，会删除该 Activity 所在 task 中位于该 Activity 之上的全部 Activity 实例；而跳转到 singleInstance 类型的 Activity，并且该 Activity 已经存在时，不需要删除其他 Activity，因为它所在的 task 只有该 Activity 唯一一个 Activity 实例。