---
title: butterfly教程（一）入门安装
categories: butterfly教程
tags:
  - hexo
description: 基于hexo框架搭建的博客，在本地显示博客主题最原始的效果！
date: 2020-10-19 22:34:39
sticky: 1 
---
## 前言 [Hexo](https://hexo.io/zh-cn/docs/)
> + **官方介绍**：Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
> + 你不需要什么编程代码的知识储备，只要按照步骤来就可以搭建一个免费的属于子自己的博客网站。

# 第一篇 入门安装
![20201019224946](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019224946.png#img-radius)  

## 1. 准备事项  
> + 下载安装git, Node.js：**[Git安装](https://blog.csdn.net/qq_36292543/article/details/109021023)** 、**[ Node.js安装](https://blog.csdn.net/qq_36292543/article/details/109021779)**  
> + 准备一个Github账号
> * 修改编辑器：Vs code，**[官网下载](https://code.visualstudio.com/)**
> + 学习Markdown基本语法，**[菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)**
> + 安装Hexo框架：**[安装教程](https://yafine-blog.cn/posts/4ab2.html)**
> + 选择Hexo的博客主题：**[模板市场](https://hexo.io/themes/)**  

**闲言碎语：**以上操作没啥好说的，不会的自行百度谷歌一下。  

## 2. 基础配置  

### 2.1 应用主题  
先把意向的主题下载好，很多好看的主题都在GitHub仓库，自己留意物色好，进行克隆下载：
``` bash
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly 
```
把下载好的主题放到hexo框架的文件夹：<kbd>themes</kbd>中，修改根目录下的配置文件_config.yml，把主题改为： butterfly 。
```bash
theme: butterfly #landscape  
```
这样就替换好主题了，但是还不能运行，缺少对应注意的渲染器。  

### 2.2 安装渲染器  
hexo初始化后，默认沒有安装 pug 以及 stylus 的渲染器，所以：  
```bash
npm install hexo-renderer-pug  hexo-renderer-stylus --save
```

### 2.3 平滑升级  
各个主题功能都在不断完善中，所以版本迭代可能会覆盖自己的配置，所有就了以下设置，可以更安全的升级。
> + hexo v5.0以上，把主题文件夹中的 _config.yml 复制到 Hexo 根目下，重新命名 _config.butterfly.yml。
> + 以后只需要在 _config.butterfly.yml进行配置就行。  

**说明：**
Hexo会自动合并主题中的_config.yml和 _config.butterfly.yml的配置，如果存在同名配置，会使用_config.butterfly.yml的配置，其优先度较高。  

## 3. 预期效果  
前期工作完成后，接下来就可以启动本地服务了:  
```bash
hexo clean;hexo g;hexo s
```
此时没有导航，只有一个初步的框架如：
![20201020002125](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201020002125.png#img-radius)

{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,green larger %}