---
layout: post
title: 使用webpack构建单页应用  
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

> 问题场景：[请问在WEUI项目中所有页面都在首页中，如何分开呢][ref-link3]

* 尝试从前端的原始森林走出，使用构建框架
* 调试时不直观，需要重新构建代码
* osx Cannot find module 'webpack' --> `npm install`
* docker-ubuntu install webpack : Package require os(darwin) not compatible with your platform(linux)

* 参考：
[webpack 单页面应用实战][ref-link1]
[weui的router样例][ref-link2]



[ref-link1]:  https://segmentfault.com/a/1190000005866410
[ref-link2]:  https://github.com/progrape/router/tree/dev/src/example
[ref-link3]:  https://github.com/progrape/router/issues/16