---
title: butterfly教程（三）主题美化
categories: butterfly教程
tags:
  - hexo
---
## 前言  
博客框架都弄好了，接下来本篇内容就是一些美化方面的内容，以及MD书写的进阶操作。

# 第三篇 进阶+美化




+ 标签外挂
  + Note (Bootstrap Callout)

  https://demo.jerryc.me/posts/4aa8abbe/#Note-Bootstrap-Callout
  格式：
  ``` 
  {% note [class] [no-icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

``` 
{% note simple %}
默認 提示塊標籤
{% endnote %}

{% note default simple %}
default 提示塊標籤
{% endnote %}

{% note primary simple %}
primary 提示塊標籤
{% endnote %}

{% note success simple %}
success 提示塊標籤
{% endnote %}

{% note info simple %}
info 提示塊標籤
{% endnote %}

{% note warning simple %}
warning 提示塊標籤
{% endnote %}

{% note danger simple %}
danger 提示塊標籤
{% endnote %}






+ 标签隐藏（可选）
https://demo.jerryc.me/posts/4aa8abbe/#tag-hide

+ 多标签
https://demo.jerryc.me/posts/4aa8abbe/#Tabs
适用范围：步骤


{% tabs test4 %}
<!-- tab 第一個Tab -->
**tab名字為第一個Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有圖標 沒有Tab名字**
<!-- endtab -->

<!-- tab 炸彈@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}

+ 按钮
https://demo.jerryc.me/posts/4aa8abbe/#Button

使用：下一个教程指示

{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,blue larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,pink larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,red larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,purple larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,orange larger %}
{% btn 'http://www.jerryc.me',JerryC,far fa-hand-point-right,green larger %}

+ 随机背景

简单：
找到Butterfly主题文件的inject:处,在bottom处插入以下代码：
``` 
inject:
  head:
  bottom:
    - <script> let backimg =["url(/images/draw.JPG)","url(/images/life.jpg)","url(/images/idea.jpg)","url(/images/study.jpg)"];let index =Math.ceil(Math.random() * (backimg.length-1));document.getElementById("web_bg").style.backgroundImage = backimg[index]</script>
```
在backimg数组里替换自己想要的图片链接即可。


法2：
css：平滑过渡
#web_bg {
    background-image: linear-gradient(60deg, rgba(139, 222, 231, 0.35) 5%, rgba(139, 222, 231, 0.35)),url("https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg");
    animation:frams 600s linear infinite;
    transition-duration: 2s;
    transition-property: all;
    
}
@keyframes frams {
    0%,100%{
        background-image: linear-gradient(60deg, rgba(139, 222, 231, 0.35) 5%, rgba(139, 222, 231, 0.35)),url("https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg");
        background-image: url("https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg");
    }
    10%{
        background-image: url("/img/01.jpg");
    }
    40%{
        background-image: url("/img/02.jpg");
    }  
    70%{
        background-image: url("/img/03.jpg");
    } 
    85%{
        background-image: url("/img/04.jpg");
    } 
}

https://zfe.space/2020/10/13/2020-10-13/

+ 网站验证
https://demo.jerryc.me/posts/ceeb73f/#%E7%B6%B2%E7%AB%99%E9%A9%97%E8%AD%89

+ 分析统计
https://demo.jerryc.me/posts/ceeb73f/#%E5%88%86%E6%9E%90%E7%B5%B1%E8%A8%88

+ 广告
https://demo.jerryc.me/posts/ceeb73f/#%E5%BB%A3%E5%91%8A

+ 主题自带美化、特效设置
https://demo.jerryc.me/posts/ceeb73f/#%E8%87%AA%E5%AE%9A%E7%BE%A9%E4%B8%BB%E9%A1%8C%E8%89%B2

+ 主题背景色
主题配置中， 搜索：# Website Background (設置網站背景)
background: "#efefef"
这个是透明灰色

+ 自定义页面样式-外部挂载代码
https://blog.csdn.net/howareyou2104/article/details/106393184/
主题配置中， 搜索：
inject:
  head:
通常在head处挂载css代码，在bottom处挂载js代码，
css代码通常放在\Butterfly\source\css目录下，js代码放在\Butterfly\source\js目录下

我的挂载配置如下：
inject:
  head:
  - <link rel="stylesheet" href="/css/mystyle.css">
  bottom:

mystyle.css代码，如下：

