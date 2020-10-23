---
title: butterfly教程（二）基本功能
categories: butterfly教程
tags:
  - hexo
description: 教程（一）已经搭建好博客框架，接下来本篇内容就是手把手教你把博客的基本的功能完善！
---
## 前言
一个博客网站，主要是用来发表博客，记录笔记心得的心灵圣地。所以搭建好hexo框架后，就是要明确你的博客需要哪些功能，就能进一步添加自己需要的功能，满足写作需求。

# 第二篇 基本功能  

![20201020161326](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201020161326.png#img-radius)  

## 1.完善导航  

### 1.1 创建各个页面  

+ 1.1.1 创建页面  

需要创建的基本页面有：tags、categories、link、about，创建命令如下：
``` bash
hexo new page tags
```
**注意：**新创建页面对应的md文件，开头必须指明类型，如type: "tags"，默认状态下已经包含以下类型：  
``` bash
title:
date:
```

其他配置添加说明：[Post Front-matter](https://demo.jerryc.me/posts/dc584b87/#Page-Front-matter)



+ 1.1.2 友链页面  

在Hexo博客根目录中的source文件夹下创建<kbd>_data</kbd>文件夹，里面再创建一个link.yml文件，格式如下：
``` bash
- class_name: 友情鏈接
  class_desc: 那些人，那些事
  link_list:
    - name: JerryC
      link: https://jerryc.me/
      avatar: https://jerryc.me/image/avatar.png
      descr: 今日事,今日畢
    - name: Hexo
      link: https://hexo.io/zh-tw/
      avatar: https://d33wubrfki0l68.cloudfront.net/6657ba50e702d84afb32fe846bed54fba1a77add/827ae/logo.svg
      descr: 快速、簡單且強大的網誌框架

- class_name: 網站
  class_desc: 值得推薦的網站
  link_list:
    - name: Youtube
      link: https://www.youtube.com/
      avatar: https://i.loli.net/2020/05/14/9ZkGg8v3azHJfM1.png
      descr: 視頻網站
    - name: Weibo
      link: https://www.weibo.com/
      avatar: https://i.loli.net/2020/05/14/TLJBum386vcnI1P.png
      descr: 中國最大社交分享平台
    - name: Twitter
      link: https://twitter.com/
      avatar: https://i.loli.net/2020/05/14/5VyHPQqR6LWF39a.png
      descr: 社交分享平台
```
+ 1.1.3 各页面banner图
+ 首页  

主题配置文件， 搜索：index_img
```yml
index_img: https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg
```
  + 标签页等  

这里就不为每个标签设置banner了，设置成统一的banner图：
在hexo根目录下的source文件中，有各个导航页面的md文件，在里面头部加上：
``` md
top-img: https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg
```
+ 1.1.4 站点信息

hexo配置中，搜索：# Site
``` yml
title: 天择
subtitle: 'Zero' # 网页标签显示
description: '宁静以致远，焦躁是因为实力和成功有天大的差距，说明你的努力的汗水远远不够浇灌成功的花蕾！'
keywords:
author: Zero
language: zh-CN
timezone: ''  
```

+ 1.1.5 中文导航  

主题配置中，搜索：<kbd>menu:</kbd>
``` yml
menu:
  首页: / || fas fa-home
  归档: /archives/ || fa fa-inbox
  标签: /tags/ || fas fa-tags
  分类: /categories/ || fas fa-folder-open
  娱乐||fas fa-list:
    - 音乐 || /musics/ || fas fa-music
    - 电影 || /movies/ || fas fa-video
    - 书籍 || /books/ || fas fa-book
    - 图库 || /gallery || fas fa-photo-video 
  友链: /link/ || fas fa-link
  打赏: /reward/ || fas fa-credit-card
  关于: /about/ || fas fa-heart
```

+ 1.1.6 awesome图标  

Awesome 字体为您提供可缩放矢量图标,它可以被定制大小、颜色、阴影以及任何可以用CSS的样式。[fontawesome中文网](http://www.fontawesome.com.cn/examples/#basic)，这里展示博客常用的几个：
> 首页： fas fa-home<i class="fas fa-home" aria-hidden="true"></i>  
归档： fa fa-inbox<i class="fa fa-inbox" aria-hidden="true"></i> 
标签： fas fa-tags<i class="fas fa-tags" aria-hidden="true"></i>  
分类： fa fa-folder-open<i class="fa fa-folder-open" aria-hidden="true"></i>  
音乐： fas fa-music <i class="fas fa-music" aria-hidden="true"></i>  
电影： fas fa-video <i class="fas fa-video" aria-hidden="true"></i>  
书籍： fas fa-book  <i class="fas fa-book" aria-hidden="true"></i>  
图库： fas fa-photo-video  <i class="fas fa-photo-video" aria-hidden="true"></i>  
友链： fas fa-link <i class="fas fa-link" aria-hidden="true"></i>  
打赏： fas fa-credit-card <i class="fas fa-credit-card" aria-hidden="true"></i>  
爱心： fas fa-heart <i class="fas fa-heart" aria-hidden="true"></i>  


### 1.2 搜索系统  
+ 安装插件  

``` bash
npm install hexo-generator-search --save
```
+ 主题配置  

``` bash
local_search:
  enable: true
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}" # if there are no result
```

## 2. 文章相关  

### 2.1 主页文章  

+ 置顶  

hexo-generator-index从 2.0.0 开始，已经支持文章置顶功能。你可以直接在文章的front-matter区域里添加sticky: 1属性来把这篇文章置顶。数值越大，置顶的优先级越大。

+ 概要节选  
主题配置中，搜索：index_post_content:  

``` yml
index_post_content:
  method: 2
  length: 500 
```
> + 1： description： 只显示description
> + 2：both： 优先选择description，如果没有配置description，则+ 显示自动节选的内容
> + 3：auto_excerpt：只显示自动节选
> + 4：false： 不显示文章内容    

说明：这里的1234对应代码中method的值。  

+ 隐藏文章  

文章的markdown文档上,在Front-matter添加hide：
``` md
hide: true
```
隐藏特定分类中的文章 :在 Hexo 的 _config.yml 中可以通过ide_categories 选项设置隐藏某个分类下的文章，例如：
``` yml
hide_categories:
  - categorie1
  - categorie2
```
若隐藏无效，请装插件hexo-generator-indexed或者hexo-hide-posts.  

+ 404页面  

主题配置中，搜索：# A simple 404 page ，把enable设为true
error_404:
  enable: true
  subtitle: 'Page Not Found'
  background: https://i.loli.net/2020/05/19/aKOcLiyPl2JQdFD.png

### 2.2 文章详情  

+ 2.2.1 文章封面  

文章的markdown文档上,在Front-matter添加cover,并填上要显示的图片地址。
如果不配置cover,可以设置显示默认的cover.如果不想在首页显示cover,可以设置为false。
主题配置中，搜索：<kbd>cover:</kbd>  

``` yml
cover:
  # 是否显示文章封面
  index_enable: true
  aside_enable: true
  archives_enable: true
  # 封面显示的位置
  # 三个值可配置 left , right , both
  position: both
  # 当没有设置cover时，默认的封面显示
  default_cover: 
   - https://tva3.sinaimg.cn/large/9bd9b167gy1fwsfhi3x9vj21hc0u0hc0.jpg
```
说明：当配置多张默认图片时,会随机选择一张作为cover。

+ 2.2.2 文章meta信息  

主题配置中，搜索：<kbd>post_meta:</kbd>
``` yml
post_meta:
  page:
    date_type: both # created or updated or both 主页文章日期是创建日或者更新日或都显示
    date_format: relative # date/relative 显示日期还是相对日期
    categories: true # true or false 主页是否显示分类
    tags: true # true or false 主页是否显示标籤
    label: true # true or false 显示描述性文字
  post:
    date_type: both # created or updated or both 文章页日期是创建日或者更新日或都显示
    date_format: relative # date/relative 显示日期还是相对日期
    categories: true # true or false 文章页是否显示分类
    tags: true # true or false 文章页是否显示标籤
    label: true # true or false 显示描述性文字
```
说明：page中的配置：主页文章列表中的，post中的配置：文章详情页中的。

+ 2.2.3 代码优化  

主题配置文件, 搜索：# Code Blocks (代碼相關)：

```bash
highlight_theme: mac  # 高亮样式
highlight_copy: true  # 代码复制
highlight_lang: true  # 显示代码语言
highlight_shrink: false # 代码框展开、关闭
code_word_wrap: false  # 代码换行
```
其他：[自定义代码配色](https://demo.jerryc.me/posts/b37b5fe3/#Highlight)

+ 2.2.4 评论系统  

主题配置文件，搜索：# Comments System，使用valine：
``` bash
  use:
  - Valine
  lazyload: true
  count: true # Display comment count in top_img
```
搜索：# https://valine.js.org,添加appid和appkey的值:
```yml
  appId: 
  appKey: 
  lang: zh_CN 
```
注意：valline美化见第三篇

+ 2.2.5 toc目录  

主题配置中，搜索： # toc (目錄)
``` yml
  toc:
  enable: true
  number: true # 自动填写目录序号
  auto_open: false # 自动打开目录
```

+ 2.2.6 版权

主題配置文件，搜索：<kbd>post_copyright:</kbd>
``` yml
post_copyright:
  enable: true
  decode: false
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/
```

+ 2.2.7 打赏  

主题配置文件中，搜索：<kbd>reward:</kbd>
```yml
reward:
  enable: true
  QR_code:
    - img: /img/wechat.jpg
      link:
      text: 微信
    - img: /img/alipay.jpg
      link:
      text: 支付宝
```
说明：对于没有提供二维码的，可配置一张软件的icon图片，然后在link上添加相应的打赏链接。用户点击图片就会跳转到链接去。link可以不写，会默认为图片的链接。  

  + 分享  

``` yml
sharejs:
  enable: true
  sites: wechat,weibo,qq #facebook,twitter,
```

+ 相关文章  

主題配置文件中，搜索：<kbd>related_post:</kbd>
``` yml
related_post:
  enable: true
  limit: 6 # Number of posts displayed
  date_type: created # or created or updated 文章日期顯示創建日或者更新日
```
+ 下一篇按钮  

```yml
{% btn 'http://www.jerryc.me',下一篇,far fa-hand-point-right,green larger %}
```

## 3. 侧边栏设置
+ 头像  

主题配置中， 搜索：<kbd># Avatar (頭像)</kbd>
```yml
avatar:
  img: https://s.gravatar.com/avatar/d8fdf908ef4641679f024dcc89be406b?s=80&r=g
  effect: true # 頭像會一直轉圈
```
avatar头像链接：  [如何制作avatar头像](http://avatar.sisome.com/support/how-to-sign-up/)

+ 社交  

搜索：# social settings (社交圖標設置)，把注释打开，注意不显示可能被广告插件拦截了。
``` yml
social:
  fab fa-github: https://github.com/xxxxx || Github
  fas fa-envelope: mailto:2296582473@qq.com || Email
  fa fa-weixin: https://mp.weixin.qq.com/ || 公众号
  fa fa-weibo: https://weibo.com/u/6747699297/ || weibo
```
说明：社交推广，微博，微信，简书，小红书，知乎

+ rss  

输入以下命令安装 RSS 插件:  
```cmd
npm install hexo-generator-feed --save
```
根目录下的 _config.yml 文件，加入以下配置：
```yml
# rss订阅
feed:
  enable: true
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon: icon.png
  autodiscovery: true
  template:
```
主题目录下的 _config.yml 文件，设置 RSS 地址：
```yml
aside:
  enable: true
  mobile: false # display on mobile
  position: right # left or right
  card_author:
    enable: true
    description:
    button:
      icon: fa fa-rss
      text: 订阅RSS
      link: atom.xml
```

## 4. 右下角按钮

+ 简繁互换+ 阅读模式+ 夜间模式  

主题配置中， 搜索：translate: ，# dark mode ，readmode: 
将设置改为true即可。

## 5.footer设置
+ 站点起始时间  

主題配置文件，搜索：<kbd>footer:</kbd>
```yml
footer:
  owner:
    enable: true
    since: 2018
```
+ icp  

显示备案域名，主题配置文件，
```yml
ICP:
  enable: true
  url: http://www.beian.miit.gov.cn/state/outPortal/loginPortal.action
  text: 粵ICP備xxxx
  icon: /img/icp.png
```
## 5. 部署到github
+ 5.1 安装插件  

``` bash
npm install hexo-deployer-git --save
```

+ 5.2 hexo配置  

在deploy下指定仓库路径和部署的协议，具体配置如下：
``` yml
deploy:
  - type: git
    repo: https://github.com/GitACzero/GitACzero.github.io.git
    branch: master
```
url: http://GitACzero.github.io
## 6. 预期  
配置好本期教程后，网站的基本功能已经完善，其他就是一些美化的边边角角了。从这里就可以开始，在书写博客的大坑中越走越远了。

