---
layout:     post
title:      "PS切图实用整理"
date:       2017-04-23 22:00:00
author:     "曾思勇"
header-img: "img/ps.jpg"
header-mask: 0.3
catalog:    true
tags:
    - 前端
---


`注：本文使用的PS软件为CS5和CC2017，所以本教程使用各个版本PS`
![PSCC2017.jpg](http://upload-images.jianshu.io/upload_images/2762413-2f11c1591fffe209.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 一、PS首选项设置
+ 在顶部菜单栏中选择 ***编辑>首选项>单位和标尺***
![菜单选择.png](http://upload-images.jianshu.io/upload_images/2762413-f8740e2df4eeab93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 标尺与文字选择为 ***像素***
![修改单位标尺.png](http://upload-images.jianshu.io/upload_images/2762413-2c0dd2291e20c999.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 二、工作区面板设置
+ 在菜单栏 ***窗口*** 中打开三个视图面板
![视图面板设置.png](http://upload-images.jianshu.io/upload_images/2762413-95e13de3eda25869.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 保存到新建的工作区
![保存新建工作区.png](http://upload-images.jianshu.io/upload_images/2762413-e3dfd5c6c3bd0fb4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 三、基本工具设置
+ ***移动工具*** : 将自动选择打钩，选择 ***图层*** 而不是 ***组***
![移动工具设置.png](http://upload-images.jianshu.io/upload_images/2762413-b84bc7f4c56b6901.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ ***魔棒工具*** : 容差越小，选择的颜色范围越小
![魔棒工具修改容差](http://upload-images.jianshu.io/upload_images/2762413-6bd35ad7a3138a3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 四、辅助视图
+ 在菜单栏 ***视图*** 中开启 : ***显示额外内容、对齐、标尺、参考线***
![视图设置.png](http://upload-images.jianshu.io/upload_images/2762413-7f71eb25529b5048.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 五、切图常需测量的数值
+ 宽度、高度
+ 内边距、外边距
+ 边框
+ 定位
+ 文字大小
+ 行高
+ 背景图位置

#### 六、使用矩形选框工具进行长度测量
+ ***矩形选框*** : 选择图片后通过 ***信息*** 面板查看图片的宽和高
![查看图片的宽和高.png](http://upload-images.jianshu.io/upload_images/2762413-aee801cecb95ca38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 使用选框测量嵌入背景中的字体大小，高度即为字号大小
![测量嵌入背景中的字体大小.png](http://upload-images.jianshu.io/upload_images/2762413-e6ede69ca7fc7b05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ 快捷键
+ 添加到选取 : 在已选区按住 shift
+ 从选区减去 : 在已选区按住 alt
+ 与选取交叉 : 在已选区按住 shift + alt

#### 七、取色
+ 使用 ***拾色器&吸管工具***
![拾色.png](http://upload-images.jianshu.io/upload_images/2762413-6daa12fbaa1fe420.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
+ 拾色器中的此值用来应用在css中
![css应用数值.png](http://upload-images.jianshu.io/upload_images/2762413-a3e2927c52ec8074.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 八、常见切图需求
+ **隐藏文字只留背景**

背景是纯色适合拉伸时,使用 `ctrl+T`,先矩形选框一小块区域，然后拉伸覆盖字体 
![拉伸背景图片](http://upload-images.jianshu.io/upload_images/2762413-91697752ebc69d38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
背景有纹理时,先用矩形选框一小块区域，然后按住alt（shift键可以保证拖动选框时是水平方向）

+ **抠播放按钮**

　　在 ***矩形工具*** 框选按钮图标区域，使用 ***魔棒工具***，容差按背景颜色设定，鼠标点选按键内的空白部分，就可以扣出按钮，可以结合以下快捷键
```
ctrl+shift+T（反选）
alt + 魔棒（删减选中区域）
shift + 魔棒（增加选中区域）
```
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-a1f389b7958efd91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ **切片工具**

在需要切图的地方画置参考线，画好后点选 ***切片工具***，上方选择基于
 ***参考线自动切片***，如图对应两条参考线自动切好。
![切片工具的使用.png](http://upload-images.jianshu.io/upload_images/2762413-d54b54f4641686e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击 ***文件>导出>存储为Web所用格式***
![保存切片.png](http://upload-images.jianshu.io/upload_images/2762413-21066d998bccade7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择好切片，右边统一修改为JPG格式，高，品质60，点击下方保存（点击菜单栏的 ***双联*** 可以对比保存前后的切片图）
![设置图片选项.png](http://upload-images.jianshu.io/upload_images/2762413-5e4e8dad2d8ee1a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 九、图片保存类型
平时在ps中对于用于网站设计的图片，应该**存储为web所用格式**
![图片保存类型.png](http://upload-images.jianshu.io/upload_images/2762413-d440463fc33ee449.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ **保存类型一** : 当图片色彩丰富且无透明要求时，建议保存为***JPG*** 格式并选择合适的品质
+ **保存类型二** : 当图片色彩不太丰富时无论有无透明要求，请保存为 ***PNG8*** 
+ **保存类型三** : 当图片有半透明要求，请保存为 ***PNG24***
+ **保存类型四** : 为保证图片质量，保留一份 ***PSD*** ,方便修改

#### 十、修改和维护
+ **更改画布大小**：菜单栏 ***图像>画布大小***
+ **减小画布到制定区域**：***矩形工具*** 选中区域后菜单栏选中 *** 图像>裁剪***，或者直接使用 ***裁剪工具*** 
![修改画布.png](http://upload-images.jianshu.io/upload_images/2762413-37be48220bfdb071.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 十一、常用快捷键
+ 图层窗口中使用 `Ctrl` 可以多选所需图层
+ 右键合并图层（`Ctrl +Ｅ`） 
+ 复制图层（`Ctrl + C`）
+ 新建文档用于存放合并修改好的图层（`Ctrl + N`）
+ 粘贴图层 （`Ctrl +V`）
+ 跨文档移动图层也可以通过在图层右键点击复制图层后选择要粘贴到的文档，或者直接拖动图层到另外一个文档。

#### 注意事项
 **修改PNG8格式的图片时，需要在菜单栏 图像>模式>更改为RGB颜色**
![修改颜色模式.png](http://upload-images.jianshu.io/upload_images/2762413-4977bea50947e115.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

[简书博文链接](http://www.jianshu.com/p/27ad2d3e1c9a)