---
layout: post
title: GoAgent与AutoProxy故障解决
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

起因是需要翻墙上twitter，用的是GoAgent加AutoProxy，但好长时间没上，现在居然上不了了。

- 第一步：解决GoAgent的ssl证书问题
也不清楚从哪一版开始需要手工导入证书到浏览器，可能一开始就需要吧，只是自己不知道。
火狐“选项”-->高级-->证书-->查看证书-->导入-->选择“GoAgent目录/Local/certs”

- 第二步：解决AutoProxy插件的订阅源问题
订阅源是AutoProxy翻墙名单的来源，之前添加完订阅源是可以看到规则列表的，还可以编辑规则，
最近更新了火狐，发现规则列表是空的，没办法手工添加规则，这是比较麻烦的事儿。假设某个
站需要翻墙，不能编辑规则的话，只能先打开失败下，然后选择“对该站启用代理”AutoProxy才
会记忆该站。
解决的办法是安装修改版本的AutoProxy插件，这个版本的插件是针对AutoProxy的安全修改，开
源的，代码托管在[github][1]上，下载链接[点这里][2]。

[1]: https://github.com/agunchan/autoproxy   "AutoProxy修改版GitHub地址"
[2]: http://fxthunder.com/blog/archives/2866 "AutoProxy修改版下载链接"
