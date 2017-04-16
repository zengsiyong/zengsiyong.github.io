# this theme

 如果喜欢这个模版可以直接fork我的仓库，再参考我的博文搭建属于你自己的blog，别忘了在`zengsiyong.github.io`这个repository点个赞——右上角**star**一下哦！ ??.

## 说明文档
#### Environment

如果你安装了jekyll，那你只需要在命令行输入`jekyll serve`就能在本地浏览器预览主题。

#### 获取博客模板

> $ git clone https://github.com/zengsiyong/zengsiyong.github.io

或者直接[下载博客] https://github.com/zengsiyong/zengsiyong.github.io/archive/master.zip 


clone到本地后，进zengsiyong.github.io/ 目录下， 开启本地服务 

> $ bundle exec jekyll server

在浏览器输入 [127.0.0.1:4000]， 就可以看到博客效果了。

#### 如何将模版修改为自己的博客
你可以通用修改clone到本地的仓库文件夹中的 `_config.yml`文件轻松的开始搭建自己的博客:

```
# Site settings
title: 曾思勇_Blog             		# 你的博客网站标题
SEOTitle: 曾思勇的Blog				# 显示在浏览器标题栏的名字
description: "分析学习笔记的Blog"    # 简单地blog描述

# SNS settings      
github_username: zengsiyong     # 你的github账号

# Build settings
# paginate: 5              # 数值是一页你准备放几篇文章

```

要发表的文章一般以markdown的格式放在这里`_posts/`，你只要看看这篇模板里的文章你就立刻明白该如何设置。

yaml 头文件长这样:

```
---
layout:     post
title:      "Hello 2017"
subtitle:   "Hello World, Hello Blog"
date:       2017-04-15 10:05:00
author:     "zengsiyong"
header-img: "img/post-bg-2017.jpg"
tags:
    - Life
---

```

#### SideBar（显示在首页右边的个人资料部分）


设置是在 `_config.yml`文件里面的`Sidebar settings`那块。
```
# Sidebar settings
sidebar: true  #添加侧边栏
sidebar-about-description: "简单的描述一下你自己"
sidebar-avatar: /img/me.jpg     #你的大头贴，请使用绝对地址.
```

侧边栏是响应式布局的，当屏幕尺寸小于992px的时候，侧边栏就会移动到底部。具体请见bootstrap栅格系统 <http://v3.bootcss.com/css/>


#### Mini About Me

Mini-About-Me 这个模块将在你的头像下面，展示你所有的社交账号。这个也是响应式布局，当屏幕变小时候，会将其移动到页面底部，只不过会稍微有点小变化，具体请看代码。

#### Featured Tags

看到这个网站 [Medium](http://medium.com) 的推荐标签非常的炫酷，所以我将他加了进来。
这个模块现在是独立的，可以呈现在所有页面，包括主页和发表的每一篇文章标题的头上。

```
# Featured Tags
featured-tags: true  
featured-condition-size: 1     # A tag will be featured if the size of it is more than this condition value
```

唯一需要注意的是`featured-condition-size`: 如果一个标签的 SIZE，也就是使用该标签的文章数大于上面设定的条件值，这个标签就会在首页上被推荐。
 
内部有一个条件模板 `{% if tag[1].size > {{site.featured-condition-size}} %}` 是用来做筛选过滤的.




#### Keynote Layout

HTML5幻灯片的排版：


这部分是用于占用html格式的幻灯片的，一般用到的是 Reveal.js, Impress.js, Slides, Prezi 等等.

其主要原理是添加一个 `iframe`，在里面加入外部链接。
你可以直接写到头文件里面去，详情请见下面的yaml头文件的写法。

```
---
layout:     keynote
iframe:     "外部链接"
---
```

iframe在不同的设备中，将会自动的调整大小。保留内边距是为了让手机用户可以向下滑动，以及添加更多的内容。


#### Comment

博客不仅支持多说[Duoshuo](http://duoshuo.com)评论系统，也支持[Disqus](http://disqus.com)评论系统。

`Disqus`优点是：国际比较流行，界面也很大气、简介，如果有人评论，还能实时通知，直接回复通知的邮件就行了；缺点是：评论必须要去注册一个disqus账号，分享一般只有Facebook和Twitter，另外在墙内加载速度略慢了一点。想要知道长啥样，可以看以前的版本点[这里](http://brucezhaor.github.io/about.html) 最下面就可以看到。

`多说` 优点是：支持国内各主流社交软件(微博，微信，豆瓣，QQ空间 ...)一键分享按钮功能，另外登陆比较方便，管理界面也是纯中文的，相对于disqus全英文的要容易操作一些；缺点是：就是界面丑了一点。
当然你是可以自定义界面的css的，详情请看多说开发者文档 http://dev.duoshuo.com/docs/5003ecd94cab3e7250000008 。

**首先**，你需要去注册一个账号，不管是disqus还是多说的。**不要直接使用我的啊！**

**其次**，你只需要在下面的yaml头文件中设置一下就可以了。

```
duoshuo_username: _你的用户名_
# 或者
disqus_username: _你的用户名_
```

**最后**多说是支持分享的，如果你不想分享，请这样设置：`duoshuo_share: false`。你可以同时使用两个评论系统，不过个人感觉怪怪的。

#### Analytics

网站分析，现在支持百度统计和Google Analytics。需要去官方网站注册一下，然后将返回的code贴在下面：

```
# Baidu Analytics
ba_track_id: 4cc1f2d8f3067386cc5cdb626a202900
```

```
1. 这个模板是从这里[IronSummitMedia/startbootstrap-clean-blog-jekyll](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll)  fork 的。 感谢这个作者
2. 感谢[@BrucZhaoR](https://github.com/BruceZhaoR)的中文翻译 

3. 感谢 Jekyll、Github Pages 和 Bootstrap!
```


