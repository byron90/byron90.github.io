---
layout: post
title: miwifi 双信道引发的局域网访问故障
---


{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

> 问题场景：在 miwifi 搭建的局域网中，苹果手机访问君艺系统时，会偶现无法访问的现象，而安卓手机和电脑端没有此问题

* 定位过程：

	1) `nginx` 是否有问题：观察了下 nginx 日志，iPhone 无法访问时 nginx 没有收到访问请求，查看了下相关配置，可以排除是 nginx 的问题；

	2) `miwifi` 是否有问题：miwifi 没有办法查看日志 ，有个上传日志的选项，但是是给小米工程师看的，蛋疼了。后台也只有笼统的曲线，而且数据也不及时更新，这个方向只能挂起；

	3) `Raspberry Pi` 是否有问题：在树莓派上用 `tcpdump` 抓包，发现三次握手阶段就失败了，有很多 tcp 重传包：

	![][image-1]
	这就解释了为什么 nginx 没有访问日志的现象了，但还不能进一步确定是不是 Raspberry Pi 的问题，无从查起；

	4) 反思了下，在 iPhone 无法访问君艺系统，也就是 Raspberry Pi 时，iPhone 访问外网是没有问题的，因此，问题很有可能出在了局域网中 iPhone 到 Raspberry Pi 这一段物理链路上，因此还要回到 miwifi ，查看不能访问时，iPhone 和 Raspberry Pi 的连接状态有啥异常；

	5) 在 miwifi 的 App 上，发现一个不同点：无法访问时，iPhone 是 5G 信道接入，而 Raspberry Pi 是 2.4G 信道接入，出现这个现象是因为 miwifi 开启了“双频合一”功能，而 iPhone 会自动选择 5G 信道接入。

	![][image-2]
	这就造成了 iPhone 与 Raspberry Pi 不在同一个信道上，miwifi ，也有可能是 iOS  没有彻底地实现这两种链路的互通（具体是谁的问题，找个 Android 机做参照测试就知道了），导致了 tcp 协议层面上的丢包重传；
* 解决办法：关掉“双频合一”功能，关掉 5G 信道，全部使用 2.4G 信道

[image-1]:	http://ov2ixeq0q.bkt.clouddn.com/miwifi-wireshark-pi.png
[image-2]:	http://ov2ixeq0q.bkt.clouddn.com/dreamart-error-fix.png
