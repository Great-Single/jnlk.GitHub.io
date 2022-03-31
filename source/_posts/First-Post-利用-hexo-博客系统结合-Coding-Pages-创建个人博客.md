---
title: First Post - 利用 hexo 博客系统结合 Coding Pages 创建个人博客
date: 2021-02-14 20:14:35
tags: 
    - hexo
    - 原创
categories:
    - 行动记录
---
> Hello World!

这是我在博客中写下的第一句话，我想，这应该是我第一篇关于应用方面的正式教程。

<!-- more -->

利用 Coding Pages 配合 hexo 框架搭建博客，好处有这么几条：

1. 可以很方便地配合 Coding 的 Cloud Studio 服务；
2. 访问速度快，且有腾讯云支持，自定义功能更高，且备案等流程更为便捷；
3. 无需自建服务器，且能轻松进行自动化构建。

## 在 Coding 中快速搭建 hexo 个人博客

Coding 静态网站部署原名为 `Coding Pages`，和 Github 上的“Github Pages”差不多一样。

而 hexo 则是一款基于 `Node.js` 的静态博客框架，且使用 `Markdown` 解析文章。

两者结合使用十分简单，而且方便配置。

下面，教程开始。

---

## 步骤一：创建 CODING 项目

1. 在 Coding 中新建项目；
2. 选择并创建 DevOps 项目；

![img](https://help-assets.codehub.cn/enterprise/20201027151849.png)

3. 填写项目名称后，点击 `完成创建 `按钮，即可完成项目创建。

## 步骤二：创建静态网站

1. 进入项目面板以后，在左侧栏找到 `持续部署 - 静态网站`。

> 注意，首次使用 Coding 的静态网站服务是需要进行实名验证的，并且要在腾讯云后台进行一些操作。

![img](https://help-assets.codehub.cn/enterprise/20201027152018.png)

2. 点击 `新建静态网站`，进入表单，选择如图所示，当然了，网站名称自己随便填写就可以了。部署的节点可以选择香港，海外网站无需备案。

![img](https://help-assets.codehub.cn/enterprise/20201027152337.png)

3. 表单填写完成后点击 `确定` 即可提交。

## 步骤三：等待部署

1. 创建成功后，耐心等待静态网站部署完成，状态会由 `部署中` 变为 `部署成功`。

![img](https://help-assets.codehub.cn/enterprise/20201027160113.png)

2. 部署成功以后，Coding 静态网站自动给你一个 `访问地址`，复制粘贴到链接栏即可访问。至此，部署的流程全部完成。

![img](https://help-assets.codehub.cn/enterprise/20201027160302.png)