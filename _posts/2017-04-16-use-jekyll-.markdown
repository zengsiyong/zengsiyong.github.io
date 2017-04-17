---
layout:     post
title:      "[17年重整版]Jekyll搭建个人博客"
date:       2017-04-16 11:00:00
author:     "曾思勇"
header-img: "img/Our+Blog.jpg"
header-mask: 0.3
catalog:    true
tags:
    - tool
    - 写作
---



这是基于githubpage使用Jekyll工具搭建的博客效果：[曾思勇的博客](http://zengsiyong.github.io)
![博客截图.jpg](http://upload-images.jianshu.io/upload_images/2762413-e4b693a2ad539aaa.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
[博文简书链接](http://www.jianshu.com/p/aadffb90d634)

## 一、Jekyll是什么
　　Jekyll是一款静态网站生成工具，允许用户使用HTML、Markdown或Textile通过模块的方式建立所需网站，然后通过模板引擎Liquid（Liquid Templating Engine）来运行或者生成对应的静态网站文件。因为GitHub的渲染引擎默认为Jekyll，所以Jekyll在GitHub上使用较多，通过GitHub搭建自己的博客一般都是使用Jekyll。

　　**因为Jekyll是一款基于*Ruby*的插件，必须先配置*Ruby*开发环境，需要*Pygments*代码高亮引擎，所以需配置*Python*开发环境**

## 二、安装Ruby

1. **[安装包下载页面](http://rubyinstaller.org/downloads/)**
2. **在 “RubyInstallers” 部分，选择某个版本点击下载**。
例如， Ruby 2.2.4-p230-(x64) 是适于**64位 Windows** 机器上的安装包。
![Ruby安装包.png](http://upload-images.jianshu.io/upload_images/2762413-89cd6c2ff23651e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.  **通过安装包安装**

　　最好保持**默认的路径** C:\Ruby22-x64， 因为安装包明确提出 “请不要使用带有空格的文件夹 (如： Program Files)”。

　　**勾选 “Add Ruby executables to your PATH”**，这样执行程序会被自动添加至 PATH 而避免不必要的头疼。
![安装目录设置.png](http://upload-images.jianshu.io/upload_images/2762413-1aada41104b2d515.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
		
4.  **打开一个命令提示行并输入`ruby -v`检测 Ruby 是否成功安装（注意命令行要重新开启）**
![检测Ruby版本.png](http://upload-images.jianshu.io/upload_images/2762413-73ff236e4b3b0a82.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. ** 打开一个命令提示行并输入`gem -v`来检测 gem 是否存在**
![检测gem版本.png](http://upload-images.jianshu.io/upload_images/2762413-4e6261d82a508470.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 三、安装 DevKit
　　DevKit 是一个在 Windows 上帮助简化安装及使用 Ruby C/C++ 扩展如 RDiscount 和 RedCloth 的工具箱。 详细的安装指南可以在程序的wiki 页面 阅读。
1. **[安装包下载页面](http://rubyinstaller.org/downloads/)**
2. **下载同系统及 Ruby 版本相对应的 DevKit 安装包。** 例如，DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe 适用于64位 Windows 系统上的 Ruby 2.0.0及以上的版本
![选择DevKit 版本.png](http://upload-images.jianshu.io/upload_images/2762413-5d636ad2132a5728.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. **运行安装包并解压缩至某文件夹，如 C:\DevKit**
4. **通过初始化来创建 config.yml 文件。**在命令行窗口内，输入下列命令：
`
cd “C:\DevKit”
ruby dk.rb init
`
![初始化.png](http://upload-images.jianshu.io/upload_images/2762413-c850e2bb40c9c1cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. **通过记事本打开该目录下config.yml，于末尾添加如下代码，保存后退出**

`- C:\Ruby22-x64`

6. 回到命令行窗口内，审查（非必须）并安装。

```
ruby dk.rb review

ruby dk.rb install
```


## 四、安装 Jekyll
1.**确保 gem 已经正确安装（在2.2.4版本的ruby会自动安装）**

2.**安装 Jekyll gem**
![安装 Jekyll gem.png](http://upload-images.jianshu.io/upload_images/2762413-90dc0f29d8e373f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


`gem install jekyll`


+  如果报错参照解决办法
 [证书验证](https://github.com/ruby-china/rubygems-mirror/wiki)
+ 其他报错请参考文末的常见错误及解决方法

3.**安装jekyll-paginate**，在命令行里输入

`gem install jekyll-paginate`
![gem install jekyll-paginate.png](http://upload-images.jianshu.io/upload_images/2762413-98e463c0f997cf4a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如遇到以下错误，说明网络不通：
```
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
Errno::ECONNRESET: An existing connection was forcibly closed by the remote host.
```
4.**该方法如果不行请先继续下面操作**

## 五、安装 Python
1. **[python下载地址]( http://www.python.org/download/)**
2. **下载合适的 Python windows 安装包，**如 *Python 2.7.6 Windows Installer*。
3. 安装
4. **添加安装路径 (如： C:\Python27) 至 PATH。**(不懂可百度添加环境变量)
![添加环境变量.png](http://upload-images.jianshu.io/upload_images/2762413-a098d4d5f33c9a08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	
5. 检验 Python 安装是否成功
`python –V`
![检验 Python 安装是否成功.png](http://upload-images.jianshu.io/upload_images/2762413-2f85644b3a2bdb1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. **安装 ‘Easy Install’**


+ [详细安装指南](https://pypi.python.org/pypi/setuptools#installation-instructions) （需要梯子）
+ 对于 Windows 7以上的机器，**百度查找 `ez_setup.py` 文件后复制内容保存到本地，例如，至C:\。 然后从命令行使用 Python 运行此文件：**
`python “C:\ez_setup.py”`
+ **添加 ‘Python Scripts’ 路径 (如： C:\Python27\Scripts) 至 PATH**
![添加 ‘Python Scripts’ 路径到环境变量.png](http://upload-images.jianshu.io/upload_images/2762413-f374cad9a2f7fc8e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 七、安装 Pygments
1. 确保 easy_install 已经正确安装

`easy_install --version`

输出示例：

`setuptools 3.1`

2. 使用 “easy_install” 来安装 Pygments

`easy_install Pygments`
![安装 Pygments](http://upload-images.jianshu.io/upload_images/2762413-4436a135931874fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	

## 八、启动 Jekyll
　　按照[Jekyll中文文档](http://jekyll.bootcss.com/) 的步骤
1. **先进入一个你想要存储博客的文件夹中**
2. **`jekyll new myblog`**
3. **`cd myblog`**
4. **`jekyll serve`**
![生成的 myblog文件夹内容.png](http://upload-images.jianshu.io/upload_images/2762413-e537cd7525bd5687.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

　　**一个新的 Jekyll 博客可以被建立并在 *localhost:4000* 浏览。**即在浏览器地址框输入 *localhost:4000* 或者 *127.0.0.1:4000* 

![我新建的Jekyll网页.png](http://upload-images.jianshu.io/upload_images/2762413-5168e73df0afc236.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 九、套用优秀的博客模版
**详细教程请查看我的另外一篇博文[[17年重整版]GithubPages + Jekyll搭建个人博客](http://www.jianshu.com/p/64864a179c2e)**
+ ** 挑选“模版”**
[Jekyll项目的wiki页面](https://github.com/jekyll/jekyll/wiki/sites)给出了大量优秀的风格各异的网站，这里以 Zhijun Kang为例讲解。
点击[Zhijun Kang](http://robotkang.cc/)，会跳出他的博客首页
返回github进入wiki页，点击Zhijun Kang右边的source链接，进入到作者的模版仓库。
![操作演示.png](http://upload-images.jianshu.io/upload_images/2762413-1bf5786899a6fc02.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在右边有绿色的克隆代码到本地按钮，通过ZIP下载到本地
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-9cae01d6f0095cf3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下载后解压得到模版的网页站点文件夹
![模版网页的站点文件夹.png](http://upload-images.jianshu.io/upload_images/2762413-aca9ba78ecdfb95b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 十、使用jekyll serve命令部署本地服务
**打开命令行进入到模板文件夹目录下，执行命令**
`jekyll serve`
**如果你配置jekyll环境不完全，可能会出现许多未知错误**
下图为正确配置jekyll环境后会发生的错误提示
![错误提示1.png](http://upload-images.jianshu.io/upload_images/2762413-a0edb2f12f6b0096.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**原因： 没有安装 bundler ，所以接下来执行安装 bundler 命令**

`gem install bundler`
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2762413-08395e3539ee4f42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**如果报错，尝试更换源，注意众多博客中的源都没有更新**
更换源的步骤如下
```
$ gem sources  //查看当前源
$ gem sources --remove http://ruby.taobao.org/
$ gem sources -a http://gems.ruby-china.org/
$ gem sources -l
```
![建议添加源为http://gems.ruby-china.org/.png](http://upload-images.jianshu.io/upload_images/2762413-8dbfbf7043c795fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

命令行显示当前ruby源
```
*** CURRENT SOURCES ***
http://gems.ruby-china.org/
```
**接下来执行
`bundle install`**
安装过程中出现错误提示：在安装redcarpet时出现错误
![错误提示2.png](http://upload-images.jianshu.io/upload_images/2762413-3d7b99b1c81c96d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

请用一下指令安装该程序至成功再**重新安装bundle**

`gem install redcarpet`

如下图显示redcarpet已经安装成功
![redcarpet安装成功.png](http://upload-images.jianshu.io/upload_images/2762413-d904a0d57b54660e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**再次运行 `bundle install` 直到提示成功**（未知错误请参考文末解决方法）
![再次运行 bundle install .png](http://upload-images.jianshu.io/upload_images/2762413-c087465b0b6a6716.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**执行jekyll server**
![错误提示3.png](http://upload-images.jianshu.io/upload_images/2762413-758f765749a90bfe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

错误信息中有提示：**尝试在你要输入的命令前添加 `bundle exec`**

![在jekyll server 命令前添加 bundle exec
](http://upload-images.jianshu.io/upload_images/2762413-b6c0d5ede3a6bd26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如上图所示，**在本地启动jekyll sever成功，现在即可在浏览器通过
http://localhost:4000 或者 http://127.0.0.1:4000/ ，访问拷贝的博客模版。**
![本地启动模版网页.png](http://upload-images.jianshu.io/upload_images/2762413-2f4daee82ab259d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 十一、将模版修改为自己的内容
+ **修改博客名，博客简介等个人信息内容 ：**
　　使用编辑器打开本地仓库中的 _config.yml 文件，按照里面的注释修改为自己的内容。

+ **修改博客文章内容**
　　打开本地仓库的 _posts 文件夹。默认博文都将放在这里，写新博文只需要新建一个标准文件名的文件，在文件中编写文章内容。 比如_posts 文件夹里有一篇 2016-03-23-hello-world.markdown，你的文件命名也要严格遵循 年-月-日-文章标题.文档格式 这样的格式，尤其要注意月份和日期一定是两位数，尽量不要出现中文。推荐使用Markdown语言写文章，windows下推荐MarkdownPad这个软件编写Markdown文本，web中使用简书。

+ **提交修改**
　　修改好内容后按照更新仓库版本的方法重新提交本地仓库中的内容到github的远程仓库，关闭浏览器再次刷新 http://localhost:4000 或者 http://127.0.0.1:4000/ 就可以生效修改了 。

## 十二、博客部署到远端
　　**详细教程请查看我的另外一篇博文[[17年重整版]GithubPages + Jekyll搭建个人博客](http://www.jianshu.com/p/64864a179c2e)**　　
　　
　　这里讲的是部署到 Github Page， 创建一个 github 账号，然后创建一个跟你账户名一样的仓库，如我的 github 账户名叫 zengsiyong，我的 github 仓库名就叫 zengsiyong.github.io，创建好了之后，把刚才建立的 myBlog 项目 push 到 username.github.io仓库里去（username指的是你的github用户名），检查你远端仓库已经跟你本地 myBlog 同步了，然后你在浏览器里输入 username.github.io ，就可以访问你的博客了。
　　
## 十三、总结
　　**所以通过配置jekyll环境，我们就可以通过在站点文件夹中运行 `jekyll server`命令并通过 http://localhost:4000 查看我们对网页做出的修改，修改满意后再`push`到 github 远程仓库，在外网通过 github page `username.github.io`访问自己的博客。**
### 错误汇总：
1.**使用ruby2.0.0等较旧的版本时，可能会出现如下错误**，解决方法是进入ruby安装文件夹，点击卸载，重新下载例如本博客使用的ruby2.2.4版本安装。
![ruby旧版本导致的错误.png](http://upload-images.jianshu.io/upload_images/2762413-3305d9a5792c34f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.**如果jekyll serve命令执行出现如下错误**，就必须重新执行
install bundle和gem bundle install两条命令直至成功
![bundle安装失败的错误.png](http://upload-images.jianshu.io/upload_images/2762413-57316a88c5860148.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.出现如下错误时，应按照正文中的方式步骤重新做一遍
![未知错误请重新配置环境.png](http://upload-images.jianshu.io/upload_images/2762413-6b674cda1058270e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 参考文档
[1][windows安装jekyll](http://blog.csdn.net/rainloving/article/details/45745491)

[2][Jekyll中文文档](http://jekyll.bootcss.com/)

[3][使用Github Pages建独立博客](http://beiyuu.com/github-pages/)

[4][亢志军博客](http://robotkang.cc/2017/03/HowToCreateBlog/)

[5][独立博客一小时快速搭建](http://playingfingers.com/2016/03/26/build-a-blog/)