# this theme

 ���ϲ�����ģ�����ֱ��fork�ҵĲֿ⣬�ٲο��ҵĲ��Ĵ�������Լ���blog����������`zengsiyong.github.io`���repository����ޡ������Ͻ�**star**һ��Ŷ�� ??.

## ˵���ĵ�
#### Environment

����㰲װ��jekyll������ֻ��Ҫ������������`jekyll serve`�����ڱ��������Ԥ�����⡣

#### ��ȡ����ģ��

> $ git clone https://github.com/zengsiyong/zengsiyong.github.io

����ֱ��[���ز���] https://github.com/zengsiyong/zengsiyong.github.io/archive/master.zip 


clone�����غ󣬽�zengsiyong.github.io/ Ŀ¼�£� �������ط��� 

> $ bundle exec jekyll server

����������� [127.0.0.1:4000]�� �Ϳ��Կ�������Ч���ˡ�

#### ��ν�ģ���޸�Ϊ�Լ��Ĳ���
�����ͨ���޸�clone�����صĲֿ��ļ����е� `_config.yml`�ļ����ɵĿ�ʼ��Լ��Ĳ���:

```
# Site settings
title: ��˼��_Blog             		# ��Ĳ�����վ����
SEOTitle: ��˼�µ�Blog				# ��ʾ�������������������
description: "����ѧϰ�ʼǵ�Blog"    # �򵥵�blog����

# SNS settings      
github_username: zengsiyong     # ���github�˺�

# Build settings
# paginate: 5              # ��ֵ��һҳ��׼���ż�ƪ����

```

Ҫ���������һ����markdown�ĸ�ʽ��������`_posts/`����ֻҪ������ƪģ�������������������׸�������á�

yaml ͷ�ļ�������:

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

#### SideBar����ʾ����ҳ�ұߵĸ������ϲ��֣�


�������� `_config.yml`�ļ������`Sidebar settings`�ǿ顣
```
# Sidebar settings
sidebar: true  #��Ӳ����
sidebar-about-description: "�򵥵�����һ�����Լ�"
sidebar-avatar: /img/me.jpg     #��Ĵ�ͷ������ʹ�þ��Ե�ַ.
```

���������Ӧʽ���ֵģ�����Ļ�ߴ�С��992px��ʱ�򣬲�����ͻ��ƶ����ײ����������bootstrapդ��ϵͳ <http://v3.bootcss.com/css/>


#### Mini About Me

Mini-About-Me ���ģ�齫�����ͷ�����棬չʾ�����е��罻�˺š����Ҳ����Ӧʽ���֣�����Ļ��Сʱ�򣬻Ὣ���ƶ���ҳ��ײ���ֻ��������΢�е�С�仯�������뿴���롣

#### Featured Tags

���������վ [Medium](http://medium.com) ���Ƽ���ǩ�ǳ����ſᣬ�����ҽ������˽�����
���ģ�������Ƕ����ģ����Գ���������ҳ�棬������ҳ�ͷ����ÿһƪ���±����ͷ�ϡ�

```
# Featured Tags
featured-tags: true  
featured-condition-size: 1     # A tag will be featured if the size of it is more than this condition value
```

Ψһ��Ҫע�����`featured-condition-size`: ���һ����ǩ�� SIZE��Ҳ����ʹ�øñ�ǩ�����������������趨������ֵ�������ǩ�ͻ�����ҳ�ϱ��Ƽ���
 
�ڲ���һ������ģ�� `{% if tag[1].size > {{site.featured-condition-size}} %}` ��������ɸѡ���˵�.




#### Keynote Layout

HTML5�õ�Ƭ���Ű棺


�ⲿ��������ռ��html��ʽ�Ļõ�Ƭ�ģ�һ���õ����� Reveal.js, Impress.js, Slides, Prezi �ȵ�.

����Ҫԭ�������һ�� `iframe`������������ⲿ���ӡ�
�����ֱ��д��ͷ�ļ�����ȥ��������������yamlͷ�ļ���д����

```
---
layout:     keynote
iframe:     "�ⲿ����"
---
```

iframe�ڲ�ͬ���豸�У������Զ��ĵ�����С�������ڱ߾���Ϊ�����ֻ��û��������»������Լ���Ӹ�������ݡ�


#### Comment

���Ͳ���֧�ֶ�˵[Duoshuo](http://duoshuo.com)����ϵͳ��Ҳ֧��[Disqus](http://disqus.com)����ϵͳ��

`Disqus`�ŵ��ǣ����ʱȽ����У�����Ҳ�ܴ�������飬����������ۣ�����ʵʱ֪ͨ��ֱ�ӻظ�֪ͨ���ʼ������ˣ�ȱ���ǣ����۱���Ҫȥע��һ��disqus�˺ţ�����һ��ֻ��Facebook��Twitter��������ǽ�ڼ����ٶ�������һ�㡣��Ҫ֪����ɶ�������Կ���ǰ�İ汾��[����](http://brucezhaor.github.io/about.html) ������Ϳ��Կ�����

`��˵` �ŵ��ǣ�֧�ֹ��ڸ������罻���(΢����΢�ţ����꣬QQ�ռ� ...)һ������ť���ܣ������½�ȽϷ��㣬�������Ҳ�Ǵ����ĵģ������disqusȫӢ�ĵ�Ҫ���ײ���һЩ��ȱ���ǣ����ǽ������һ�㡣
��Ȼ���ǿ����Զ�������css�ģ������뿴��˵�������ĵ� http://dev.duoshuo.com/docs/5003ecd94cab3e7250000008 ��

**����**������Ҫȥע��һ���˺ţ�������disqus���Ƕ�˵�ġ�**��Ҫֱ��ʹ���ҵİ���**

**���**����ֻ��Ҫ�������yamlͷ�ļ�������һ�¾Ϳ����ˡ�

```
duoshuo_username: _����û���_
# ����
disqus_username: _����û���_
```

**���**��˵��֧�ַ���ģ�����㲻��������������ã�`duoshuo_share: false`�������ͬʱʹ����������ϵͳ���������˸о��ֵֹġ�

#### Analytics

��վ����������֧�ְٶ�ͳ�ƺ�Google Analytics����Ҫȥ�ٷ���վע��һ�£�Ȼ�󽫷��ص�code�������棺

```
# Baidu Analytics
ba_track_id: 4cc1f2d8f3067386cc5cdb626a202900
```

```
1. ���ģ���Ǵ�����[IronSummitMedia/startbootstrap-clean-blog-jekyll](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll)  fork �ġ� ��л�������
2. ��л[@BrucZhaoR](https://github.com/BruceZhaoR)�����ķ��� 

3. ��л Jekyll��Github Pages �� Bootstrap!
```


