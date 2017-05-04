---
layout:     post
title:      "网页设计——精品商城"
date:       2017-05-03 20:00:00
author:     "曾思勇"
header-img: "img/cala.jpg"
header-mask: 0.3
catalog:    true
tags:
    - 前端
---


本文使用简单的 **html标签+div+css+JavaScript** 实现带有表单提交和图片轮播效果的商城网站设计，效果如下图，[源码下载github链接](https://github.com/zengsiyong/GoodGoods)（以下仅列举设计过程中的部分注意点）
![精品小屋首页.jpg](http://upload-images.jianshu.io/upload_images/2762413-8aab9efd9af27faa.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 一、搭建网站首页
* **首页的所有内容可以放置在一个大的table标签中，再通过嵌入表格划分模块，并使用div+css在各个模块中添加居中等css效果**
![整体布局](http://upload-images.jianshu.io/upload_images/2762413-86cc09e93cdc1807.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![一行三列表格添加模块内容](http://upload-images.jianshu.io/upload_images/2762413-cca1f4b8adc3d076.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **商品列表模块添加图片**
如下图在table的单元格中插入图片可以居中显示，且在下方有文字说明
![商品列表效果图](http://upload-images.jianshu.io/upload_images/2762413-bb1a6a1a1cb673ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/680)
需要使用align的居中属性，并设置width的值为百分比
![代码实现](http://upload-images.jianshu.io/upload_images/2762413-7295ad3b16474f05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 二、搭建网站注册页面
* **表单标签**：所有需要提交到服务器端的表单项必须使用<form></form>括起来
![注册页面](http://upload-images.jianshu.io/upload_images/2762413-d3fbb0d6967567c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/480)

* **表单提交的是value里的内容**，所以表单中除了file类型都需要设置value值用于上传到后台
![设置value](http://upload-images.jianshu.io/upload_images/2762413-b67b634b4171cdf2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **默认勾选属性**在option标签中是selected而不是checked
![默认勾选属性](http://upload-images.jianshu.io/upload_images/2762413-d3741b235f7f8068.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


* 按钮不需要name属性
![按钮不需要name属性](http://upload-images.jianshu.io/upload_images/2762413-4938edd5b2af35a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


* H5有**required属性**，规定该文本区域是必填的

### 三、搭建网站后台管理页面
* **使用框架结构标签<frameset>可以使同一个浏览器窗口中显示不止一个页面**

![框架结构标签的应用](http://upload-images.jianshu.io/upload_images/2762413-1eee1a467a4d8eb5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![效果图](http://upload-images.jianshu.io/upload_images/2762413-fe821b0c9c4bac81.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/560)

### 四、JS完成表单校验
* **在form标签添加onsubmit事件,并为其绑定一个函数**
![onsubmit绑定js函数](http://upload-images.jianshu.io/upload_images/2762413-c806fd06a8ada81d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 书写函数，用于**获取用户输入的数据**（获取数据时需要在**指定位置定义一个id**）
* **对用户输入的数据进行判断**（使用document.getElementById("").value与判断值比较）
![书写值判断函数.png](http://upload-images.jianshu.io/upload_images/2762413-16293b0d496eeed3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **控制表单提交**：若输入数据非法，提示错误信息并通过**返回一个false**阻止表单提交
![返回false则表单提交失败.png](http://upload-images.jianshu.io/upload_images/2762413-76a2a891e6c43e81.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 利用**正则表达式验证邮箱**

![正则表达式验证邮箱](http://upload-images.jianshu.io/upload_images/2762413-daf50ead21c0d65d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 五、JS实现图片轮播
* **定时器**：BOM浏览器对象模型中window窗口对象的定时器方法， 结果都将返回一个唯一的id值，一般用于清除定时器
```
setInterval("run",3000)方法为每隔3秒执行一次run方法
setTimeout("run",3000)方法为3秒后执行一次run方法
```
* 在body标签中添加**onload事件**，并绑定一个带有定时器和更换图片源文件位置的函数
![设置定时器和改变图片资源文件目录的函数](http://upload-images.jianshu.io/upload_images/2762413-c8cb11910893cb3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 源码下载
[github链接](https://github.com/zengsiyong/GoodGoods)