---
title: npm 速度过慢的解决方案
date: 2021-02-14 22:26:55
tags: 
    - NPM
    - 转载
categories:
    - 问题记录
---

因为npm连接的数据源网站太慢，可以使用淘宝提供的npm数据源，

<!-- more -->

```bash
npm config set registry https://registry.npm.taobao.org
```

---

使用NPM（[Node.js](http://lib.csdn.net/base/nodejs)包管理工具）安装依赖时速度特别慢，为了安装Express，执行命令后两个多小时都没安装成功，最后只能取消安装，笔者20M带宽，应该不是我网络的原因，后来在网上找了好久才找到一种最佳解决办法，在安装时可以手动指定从哪个镜像服务器获取资源，我们可以使用阿里巴巴在国内的镜像服务器，命令如下：

```
npm install -gd express --registry=http://registry.npm.taobao.org
```

只需要使用–registry参数指定镜像服务器地址，为了避免每次安装都需要`--registry`参数，可以使用如下命令进行永久设置：

```
npm config set registry http:/bash
```

```
换了国内镜像，安装速度就很快了。
```

---

```
npm install cnpm -g
```

或者

```
npm install cnpm -g --registry=https://registry.npm.taobao.org
```

应该都是可以的额。
cnpm安装后，直接用cnpm解决被墙的问题。
或者直接配置registry为淘宝的registry,后面还是使用npm

来源网址：https://www.cnblogs.com/sddai/p/9388261.html