---
layout:     post
title:      "利用JDK_API发现错误原因"
date:       2017-04-17 22:00:00
author:     "曾思勇"
header-img: "img/coding.jpg"
header-mask: 0.3
catalog:    true
tags:
    - markdown
    - 写作
---

　　**在java编写代码过程中，经常遇到编译器没有提示错误，而控制台提示异常报错，对于初学者来说面对一串串英文的错误信息可能无从下手，这篇文档就用实例和API文档来解读错误信息。**
#### 错误实例一：java中使用dom解析xml时在指定标签前添加子节点
xml代码：book2.xml

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?><书架>
	<书 编号="b2">
		<书名>javaweb开发大全</书名>
		<作者>班长</作者>
		<售价>99.8元</售价>
		<简介>这是不错啊</简介>
	</书>
	<书>
		<书名>葵花宝典</书名>
		<作者>岳不群</作者>
		<售价>99.8</售价>
		<简介>欲练此功...</简介>
		<出版社>人民出版社</出版社>
	</书>
</书架>
```

java代码：JaxpDomTest.java


```java
package cn.itcast.jaxp;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.transform.Transformer;
import javax.xml.transform.TransformerFactory;
import javax.xml.transform.dom.DOMSource;
import javax.xml.transform.stream.StreamResult;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.Node;
import org.w3c.dom.NodeList;

import cn.itcast.utils.JaxpDomUtil;

/**
 * JAXP的DOM解析XML
 * @author Administrator
 *
 */
public class JaxpDomTest {
	
	public static void main(String[] args) {
		try {
			run2();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
	public static void run2() throws Exception{
		// 获取工厂类
		DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
		// 获取解析器
		DocumentBuilder builder = factory.newDocumentBuilder();
		// 解析xml，返回document对象
		Document document = builder.parse("src/book2.xml");
		// 获取第二本书
		Node book2 = document.getElementsByTagName("书").item(1);
		// 创建元素对象
		Element chubanshe = document.createElement("出版社");
		// 设置文本内容
		chubanshe.setTextContent("人民出版社");
		//在book2中添加出版社标签
		book2.appendChild(chubanshe);
		
        //使用insertbefore方法想把出版社标签插入到售价标签前面时报错
		Node shoujia = book2.getChildNodes().item(2);
		document.insertBefore(chubanshe, shoujia);
		
		// 回写
		// 创建回写类的工厂
		TransformerFactory transformerFactory =  TransformerFactory.newInstance();
		// 获取回写类
		Transformer transformer = transformerFactory.newTransformer();
		// 调用回写的方法
		transformer.transform(new DOMSource(document), new StreamResult("src/book2.xml"));
	}
}
```


错误信息：
> org.w3c.dom.DOMException: HIERARCHY_REQUEST_ERR: 尝试在不允许的位置插入节点。
	
	at com.sun.org.apache.xerces.internal.dom.CoreDocumentImpl.insertBefore(CoreDocumentImpl.java:396)
	
	at cn.itcast.jaxp.JaxpDomTest.run2(JaxpDomTest.java:76)
	
	at cn.itcast.jaxp.JaxpDomTest.main(JaxpDomTest.java:26) 


### 利用错误信息中的关键词定位到JDK_API中对应的描述：
+ ###### DOMException定位到类

![DOMException类.png](http://upload-images.jianshu.io/upload_images/2762413-aafd5f3a03882116.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ ###### HIERARCHY_REQUEST_ERR定位到该类下的字段摘要

![HIERARCHY_REQUEST_ERR字段摘要.png](http://upload-images.jianshu.io/upload_images/2762413-134246ec0e0de514.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

+ ###### at com.sun.org.apache.xerces.internal.dom.CoreDocumentImpl.insertBefore定位到insertbefore方法

![insertbefore方法.png](http://upload-images.jianshu.io/upload_images/2762413-fda0a958f7381fe1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* ###### 再由insetBefore方法定位到两个参数node节点对象是否正确，检查后无误
* ###### 最后检测调用insetBefore方法的对象，发现错误原因：
> 查阅API可知，insetBefore方法的调用对象必须是添加之前的现有子节点的父节点，而之前的代码错误地调用对象document而不是book2，所以源代码只需修改为
        book2.insertBefore(chubanshe, shoujia);
+ ##### 修改结果
![修改成功结果.png](http://upload-images.jianshu.io/upload_images/2762413-a6d1f546381aaac6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 特别注意：textNode的存在，即xml中空格部分也是作为一个子节点。