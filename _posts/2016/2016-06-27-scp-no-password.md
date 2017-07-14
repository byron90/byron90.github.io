---
layout: post
title: scp无密码传输  
---

{{ page.title }}
================
<p class="date">{{ page.date | date_to_string }} - ByronTech</p>

> 问题场景：君艺系统 raspberry pi 配置

* `ssh-keygen -t rsa`  本机产生密钥
* 添加到服务器的 ~/.ssh/authorized_keys 
* 修改 authorized_keys 权限为 700
* 本机 `scp a.txt user@server` 时，每次仍需要输入密钥对应的密码，应该与本机操作系统有关，因为OSX下是免密的
* Linux下可用 ssh agent来缓存密码，之后的ssh 和 scp操作就不需要密码了：  
1) `ssh-agent bash`  
2) `ssh-add`   输入id_rsa对应的密码
* OSX下有 keychain 管理密钥，相当于 ssh agent 的替代品

* 参考：[Enter SSH passphrase once - Ask Ubuntu][ref-link]

[ref-link]:  http://askubuntu.com/questions/362280/enter-ssh-passphrase-once