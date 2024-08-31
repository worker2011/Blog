---
title: 我艹，这么多良心软件都在GitHub上，你却打都打不开？
date: 2024-01-25 12:54:47
tags:
---

# GitHub为何物？

Git是一个代码管理工具。GitHub上自带Git，可以上传代码，上面囤积了不少高质量开源项目，比如[你谷的CYaRon](https://github.com/luogu-dev/cyaron)。

<!--more-->

# 有啥缺点不？

有啊，国内裸网打不开……~~设计墙这东西的那个S13出来挨打！！！~~

# 咋办呢？

## 挂梯子

愁，是一堵矮矮的墙。我在这头，GitHub在那头（doge

那你架个梯子把墙翻过去不就得了？

### 优点

简单粗暴，能够访问其它站点

### 缺点

1. 大部分梯子都要付钱
2. 免费的梯子不好找，一般还不太稳定
3. **外挂梯子是违法行为**

![](https://s2.loli.net/2024/07/23/l4ZNXhWIinYKFdz.png)

## Watt Toolkit

[在这里~](https://steampp.net/)

### 优点
1. 服务比较稳定
2. 免费
3. 由正规公司开发，通过了微软的审核，不会逝
4. 能加速部分其他站点，但像谷歌全家桶这样的就算了……

### 缺点
1. 还是可能会崩

{% folding blue:: 讲点别的——Watt Toolkit什么能加速？ %}
Watt Toolkit什么能加速？

这得说到GitHub为什么访问慢。其实GitHub在日本、韩国这些地方有服务器，离咱们近，自然访问快。但GitHub配置的DNS（有多个服务器时帮你选择服务器的服务）比较奇葩，会把你导到美国的服务器去，很容易就TLE了。

而另一个关键是Hosts文件，你可以在此修改一些网络配置。比如以`站点地址 服务器IP`的格式让所有访问这个地址的请求在本机上转移到你指定的服务器。所以我们拿到日韩的服务器IP地址，再修改Hosts就可以实现加速了。

Watt Toolkit其实就是实现这个过程的自动化脚本，但有图形化界面。~~不会的可以看[这篇简介](https://www.cnblogs.com/leo2011/p/17938779)。~~
{% endfolding %}

## Steamcommunity 302

[这里~](https://www.dogfight360.com/blog/knowledge-base/steamcommunity_302_manual/)。

### 优点

1. 比较稳定
2.免费
3. 能加速一些别的

### 缺点

1. Watt Toolkit与这个互相不兼容，即不能同时开启两个
2. ~~我个人认为~~UI有那么亿点点简陋……

## FastGitHub

~~原GitHub库已消失，只能在[这里找到](https://github.com/ylong52/fastgithub_win)~~

### 优点

1. 纯粹
2. 如果加速不成功能显示报错信息
3. 与上面两个兼容

### 缺点

1. 名字就能看出只加速GitHub
2. 这项目本身就TM托管在GitHub上……~~这作者有脑子，但不多。~~

# 总结

一张表，拿走：

| 方式 | 网址 | 优点 | 缺点 |
| :---: | :---: | :---: | :---: |
| 挂梯子 | - | 能访问所有外国站点，简单粗暴 | **违法**、付费、免费的不稳定、有些加速器的“智能路由模式”非常智障 |
| Watt Toolkit | [https://steampp.net/](https://steampp.net/) | 能加速一些别的、稳定、安全 | 还是可能会崩 |
| Steamcommunity 302 | [https://www.dogfight360.com/blog/knowledge-base/steamcommunity_302_manual/](https://www.dogfight360.com/blog/knowledge-base/steamcommunity_302_manual/) | 同Watt Toolkit | 与Watt Toolkit不兼容、UI比较丑 |
| FastGitHub | 已消失，但可以在[https://github.com/ylong52/fastgithub_win](https://github.com/ylong52/fastgithub_win)下载 | 纯粹、能显示报错信息，与上面两个兼容 | 只能加速GitHub、原GitHub项目已消失 |
