---
title: 使用 PicGo 上传图片到 SM.MS 图床
date: 2021-02-14 22:47:47
tags: 
    - 转载
categories:
    - 问题记录
---

昨天，轻狂测试了一下[使用 PicGo+GitHub 打造最稳定可靠的免费图床](https://www.flighty.cn/html/tutorial/20200217_576.html)，但是由于众所周知的原因，GitHub在国内的访问速度有点慢，可能会影响页面的加载速度。那么，今天轻狂就来试试 SM.MS 图床。

<!-- more -->

**一、SM.MS 图床**

其实轻狂之前就注册了 SM.MS 图床，只是测试了一下速度，并没有正式使用，注册账号我就不多说了，自己去 SM.MS 上注册就行了，地址：https://sm.ms/ 

登录之后，我们要到 https://sm.ms/home/apitoken 生成一个 Secret Token 以备后用。

**二、PicGo 设置**

到 PicGo-插件设置里面搜索一个插件：picgo-plugin-smms-user，点击安装。

注意：安装这个插件需要用到 Node.js，没有安装的小伙伴要先安装一下，地址：https://nodejs.org/zh-cn

点击图床设置-SM.MS-登录用户（不是那个SM.MS图床，那个接口已经失效了），把上面我们申请到的 Secret Token 填写进去点击 确定 保存，设为默认图床即可体验啦。

**总结：**
经过测试，目前我用的网络环境下，SM.MS图床，要比 Github 速度快一些。

原文链接：https://www.flighty.cn/html/tutorial/20200218_579.html