---
title: 如何下载github项目中的一个子文件或者文件夹
categories: tools
tags:
  - github
  - TortoiseSVN
date: 2020-10-22 12:44:50
description: 单纯的只下载GitHub项目中的某个文件办法。
sticky:
cover:
---

<!-- 脑图区域，显示文章结构脉络。 -->


## 1. 前言🗡  
<!-- 写本文的缘由 -->
学习git的时候，了解到从GitHub上下载整个项目命令非常简单，只需要git clone url就可以了。但是有时候我们只需要项目中的某个文件或者子文件夹，怎么办呢？在Windows上装个 **TortoiseSVN** 就可以实现.

## 2. 正文🔪  
<!-- 分析，有理有据，思维清晰 -->
### 2.1 下载软件  

🗡点击下载：[TortoiseSVN-1.14.0.28885-x64-svn-1.14.0.msi.](https://osdn.net/projects/tortoisesvn/storage/1.14.0/Application/TortoiseSVN-1.14.0.28885-x64-svn-1.14.0.msi/)
直接安装即可，安装可以选择路径，安装完成后，右键点击桌面，里面有SVN checkout的选项，点击进入。

### 2.2 链接修改  

+ 进入GitHub项目，点击到你要下载的文件夹，复制对应文件地址栏的地址

+ 将地址中的 /tree/master/ 换成 /trunk/即可  

### 2.3 效果图  
![20201022125028](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201022125028.png#img-radius)

## 3. 总结🚩  
<!-- 回顾总结，给出理解 -->
除此之外，还可以利用github的对应插件，如Octotree，是一个吸附的树状目录，对应文件有链接，但是可能链接失效。

以上就是 <font color=red>**zero**</font> 今天要分享的内容，欢迎大家留言评论，提出你的见解，我们一起学习进步！