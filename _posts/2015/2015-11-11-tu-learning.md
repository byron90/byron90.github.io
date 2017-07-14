---
layout: post
title: 吐学
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

边吐槽，边学习，故名“吐学”。
主要记录各种小坑、小Bug带来的思考和积累。
持续更新中......

*******************************************************
**2015-11-11   jquerymobile listview demo的一个bug**

listview中的一个a标签，点击后，会将被跳转的页面嵌入当前页面下。

解决办法：a标签添加data-ajax="false" 属性

*******************************************************
**2015-11-03   c的strncmp的函数**

为了防止访问越界，往往会忽视两个字符串只是前缀相等的情况

*******************************************************
**2015-11-02   HTML的编码**

HTML的charset=gb2312并不是说整个HTML页面都是gb2312编码，只是中间有gb2312的中文而已，比如qq.com

*******************************************************
**2015-9-26   解决windows10 开始菜单、系统状态图标不可用**

打开powershell，输入命令：
	Get-AppxPackage | % { Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppxManifest.xml" -verbose }
等待命令执行完毕，不用重启，问题即解决。

这条命令是将windows的Appx全部重新注册。

From Baidu：http://www.cr173.com/html/66828_1.html

*******************************************************
**2015-1-22 Raspbian上安装mongodb**

懒人模式：https://github.com/svvitale/mongo4pi

git clone的时候费点时间而已，clone后直接./install.sh，分分钟搞定，不用自己编译一堆东西喽

*******************************************************
**2015-1-22 Raspbian上的goagent**

在raspbian上goagent的配置与win8的一样，但用的时候报错：

Your client does not have permission to get URL /gh/ from this server，

请空自定义的hosts后，问题解决。。。。

*******************************************************
**2014-11-04 windows的ssh key管理**

创建一个rsa key，用在git操作上，必须将2个key文件放在.ssh下，替换之前的文件？

必须在git bash下操作git，在cmd下key无效？

*******************************************************
**2014-11-03 xcode6下，为UIViewController子类增加自定义init函数**

UIViewController类树复杂，一旦自定义init函数，需要同时实现三个init函数，缺少任一个都会报错：

    required init(coder aDecoder: NSCoder!) {
        super.init(coder: aDecoder)
    }

    override init(nibName nibNameOrNil: String!, bundle nibBundleOrNil: NSBundle!) {
        subview = UIView()
        super.init(nibName: nil, bundle: nil)
    }

    convenience override init() {
        self.init(nibName: nil, bundle: nil)
    }

*******************************************************
**2014-06-13 C++ 迭代器的++操作**

ite为某迭代器，ite++与++ite，在不牵扯到赋值时（如iteNew=ite++），是否等价？

答：不等价，ite++会产生copy操作，++ite不会，后者效率更高。

A ++p returns a reference top, whereas p++ must return a copy ofpholding the old value. Thus, for
more complicated iterators,++p is likely to be more efficient than p++. 摘自《The C++ Programming Language》
