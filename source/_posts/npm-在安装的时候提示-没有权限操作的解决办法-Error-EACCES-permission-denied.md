---
title: npm 在安装的时候提示 没有权限操作的解决办法 Error EACCES permission denied
date: 2021-02-14 22:27:45
tags: 
    - NPM
    - 转载
categories:
    - 问题记录
---

在安装插件的时候出现这样的错误，权限不够，是因为之前用 `root` 用户进行了局部安装npm包的操作，留下所属权为 `root` 的文件，导致普通用户无法访问 `root`的文件内容。

<!-- more -->

## 报错日志如下：

![image](https://img-blog.csdnimg.cn/20190326155116447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

```bash
npm ERR! path /Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall open
npm ERR! Error: EACCES: permission denied, open '/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c'
npm ERR!  { [Error: EACCES: permission denied, open '/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c']
npm ERR!   cause:
npm ERR!    { Error: EACCES: permission denied, open '/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c'
npm ERR!      errno: -13,
npm ERR!      code: 'EACCES',
npm ERR!      syscall: 'open',
npm ERR!      path:
npm ERR!       '/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c' },
npm ERR!   isOperational: true,
npm ERR!   stack:
npm ERR!    'Error: EACCES: permission denied, open \'/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'open',
npm ERR!   path:
npm ERR!    '/Users/Kyle/.npm/_cacache/index-v5/d8/1f/98ab242d0cbad080828ef3e3f4b864c25e506a719121c293fec810b14b3c',
npm ERR!   parent: 'findup-sync' }
npm ERR! 
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR! 
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator (though this is not recommended).

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/Kyle/.npm/_logs/2019-03-26T07_00_54_812Z-debug.log
```

## 错误原因：

找到报错的文件，会看到它的所有者是 `root`。
之前用 `root` 进行了局部的安装操作，导致这个文件的所有者是 `root` ，还包括 `.npm` 文件夹下部分文件夹的所有权，也是 `root`，普通用户当然就无权访问了。就会报权限错误。

![image](https://img-blog.csdnimg.cn/20190326155214466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

## 解决办法

就是把用户目录下的 `.npm` 文件夹所有权都改成当前用户即可。
比如：当前用户名为 `Kyle`

```bash
sudo chown -R Kyle ~/.npm 
```

执行后输入 root 密码，文件所属已改为当前用户了，再执行操作就不会出现了。

![image](https://img-blog.csdnimg.cn/20190326155245200.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)
![image](https://img-blog.csdnimg.cn/20190326155233351.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0tpbUJpbmc=,size_16,color_FFFFFF,t_70)

## 注意事项

初学者在用 terminal 操作 npm 的时候，经常会混用 `root` 和 普通用户。
由于分不清全局安装和局部安装的区别，才会出现乱用 `root` 的问题。

一般来说，全局安装就用 `root` 安装。
局部安装就用普通用户。

原文链接：https://blog.csdn.net/kimbing/article/details/88821182