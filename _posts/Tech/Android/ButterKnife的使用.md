---
title: ButterKnife 的使用
date: 2015-05-23 09:05  
categories: 
    - Tech
    - Android
permalink: Use-ButterKnife
---

![butterknife-logo](https://i.loli.net/2019/07/29/5d3e9073405cd33033.png)
[ButterKnife](https://github.com/JakeWharton/butterknife)是一个通过对Android View添加注解的方式来提高开发效率的开源库。

### 1.配置
在项目中配置ButterKnife有下面几种方式:   

#### JAR
旧式导jar包:[Butter Knife v6.1.0 JAR](http://repo1.maven.org/maven2/com/jakewharton/butterknife/6.1.0/butterknife-6.1.0.jar)
#### MAVEN
如果你使用maven，可以添加butterknife库作为依赖
```java
<dependency>
  <groupId>com.jakewharton</groupId>
  <artifactId>butterknife</artifactId>
  <version>6.1.0</version>
</dependency>
```
#### GRADLE
如果你使用gradle构建android项目（Android Studio默认构建方式），则可以在app -> build.gradle -> dependencies节点添加下面配置
```java
compile 'com.jakewharton:butterknife:6.1.0'
```
如果项目编译时出现类似`InvalidPackage: Package not included in Android`错误，则需要在app -> build.gradle -> android节点添加下面配置(不过我没出现这错误...)
```python
android {
...
   lintOptions {
   disable 'InvalidPackage'
   }

   packagingOptions {
   exclude 'META-INF/services/javax.annotation.processing.Processor'
   }
}
```
### 2.使用
#### 2.1 ACTIVITY INJECTION
```java
class ExampleActivity extends Activity {
  @InjectView(R.id.title) TextView title;
  @InjectView(R.id.subtitle) TextView subtitle;
  @InjectView(R.id.footer) TextView footer;

  @Override public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.simple_activity);
    ButterKnife.inject(this);
    // TODO Use "injected" views...
  }
}
```

#### 2.2 NON-ACTIVITY INJECTION
也可以对除Activity之外的view对象进行注入，不过要在获取到view root对象后。
```java
public class FancyFragment extends Fragment {
  @InjectView(R.id.button1) Button button1;
  @InjectView(R.id.button2) Button button2;

  @Override public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    View view = inflater.inflate(R.layout.fancy_fragment, container, false);
    ButterKnife.inject(this, view);
    // TODO Use "injected" views...
    return view;
  }
  
  @Override public void onDestroyView() {
    super.onDestroyView();
    // set the views to null in onDestroyView
    ButterKnife.reset(this);
  }
}
```
#### 2.3 ViewHolder INJECTION
也可以简化list adapter中的View Holder模式。
```java
public class MyAdapter extends BaseAdapter {
  @Override public View getView(int position, View view, ViewGroup parent) {
    ViewHolder holder;
    if (view != null) {
      holder = (ViewHolder) view.getTag();
    } else {
      view = inflater.inflate(R.layout.whatever, parent, false);
      holder = new ViewHolder(view);
      view.setTag(holder);
    }

    holder.name.setText("John Doe");
    // etc...

    return view;
  }

  static class ViewHolder {
    @InjectView(R.id.title) TextView name;
    @InjectView(R.id.job_title) TextView jobTitle;

    public ViewHolder(View view) {
      ButterKnife.inject(this, view);
    }
  }
}
```

#### 2.4 LISTENER INJECTION
可以对事件监听进行注入(方法的参数可以按需添加)
```java
@OnClick(R.id.submit)
public void submit() {
  // TODO submit data to server...
}
```
可以一次指定多个id，同时加事件
```java
@OnClick({ R.id.door1, R.id.door2, R.id.door3 })
public void pickDoor(DoorView door) {
  if (door.hasPrizeBehind()) {
    Toast.makeText(this, "You win!", LENGTH_SHORT).show();
  } else {
    Toast.makeText(this, "Try again", LENGTH_SHORT).show();
  }
}
```
可以给listview的item点击事件添加注入
```java
@OnItemClick(R.id.list_view)
void onItemClick(AdapterView<?> parent, View view, int position, long id) {
  // TODO ...
}
```
自定义的view不用指定具体id也可以绑定它的listeners
```java
public class FancyButton extends Button {
  @OnClick
  public void onClick() {
    // TODO do something!
  }
}
```

#### 2.5 OPTIONAL INJECTIONS
通常情况下不会出现`the target view cannot be found`情况，但为了避免出现而报异常，可以在变量或者方法前面加上 `@Optional` 注解
```java
@Optional @InjectView(R.id.might_not_be_there) TextView mightNotBeThere;

@Optional @OnClick(R.id.maybe_missing) void onMaybeMissingClicked() {
  // TODO ...
}
```
#### 2.6 其他
有一些View, Activity, or Dialog可能还是会去find views id，butterknife提供了findById方法，它会自动强转为正确类型。
```java
View view = LayoutInflater.from(context).inflate(R.layout.thing, null);
TextView firstName = ButterKnife.findById(view, R.id.first_name);
TextView lastName = ButterKnife.findById(view, R.id.last_name);
ImageView photo = ButterKnife.findById(view, R.id.photo);
```

### 3.混淆
如果你在打包apk时需要对代码进行混淆处理，这时为了避免那些使用了butterknife注解的文件被认为无用而删除，可以在app -> proguard-rules.pro 文件中添加下面混淆规则：
```python
# *********** For ButterKnife **************
-keep class butterknife.** { *; }
-dontwarn butterknife.internal.**
-keep class **$$ViewInjector { *; }

-keepclasseswithmembernames class * {
    @butterknife.* <fields>;
}

-keepclasseswithmembernames class * {
    @butterknife.* <methods>;
}
```

更多相关内容请查看源码和官方说明:
[ButterKnife Github](https://github.com/JakeWharton/butterknife)
[ButterKnife Introduction](http://jakewharton.github.io/butterknife/)

