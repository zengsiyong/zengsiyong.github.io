---
layout:     post
title:      "bootstrap使用"
date:       2017-05-12 16:00:00
author:     "曾思勇"
header-img: "img/bootstrap.jpg"
header-mask: 0.3
catalog:    true
tags:
    - 前端
---


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-f29b0141d8b4163e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 一、下载Bootstrap
* [Bootstrap中文网v3下载地址](http://v3.bootcss.com/getting-started/#download)
![Bootstrap下载](http://upload-images.jianshu.io/upload_images/2762413-e376329247180780.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 下载完成后解压得到目录结构
![目录结构1](http://upload-images.jianshu.io/upload_images/2762413-66793bfa22de57b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![目录结构2](http://upload-images.jianshu.io/upload_images/2762413-387bc1eea0e96ede.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

*  将目录结构的三个文件夹全部导入所要应用的站点目录中，**注意需要在js文件夹中添加框架依赖的JS库文件**
![导入站点目录](http://upload-images.jianshu.io/upload_images/2762413-72bf9d244e6fe609.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 使用**基本模板**创建H5文件即可生成最简单的Bootstrap页面
![基本模版](http://upload-images.jianshu.io/upload_images/2762413-1dffadac0047e86f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 二、viewPort
1.  通俗的讲，移动设备上的viewport就是 **设备的屏幕上能用来显示我们的网页的那一块区域**，在具体一点，就是浏览器上(也可能是一个app中的webview)用来显示网页的那部分区域，但viewport又不局限于浏览器可视区域的大小，要根据PC或移动端决定。
**注意：同样大小的屏幕，如果后者分辨率是前者的两倍，则后者的一个css像素等效于两个物理像素**

2. **基本模版中有如下的meta标签，作用是让当前viewport的宽度等于设备的宽度**，同时不允许用户手动缩放。

```
<meta name="viewport" content="width=device-width , initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
//要得到ideal viewport(理想视口)默认的layout viewport的宽度设为移动设备的屏幕宽度。因为meta viewport中的width能控制layout viewport的宽度，所以我们只需要把width设为width-device这个特殊的值就行了。
```

### 三、布局容器
Bootstrap **必须**需要为页面内容和栅格系统包裹一个` .container` 容器。我们提供了两个作此用处的类。注意，由于` padding `等属性的原因，这两种 容器类不能互相嵌套
* `.container` 类用于固定宽度并**支持响应式布局**的容器。
* `.container-fluid` 类用于 100% 宽度，占据全部视口（viewport）的容器。

![两种容器的代码书写](http://upload-images.jianshu.io/upload_images/2762413-b80d87edbac85e49.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 注意使用容器默认内容前面会有间距，如果想取消就在当前html中的css样式中添加paddings属性值为0像素，**尽量不要改动原有的bootstrap模版中css文件的内容**
![两种容器的区别](http://upload-images.jianshu.io/upload_images/2762413-f42003f910d6f4e0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 四、排版/表格/表单/按钮/图片
* 在使用bootstrap创建页面时**通过在html标签引入已有的css类生成对应的排版效果**，例如通过在p标签中调用class="text-xxx"使文本颜色发生相应变化
![排版需调用的固定css类](http://upload-images.jianshu.io/upload_images/2762413-fee6c62c053a564e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 具体样式在使用时通过bootstrap文档查询即可

### 五、栅格系统
* Bootstrap内置了一套响应式、移动设备优先的流式栅格系统，随着屏幕设备或视口（viewport）尺寸的增加，系统会自动分为最多12列。
**注意：如果一行的列数大于12，则多余的列数会作为一个整体另起一行排列** 
* 栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。
**注意：如下面的案例中根据 -xs -md 的划分，第二行在桌面端显示为3列，在手机端中则前两列显示为一行，第三列另起一行。而一般手机端会隐藏部分列内容，使得排版更加简洁美观**
![案例1--移动设备和桌面](http://upload-images.jianshu.io/upload_images/2762413-3460b64e6ff2f550.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 媒体查询
在栅格系统中，我们在 Less 文件中使用以下媒体查询（media query）来创建关键的分界点阈值
```
        /* 超小屏幕（手机，小于 768px） */
        /* 没有任何媒体查询相关的代码，因为这在 Bootstrap 中是默认的（还记得Bootstrap 是移动设备优先的吗？） */

        /* 小屏幕（平板，大于等于 768px） */
        @media (min-width: @screen-sm-min) { ... }

        /* 中等屏幕（桌面显示器，大于等于 992px） */
        @media (min-width: @screen-md-min) { ... }

        /* 大屏幕（大桌面显示器，大于等于 1200px） */
        @media (min-width: @screen-lg-min) { ... }
```

### 六、响应式工具
* 可用的类
通过单独或联合使用以下列出的类，可以针对不同屏幕尺寸隐藏或显示页面内容。
![可用的类](http://upload-images.jianshu.io/upload_images/2762413-d6471548fa3d9e7e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 七、常用组件
* 下拉菜单：可套用模板修改菜单名和超链接
![代码](http://upload-images.jianshu.io/upload_images/2762413-542e0ab11c17f199.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![下拉菜单效果](http://upload-images.jianshu.io/upload_images/2762413-954b5ec70ce0a2c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 按钮工具栏
* 导航：胶囊式标签页
* 导航条：表单/按钮/文本
* 分页
表单

### 八、JavaScript 插件
* Carousel：实现轮播图效果
![轮播图效果](http://upload-images.jianshu.io/upload_images/2762413-8c19078fb92a2cf1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)