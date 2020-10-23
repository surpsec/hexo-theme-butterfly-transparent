---
title: 给 Markdown 里的图片增加样式
categories: 知识储备
tags:
  - Markdown
description: MD中添加各种样式，提高博客的阅读体验。
---
<!-- 脑图区域，显示文章结构脉络。 -->


## 1. 前言🗡
<!-- 写本文的缘由 -->
最近看着用markdown写的文章，发现里面的文章配图很尖锐，很是不美观，这明显影响了我博客游客的阅读体验嘛！！！

所以，作为强迫症患者，这时候忍不了。改！

## 2. 正文🔪  
### 2.1 修改图片大小
+ 使用html中的img标签
``` html
<img src="链接" alt="如果无法显示图像，浏览器将显示替代文本" width="500px" height="313px" ><img>
```
原图：
![20201019085923](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019085923.png)
修改：
<img src="https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019085923.png" width="auto" height="60px"></img>

+ 直接在MD后加修改样式  
格式：链接空格=100x50，如下：  

```  
![20201019085923](https://img-blog.csdnimg.cn/img_convert/ff301a4ef99771d53bdbc07c63c6747b.png =400x300)
```
此方法可在csdn中使用，有效！其他md编辑器好像都不起作用！

+ 使用自定义样式

**见2.2 修改图片圆角**

### 2.2 修改图片圆角
添加一个自己的css文件，确保这个文件被引用，然后在 CSS 里定义“src 里包含字符串 #img-radius”的规则,如我的图片圆角：
``` css
img[src*="#img-radius"] {
    border-radius: 9px;
}
```
然后直接在图片链接后面，添加#img-radius，就有圆角效果了：
![20201019085923](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019085923.png#img-radius)  

## 3.总结 🚩

从目前了解的方法，常用的就html和自定义样式，各有各的好，自选！

更多请看官方文档： [MDN 文档](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)

注意：可以选择中文模式阅读，在右上角选择语言。

参考链接：[how-to-style-images-with-markdown](https://www.xaprb.com/blog/how-to-style-images-with-markdown/)

**<font color=green size=5px>**
  以上就是以上就是 zero以上就是今天要分享的内容，欢迎大家留言评论，提出你的见解，我们一起学习进步！💪💪💪</font>
