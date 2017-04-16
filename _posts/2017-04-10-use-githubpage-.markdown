---
layout:     post
title:      "[17年重整版]GithubPages + Jekyll搭建个人博客"
date:       2017-04-15 15:00:00
author:     "曾思勇"
header-img: "img/blog.jpg"
header-mask: 0.3
catalog:    true
tags:
    - tool
    - 写作
---



这是搭建的博客效果：[曾思勇的博客](http://zengsiyong.github.io)
### 一、Github Pages + Jekyll  是什么

+ #### Github:
　　如果你对编程有所了解，就一定听说过[github](https://github.com/)。简单说，它是一个具有版本管理功能的代码仓库，每个项目都有一个主页，列出项目的源文件,如下图。
![github仓库主页.png](http://upload-images.jianshu.io/upload_images/2762413-3ad6c4d5a490014e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)但是对于一个新手来说，看到英文界面和一大堆源代码，就不知何处入手。初学者希望看到的是，一个简明易懂的网页，说明每一步应该怎么做。因此，github就设计了[Pages功能](http://pages.github.com/)，允许用户自定义项目首页，用来替代默认的源码列表。

**　　所以，github Pages可以被认为是用户编写的、托管在github上的静态网页**

+ #### Jekyll:
　　**[Jekyll](http://jekyllrb.com/)（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。**它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。
![Jekyll网站首页.png](http://upload-images.jianshu.io/upload_images/2762413-5c6e514a39d50638.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**　　所以Github Pages + Jekyll就是先在本地编写符合Jekyll规范的网站源码，然后上传到github，由github生成并托管整个网站。**

### 二、Github Pages + Jekyll  优缺点及适合人群

+ #### 优点: 
1. Github免费托管源文件，自动编译符合Jekyll规范的网站。
2. 引入版本管理，修改网站更加安全方便。
3. 支持 Markdown ，编写具有优美排版的文章。


+ #### 缺点: 
1. 需要学习一些基础的Git命令。
2. 若要自己全权制作主题的话需要懂一点网页开发。
3. 由于生成的是静态网页，若要使用动态功能，如评论功能则要使用第三方服务

**　　所以，如果你只是想做一个分享见闻心得的博客，这个方案非常适合你。**

### 三、注册Github
　　到官方网站[github](https://github.com/) 注册账户，记住自己的用户名，后面会常用到。

### 四、安装GIT环境
　　本文主要介绍windows环境下的安装，其他环境可参考廖雪峰的教程
[廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)
+ **安装git for windows**

　　[进入下载页面](https://git-for-windows.github.io/)，安装好以后在开始目录中打开 git bash
![git for windows.png](http://upload-images.jianshu.io/upload_images/2762413-d637319fe6483a30.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

　　在打开的命令行窗口（Shell，操作命令与Linux系统中的相同）内执行以下命令，设置你的git用户名和邮箱：
```
$ git config --global user.name "{username}"          // 用你的用户名替换{username}
$ git config --global user.email "{name@site.com}"    // 用你的邮箱替换{name@site.com}
```
![代码操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-847fb59957668a1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 五、SSH配置
　　**为了和Github的远程仓库进行传输，需要进行SSH加密设置**

　　在刚才打开的Shell内执行：
``` 
$ ssh-keygen -t rsa -C"{name@site.com}"    // 用你的邮箱替换{name@site.com}
可以不输入其他信息，一直敲回车直到命令完成。
```
![代码操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-ba2e02a5e56a354c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这时你的用户目录（win7以上系统默认在 C:\Users\你的计算机用户名）内会出现名为 .ssh 的文件夹，点进去能看到 ` id_rsa ` 和 ` id_rsa.pub ` 两个文件，其中` id_rsa `是私钥，不能让怪人拿走，` id_rsa.pub `是公钥，无需保密。
** 用文字处理软件打开刚才的 id_rsa.pub 文件，复制全部内容。**
![操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-259030c183e37f95.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**接下来用你的浏览器登录Github，点击右上角的“Settings”**
![操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-641b01552add67bf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
**点击“SSH Keys”，“Add SSH Key”，将复制的内容粘贴在Key中，点“Add Key”确定**

 
![点击SHH Keys.png](http://upload-images.jianshu.io/upload_images/2762413-b26d397a55e827bf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Add SSH Key.png](http://upload-images.jianshu.io/upload_images/2762413-b510a4fbb2bbfb93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

至此，SSH配置完成。
 
### 六、建立Github Page
　　有两种方法：一种是自己学习jekyll和前端知识部署独一无二的博客，而对于我们大多数人来说套用模版搭建模版会容易的多，所以我以 **套用模版 **讲解：
 
+ **挑选“模版”**

[Jekyll项目的wiki页面](https://github.com/jekyll/jekyll/wiki/sites)给出了大量优秀的风格各异的网站，这里以 Zhijun Kang为例讲解。
点击[Zhijun Kang](http://robotkang.cc/)，会跳出他的博客首页
返回github进入wiki页，点击Zhijun Kang右边的source链接，进入到作者的模版仓库。
![操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-1bf5786899a6fc02.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在右边有绿色的克隆代码到本地按钮，通过ZIP下载到本地
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-9cae01d6f0095cf3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下载后解压得到模版的网页站点文件夹
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-aca9ba78ecdfb95b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ **新建一个github仓库**

在主页点击repositories
![添加仓库.png](http://upload-images.jianshu.io/upload_images/2762413-65052084af1b9e85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**repositories name的命名是：
你的github用户名.github.io（固定格式**
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-bd5d5fb198df9cbb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ **克隆github的远程仓库到本地文件仓库夹**

打开Git Bash，输入以下命令切换到你想放置本地代码仓库的位置：
```
$ cd {本地路径}     // 比如：cd F:\gitblog_workspace  
```
clone（克隆）你自己的远程仓库：
```
$ git clone https://github.com/{username}/{username}.github.io.git     // 用
你的Github用户名替换{username}
```
刚才新建的仓库为空，所以结果如下：
![克隆github的远程仓库到本地仓库.png](http://upload-images.jianshu.io/upload_images/2762413-6bd83fb83b458a1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入克隆到本地的仓库文件夹
`eg:  F:\gitblog_workspace\zengsiyong.github.io `
把刚才下载好的模版文件夹的内容全部拷贝进来
执行命令
```
$ git status //查看当前仓库状态，
```
如下图可看到复制进来的文件是新的修改,需要通过` git add `指令添加到暂存区
（相关git具体概念请查看git教程[廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)）
![当前仓库状态中的修改.png](http://upload-images.jianshu.io/upload_images/2762413-ffb34081b7a48038.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

接下来执行以下命令
```
$ git add .   //添加当前仓库内的所有修改到暂存区
```
![添加修改到暂存区.png](http://upload-images.jianshu.io/upload_images/2762413-710c823d170534e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
```
$ git commit -m "你提交的版本的名子"  //提交当前暂存区中的修改到版本库
```
![提交暂存区中的修改到版本库.png](http://upload-images.jianshu.io/upload_images/2762413-07b011461ba050fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
$ git push //把当前版本提交到远程仓库
 ```
第一次提交远程库时可能会出现如下错误，原因是还未验证SSH，按提示执行
`git push --set-upstream origin master`,输入`github用户名`
![输入github用户名.png](http://upload-images.jianshu.io/upload_images/2762413-0b948e430d4df2ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

输入github密码
![输入github密码.png](http://upload-images.jianshu.io/upload_images/2762413-8e214b7295b1077b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

验证成功后会开始提交新版本到github的远程仓库
![提交版本.png](http://upload-images.jianshu.io/upload_images/2762413-d4b9511bdf15501b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

提交成功后再刷新github仓库就会和本地仓库一样的内容
![更新github仓库内容.png](http://upload-images.jianshu.io/upload_images/2762413-e0a36df24d363161.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**现在只要在浏览器地址中输入你刚新建的github仓库名
` yourname.github.io `
就会跳转到和刚选择模版同样的站点网页**

### 七、将模版修改为自己的内容
+ **修改博客名，博客简介等个人信息内容**：
使用编辑器打开本地仓库中的 _config.yml 文件，按照里面的注释修改为自己的内容。
 
+ **修改博客文章内容**
打开本地仓库的 _posts 文件夹。默认博文都将放在这里，写新博文只需要新建一个标准文件名的文件，在文件中编写文章内容。 比如_posts 文件夹里有一篇 2016-03-23-hello-world.markdown，你的文件命名也要严格遵循 年-月-日-文章标题.文档格式 这样的格式，尤其要注意月份和日期一定是两位数，尽量不要出现中文。推荐使用Markdown语言写文章，windows下推荐MarkdownPad这个软件编写Markdown文本，web中使用简书。

+ **提交修改**
修改好内容后按照更新仓库版本的方法重新提交本地仓库中的内容到github的远程仓库，关闭浏览器再次刷新你的输入` username.github.io `就可以生效修改了 。

+ **拓展：开启本地实时预览修改内容**
 打开windows系统命令行，输入以下代码
```
$ cd {local repository} // {local repository}替换成你的本地仓库的目录
$ jekyll serve
```
如果不能成功执行，请参照的的另外一篇博文：  [[17年重整版]Jekyll搭建个人博客]()，搭建jekyll运行环境。

#### 八、参考文档
[1][Github Pages](https://pages.github.com/)
[2][Git教程 - 廖雪峰](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
[3][Jekyll中文文档](http://jekyll.bootcss.com/)
[4][使用Github Pages建独立博客](http://beiyuu.com/github-pages/)
[5][亢志军博客](http://robotkang.cc/2017/03/HowToCreateBlog/)
[6][独立博客一小时快速搭建](http://playingfingers.com/2016/03/26/build-a-blog/)（需要翻墙）