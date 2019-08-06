---
title: FUCK GFW!
date: 2014-6-15
categories: Life
permalink: FUCK-GFW!
---

2014/6/16 更新：

由于种种原因（懂的人懂的），最近Google在华的服务被屏蔽的更彻底更无下限了。GoAgent也近乎不能用，一片红黄。不过难不倒我，我已经在goagent客户端local\proxy.ini中加入了些可用的ip地址（已测试可用），同时可以下载此[hosts文件](http://pan.baidu.com/s/1pJx48kV)，将其中内容复制到你的"C:\Windows\System32\drivers\etc\hosts"同名文件的末尾。这样就又可以愉快的科学上网了。

---
众所周知，在中国，因为[GFW](http://zh.wikipedia.org/zh-cn/防火长城)的存在，很多站点不是你我想访问就能自由访问的。每当我看到网页上出现“无法显示此网页”的时候，一边打开goagent，一边会下意识念叨着“FUCK GFW!”。一直希望能把自己使用 chrome + goagent 科学上网的经验写成一篇简单明了的教程，为更多人所知。

### **Step 1 - 申请Google App Engine账号**

打开[http://appengine.google.com/](http://appengine.google.com/ "http://appengine.google.com/")，输入你的Gmail账号、密码登录（如果还没有Gmail邮箱请先去申请一个）。成功登录后，点击下图中的Create Application进入下一步。

![](/image/图/chrome_goagent_01.png)

### **Step 2 - 通过短信验证你的账号**

![](/image/图/chrome_goagent_02.jpg)

需要短信验证才可以进行下一步操作，Country and Carrier（国家和运营商）处选择Other，Mobile Number（手机号码）处填写你的个人手机号码号码，格式为+8613912345678

### **Step 3 - 将手机收到的验证码输入并发送**

![](/image/图/chrome_goagent_03.jpg)

你将会收到谷歌发给你的短信，短信内容大致为：Google App Engine：******（6位数字）。验证成功后，就可以进入下一步。

### **Step 4 - 创建一个属于你的Application**

![](/image/图/chrome_goagent_04.png)

>
1. 输入一个Application ID，允许使用英文字母和短横杆；
2. 点击Check Available，检查一下是否可用；
3. 输入Application名称，这里可以随便填；
4. 勾选I accept these terms，即接受协议；
5. 最后Creat Application

当你看到以下画面，说明你已经成功创建一个 Application

![](/image/图/chrome_goagent_05.png)

### **Step 5 - 下载并配置GoAgent客户端**

>
1. 下载goagent客户端（[点击下载](http://pan.baidu.com/s/190yiq)）,解压到某个目录
2. 双击server\uploader.bat（Windows 7或Windows 8用户最好以管理员身份运行），根据提示依次输入你的appid和Gmail帐号，密码。确定输入后回车确认即可。
3. 上一步提示上传成功后，修改local\proxy.ini中的[gae]下的appid=你最初申请的appid(多appid请用|隔开)，即前面创建Application所设定的Application ID，如我设定的mxl1989；

![](/image/图/chrome_goagent_06.png)

![](/image/图/chrome_goagent_07.png)

### **Step 6 - 在chrome浏览器中安装并配置Proxy SwitchySharp扩展**

>
1. 在chrome浏览器中安装[SwitchySharp](https://chrome.google.com/webstore/detail/dpplabbmogkhghncfbfdeeokoefdjegm)扩展
2. 安装之后浏览器就会自动弹出Switchy Sharp的配置界面，点击【导入/导出】->【从文件恢复】。在弹窗中定位到之前下载的goagent的local/SwitchyOptions.bak,然后导入

![](/image/图/chrome_goagent_08.png)
![](/image/图/chrome_goagent_09.png)

**Finally，当你需要科学上网(Fan/Qiang)的时候，先运行goagent客户端中local/goagent.exe，然后在chrome浏览器中，点击小地球的图标，选择"GoAgent"代理，就可以了。**

![](/image/图/chrome_goagent_10.png)

>GoAgent主站：[https://code.google.com/p/goagent/](https://code.google.com/p/goagent/ "https://code.google.com/p/goagent/")
>goagent客户端3.1.18[6.16新]（[百度网盘下载](http://pan.baidu.com/s/190yiq)）
