---
title: Github+jsDelivr+PicGo 打造稳定快速、高效免费图床
data: 

---

# 🗡搭建概要
![20201019085923](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019085923.png#img-radius)

<font size=4>**选择github作为图床原因：**</font>
> + 它是大厂，不怕跑路
> + 免费，容量不受限，目前还开放了私人仓库o(*￣▽￣*)ブ
> + 使用cdn加速，访问速度还不错

## 1. 准备
### **1.1 注册github账号**  

> + 不多解释，不过有时候网络问题，迟迟在验证是否为机器人这一步卡住。
> + 💡1.更换网络； 2.魔法上网； 3.配置github的hosts

### **1.2 picgo工具**  

官网：默认是在GitHub下载，直达地址[Molunerfinn/PicGo](https://github.com/Molunerfinn/PicGo/releases)。  

注意：windows系统下载<kbd>.exe</kbd>文件，mac 系统选择 dmg 下载
![20201019091344](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019091344.png#img-radius)

vscode 插件：直接在插件库搜索：**picgo**即可。

## 2. 配置操作  

### 2.1 GitHub配置  

> 登录/注册GitHub，新建一个仓库，填写好仓库名，仓库描述，根据需求选择是否为仓库初始化一个README.md描述文件.
![20201019092124](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019092124.png#img-radius)

![20201019093100](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019093100.png#img-radius)  

**生成一个Token**

+ 在主页上角点击方形头像，选择【Settings】
+ 然后在打开页面左侧导航栏，点击【Developer settings】
+ 再在新页面左侧选择：【Personal access tokens】
+ 然后点击右侧的【Generate new token】，填写描述勾选【repo】  
+ 然后点击【Generate token】生成一个Token。    

**注意**：这个Token只会显示一次，自己先保存下来，或者等后面配置好PicGo后再关闭此网页。

![20201019093855](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019093855.png#img-radius)  
![20201019094052](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019094052.png#img-radius) 


### 2.2 picgo配置
#### **2.2.1 picgo软件配置**  
![20201019094213](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019094213.png#img-radius)  

> 在左侧图床设置中，选择github，弹窗配置说明：
+ 设定仓库名：按照【用户名 / 图床仓库名】的格式填写

+ 设定分支名：【master】

+ 设定Token：粘贴之前生成的【Token】

+ 指定存储路径：填写想要储存的路径，如【imgs/】，这样就会在仓库下创建一个名为 imgs 的文件夹，图片将会储存在此文件夹中

+ 设定自定义域名：它的作用是，在图片上传后，PicGo会按照【自定义域名+储存路径+上传的图片名】的方式生成访问链接，放到粘贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为【https://cdn.jsdelivr.net/gh/用户名/图床仓库名 】，上传完毕后，我们就可以通过【https://cdn.jsdelivr.net/gh/用户名/图床仓库名/图片路径】加速访问我们的图片了.  

#### **2.2.2 vscode 中picgo插件配置**

+ 打开插件库，搜索picgo

+ 打开设置，找到【拓展】，找到picgo配置地点，  配置说明和软件配置的一样。

![20201019095150](https://cdn.jsdelivr.net/gh/awelife/imgbed/imgs20201019095150.png#img-radius)

win快捷键：<kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>u</kbd>


https://blog.csdn.net/weixin_44903718/article/details/108327022