/*1. 页面背景，设置的图片 */
#web_bg {
    background-image: linear-gradient(60deg, rgba(139, 222, 231, 0.35) 5%, rgba(139, 222, 231, 0.35)),url("https://ftp.bmp.ovh/imgs/2020/10/31b405a6432bdab6.jpg");
}
/* 2. 页脚背景 */
#footer {
    background: none;
}
/* 导航背景 */
#nav.fixed {
    background: rgba(255, 255, 255, 0.7)
}
/* 3. 主体页面透明 */
css .layout_page {
    opacity: 0.88;
}
main#content-inner.layout_page {
    border-width: 30px;
    padding-top: 20px;
    background-color: rgba(233, 241, 241, 0.5);
    box-shadow: 0px 5px 10px 2px #ffffff;
}
/* 4  设置banner底部阴影*/
header#page-header.full_page {
    box-shadow: 0 -80px 10px -2px #ffffff4d inset;
}
/* 5. 添加图标颜色 */
/* 哔哩哔哩 */
i.iconfont.icon-bilibili {
    color: red;
}
/* 归档 */
i.fas.fa-archive {
    color: mediumslateblue;
}

/* rss订阅 */
i.iconfont.icon-RSS {
    color: orange;
}

/* 邮件信封 */
i.fas.fa-envelope {
    color: darkorange;
}

/* aside icons color settings */
/* 历史 */
i.fas.fa-history {
    color: mediumturquoise;
}

/* 网站数据 */
i.fas.fa-chart-line {
    color: blue;
}

/* 6. 发布文章透明 */
#recent-posts>.recent-post-item {
    /* background-color: rgba(255, 254, 253, 0.432); */
    opacity: 0.8;
}

/* 7. 滚动条设置 */
/* 滚动条优化 ===============================================================*/
::-webkit-scrollbar {
    width: 4px;
    height: 4px;
}

::-webkit-scrollbar-track {
    background-color:rgba(55, 99, 106, 0.699);
    border-radius: 2em;
}

::-webkit-scrollbar-thumb {
    background-color: #fc0a33d5;
    background-image: -webkit-linear-gradient(45deg,
            rgba(198, 228, 28, 0.4) 25%,
            transparent 25%,
            transparent 50%,
            rgba(172, 156, 7, 0.4) 50%,
            rgba(248, 244, 19, 0.84) 75%,
            transparent 75%,
            transparent);
    border-radius: 2em;
}
::-webkit-scrollbar-corner {
    background-color: transparent;
}
::-moz-selection {
    color: #fff;
    background-color: #ec29f3;
}

+ 特效
 <!-- 1.气泡 -->
在主题js文件夹，打开main.js，最后增加如下代码：
// 气泡
function qipao() {
    $('#page-header').circleMagic({
        radius: 10,
        density: .2,
        color: 'rgba(255,255,255,.4)',
        clearOffset: 0.99
    });
}! function(p) {
    p.fn.circleMagic = function(t) {
        var o, a, n, r, e = !0,
            i = [],
            d = p.extend({ color: "rgba(255,0,0,.5)", radius: 10, density: .3, clearOffset: .2 }, t),
            l = this[0];

        function c() { e = !(document.body.scrollTop > a) }

        function s() { o = l.clientWidth, a = l.clientHeight, l.height = a + "px", n.width = o, n.height = a }

        function h() {
            if (e)
                for (var t in r.clearRect(0, 0, o, a), i) i[t].draw();
            requestAnimationFrame(h)
        }

        function f() {
            var t = this;

            function e() { t.pos.x = Math.random() * o, t.pos.y = a + 100 * Math.random(), t.alpha = .1 + Math.random() * d.clearOffset, t.scale = .1 + .3 * Math.random(), t.speed = Math.random(), "random" === d.color ? t.color = "rgba(" + Math.floor(255 * Math.random()) + ", " + Math.floor(0 * Math.random()) + ", " + Math.floor(0 * Math.random()) + ", " + Math.random().toPrecision(2) + ")" : t.color = d.color }
            t.pos = {}, e(), this.draw = function() { t.alpha <= 0 && e(), t.pos.y -= t.speed, t.alpha -= 5e-4, r.beginPath(), r.arc(t.pos.x, t.pos.y, t.scale * d.radius, 0, 2 * Math.PI, !1), r.fillStyle = t.color, r.fill(), r.closePath() }
        }! function() {
            o = l.offsetWidth, a = l.offsetHeight,
                function() {
                    var t = document.createElement("canvas");
                    t.id = "canvas", t.style.top = 0, t.style.zIndex = 0, t.style.position = "absolute", l.appendChild(t), t.parentElement.style.overflow = "hidden"
                }(), (n = document.getElementById("canvas")).width = o, n.height = a, r = n.getContext("2d");
            for (var t = 0; t < o * d.density; t++) {
                var e = new f;
                i.push(e)
            }
            h()
        }(), window.addEventListener("scroll", c, !1), window.addEventListener("resize", s, !1)
    }
}(jQuery);

