---
layout: post
title: win8下连接iphone后itunes无反应的解决办法 
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

用腻了ios6，想试试ios7，备份iphone的时候有问题了：iphone接到win8上，itunes没反应？

有一段时间没有备份过iphone，最近一次是在2014年春节，上次是很顺利地识别到手机，所以故障原因无从查起了。

google了一大通，终于找到一个靠谱的方案：

1. iphone接PC上；
2. win+R --》 输入“compmgmt.msc”进入设备管理器；
3. 找到“Apple iPhone”，选择更新驱动程序；
4. 更新驱动的方式选择“浏览计算机查找驱动程序”；
5. 点击“从磁盘进行安装”，驱动所在路径为：C:\Program Files\Common Files\Apple\Mobile Device Support\Drivers\usbaapl.inf；

[原帖][1]给出四种方案，这个问题对应的适配这么多，估计是个普及的bug。

[1]: http://www.cnblogs.com/yipu/archive/2013/05/29/3105365.html "Win8下iTunes无法连接iPhone版本的解决方法"