// 调用气泡方法
qipao();

<!-- 波浪特效 -->
找到index.styl文件（css下的）粘贴进去（z-index看自己喜好调整）
// 波浪特效
.hans-container
  position: fixed;
  bottom: 0px;
  width: 100%;
  height: 120px;
  z-index: -1

把这段粘贴到主题配置文件bottom:选项里面去：
  bottom:
  - <div id="hans-bolang"></div>
  - <script src="https://api.vvhan.com/api/bolang"></script>


+ 圆角
/* 侧边栏圆角 */
#aside_content .card-widget{
    border-radius: 19px;
}
+ 阅读全文
https://blog.zhheo.com/p/8dc862fc.html

+ 微信公众号接收评论消息

+ 网站验证

+ 文章日历

+ 分析统计

+ 广告

+ 全局音乐电影壁纸
https://demo.jerryc.me/posts/507c070f/#%E6%8F%92%E5%85%A5Aplayer-html

插件
npm install --save hexo-tag-aplayer
在Hexo的配置文件中
aplayer:
  meting: true
  asset_inject: false

在主題的配置文件中，enable設為true和per_page設為true
# Inject the css and script (aplayer/meting)
aplayerInject:
  enable: true
  per_page: true

  把aplayer代碼插入到主題配置文件的inject.bottom去
  inject:
  head:
  
  <!-- 隐藏只剩箭头 -->
  - '<style type="text/css">.aplayer.aplayer-fixed.aplayer-narrow .aplayer-body:hover{left:0px !important}.aplayer.aplayer-fixed.aplayer-narrow .aplayer-body{left:-66px !important; opacity:0.5;}}</style>'  # APlayer吸底标签自动缩入
  <!-- css，歌词永久隐藏 -->
  aplayer-lrc{display: none!important;
  bottom:
    - <div class="aplayer no-destroy" data-id="000PeZCQ1i4XVs" data-server="tencent" data-type="artist" data-fixed="true" data-mini="true" data-listFolded="false" data-order="random" data-preload="none" data-autoplay="true" muted></div>

aplayer-fixed.aplayer-narrow .aplayer-body{left:-66px !important}</style>'  # APlayer吸底标签自动缩入

最後，如果你想切換頁面時，音樂不會中斷。請把主題配置文件的pjax設為true


+ 网站背景


+ 打字效果

+ 背景特效

+ 鼠标指针

2个方法使用，一是找到 themes\Butterfly\source\css 下创建 mouse.css 文件、输入以下内容：
从链接可以看出，使用了jsdeliver加速，放在图床上了。这个简单方便
``` css
/*鼠标样式*/
body,
html {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/Arrow.cur),
	auto !important;
}

a,
img {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*a标签*/
a:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*按钮*/
button:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*i标签*/
i:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*页脚a标签*/
#footer-wrap a:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*分页器*/
#pagination .page-number:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}

/*头部的导航栏*/
#nav .site-page:hover {
  cursor: url(https://cdn.jsdelivr.net/gh/zykjofficial/zykjresource@master/img/link.cur),
	auto !important;
}
/*鼠标样式END*/
```
二是，下载鼠标指针cur文件，https://zhutix.com/tag/cursors/，然后在配置css,方法同一一样
``` css
/*鼠标样式*/
body,
html {
  cursor: url(/cur/arrow.cur),
    auto !important;
}

/* a, */
img {
  cursor: url(/cur/btn.cur),
    auto !important;
}

/*a标签*/
a:hover {
  cursor: url(/cur/link.cur),
    auto;
}

input:hover{
  cursor: url(/cur/input.cur),
    auto;
}
/*按钮*/
button:hover {
  cursor: url(/cur/btn.cur),
    auto;
}

/*i标签*/
i:hover {
  cursor: url(/cur/link.cur),
    auto;
}

/*页脚a标签*/
#footer-wrap a:hover {
  cursor: url(/cur/hf.cur),
    auto;
}

/*分页器*/
#pagination .page-number:hover {
  cursor: url(/cur/i.cur),
    auto;
}

/*头部的导航栏*/
#nav .site-page:hover {
  cursor: url(/cur/hf.cur),
    auto;
}

/*鼠标样式END*/

```

+ 气泡波浪特效
https://wr0926.ml/p/cb7b45b6/index.html?_sw-precache=ccec8424f3511abfb621c7341a9d3cf2#%E4%BB%8B%E7%BB%8D

+ 页面美化
theme_color:


+ 字体
https://demo.jerryc.me/posts/ceeb73f/#%E8%87%AA%E5%AE%9A%E7%BE%A9%E5%AD%97%E9%AB%94%E5%92%8C%E5%AD%97%E9%AB%94%E5%A4%A7%E5%B0%8F

+ 网站副标题
https://demo.jerryc.me/posts/ceeb73f/#%E7%B6%B2%E7%AB%99%E5%89%AF%E6%A8%99%E9%A1%8C

+ 页面预加载加载动画
https://demo.jerryc.me/posts/ceeb73f/#%E9%A0%81%E9%9D%A2%E5%8A%A0%E8%BC%89%E5%8B%95%E7%95%ABpreloader



+ Snackbar 弹窗
https://demo.jerryc.me/posts/ceeb73f/#Snackbar-%E5%BD%88%E7%AA%97

+ 豆瓣

https://demo.jerryc.me/posts/ceeb73f/#%E8%B1%86%E7%93%A3


+ pjax

https://demo.jerryc.me/posts/ceeb73f/#Pjax

+ inject
https://demo.jerryc.me/posts/ceeb73f/#Inject
留意: 如果你的網站根目錄不是’/‘,使用本地圖片時，需加上你的根目錄。
例如：網站是 https://yoursite.com/blog,引用css/xx.css，則設置為<link rel="stylesheet" href="/blog/css/xx.css">

不要把個人需要的文件/圖片放在主題source文件夾裏，因為在升級主題的過程中，可能會把文件覆蓋刪除了。
在Hexo根目錄的source文件夾裏，創建一個文件夾來放置個人文件/圖片。文件夾不能命名為css、js和img
引用文件直接為/文件夾名稱/文件名

+ cdn


+ seo优化

+ pwa
https://www.jianshu.com/p/74ee8695140c
https://demo.jerryc.me/posts/ceeb73f/#PWA
https://demo.jerryc.me/posts/4073eda/#PWA

+ gulp压缩
https://demo.jerryc.me/posts/4073eda/#Gulp%E5%A3%93%E7%B8%AE

+ icon图标
https://demo.jerryc.me/posts/4073eda/#Icon

+ 图片压缩
https://demo.jerryc.me/posts/4073eda/#%E5%9C%96%E7%89%87%E5%A3%93%E7%B8%AE

## 1. hexo修改默认端口

默认使用4000端口，用hexo s -p 80 ，可以暂时修改启动端口。

找到node_modules\hexo-server\index.js文件，可以修改默认的port值！

修改端口后，可以在本地开启2个主题，便于自己魔改。

## 2. 给Awesome图标加颜色 
主题样式修改，如何添加css和js。对主题修改主要以下两个方法：
1. 外部挂载代码（推荐）
2. 直接修改源码

外部挂载代码，稳定性高，可以平滑升级，不到迫不得已不要修改源码。
**步骤**：
打开主题目录下的配置文件，找到以下代码
``` bash
# inject
inject:
  head:
   - <link rel="stylesheet" href="/css/background.css">
  bottom:
   - <script src="/js/classify.js"></script>
```
+ 通常在head处挂载css代码，在bottom处挂载js代码
+ css代码通常放在\Butterfly\source\css目录下
+ js代码放在\Butterfly\source\js目录下

## 3.banner底部阴影

``` css
/* banner 底部阴影 */
 header#page-header.full_page{
    /* box-shadow:0 -80px 10px -2px #A7E9EC inset; */
    box-shadow:0 -80px 10px -2px #ffffff4d inset;
} 
```
## 4.主页main背景透明效果

``` css
main#content-inner.layout_page{
    border-width: 30px;
    padding-top: 20px;
    background-color: rgba(233, 241, 241, 0.5);
    box-shadow:0px 5px 10px 2px #ffffff;
}
```

+ rss
https://github.com/hexojs/hexo-generator-feed

+ 链接转数字
hexo-abbrlink
https://github.com/rozbo/hexo-abbrlink

+ 加强网站seo，防止权重丢失
https://github.com/hexojs/hexo-filter-nofollow

+ 站点地图
https://github.com/hexojs/hexo-generator-sitemap

+ 站内搜索
https://github.com/coneycode/hexo-generator-baidu-sitemap
+ 购买域名


+ 壁纸图库

https://demo.jerryc.me/posts/4aa8abbe/#Gallery%E7%9B%B8%E5%86%8A%E5%9C%96%E5%BA%AB
在index.md中，加入如下格式：
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>

name：圖庫名字
description：圖庫描述
link：連接到對應相冊的地址  这个你在index.md文件同级下，新建一个新的md,专门写对应相册的图片

img-url：圖庫封面的地址

+ 相册格式
{% gallery %}
markdown 圖片格式
{% endgallery %}

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}


