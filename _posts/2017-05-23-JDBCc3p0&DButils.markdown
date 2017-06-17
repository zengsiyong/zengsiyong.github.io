---
layout:     post
title:      "JDBC连接池&DButils"
date:       2017-05-23 14:00:00
author:     "曾思勇"
header-img: "img/sky2.jpg"
header-mask: 0.3
catalog:    true
tags:
    - web服务器技术
---


### 一、JDBC连接池
* 概念：实际开发中“获得连接”或“释放资源”是非常消耗系统资源的两个过程，为了解决这个问题，通过我们采用连接池技术，来共享链接Connection，解决资源浪费，提高代码性能，代码没有节省

* 规范：java为数据库连接池提供了公共的接口 javax.sql.DataSource，常见的连接池：DBCP\C3P0都用不同的方法实现了这个接口

### 二、C3P0连接池
* 使用步骤

  **1. 导入2个jar包**
  
![](http://upload-images.jianshu.io/upload_images/2762413-7615dac2a10b6eeb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  **2.配置文件设置参数**
  
配置文件名称：c3p0-config.xml（固定）

配置文件位置：src（类路径）

配置文件内容：修改常见配置项包括必须项user，password，diverClass（驱动，如com.mysql.jdbc.Driver），jdbcUrl（mysql路径,如jdbc:mysql://localhost:3306/数据库名称）和一些其他的基本配置项

 **3.编写工具类**
c3p0提供核心工具类：ComboPooledDataSource，要使用连接池就必须创建该类的实例对象（注意区分命名配置和默认配置）

此外，需要自己创建一个工具类，例如C3P0Utils，该类的代码应包括如下

![](http://upload-images.jianshu.io/upload_images/2762413-0b9fd86df3be8105.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/2762413-00a373f90366b9d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 三、使用DBUtils操作增删改查
* 概念：如果只使用JDBC开发，会有大量冗余代码，为了简化开发就使用apache commons组件的成员之一:DBUtils（封装了对JDBC的操作）

* 三个核心功能
  1.QueryRunner中提供对sql语句操作的API
  
  2.ResultSetHandler接口，用于定义select操作后，怎样封装结果集
  
  3.DbUtils类，它就是一个工具类，定义了关闭资源与事务处理的方法

### 四、 QueryRunner核心类
* QueryRunner（DataSource ds），提供数据源（连接池），DBUtils底层自动维护链接connection

* update（String sql，Object..params），执行更新数据

* QueryRunner的查询方法是：

public <T> T query(String sql, ResultSetHandler<T> rh, Object… params)

public <T> T query(Connection con, String sql, ResultSetHandler<T> rh, Object… params)

query()方法会通过sql语句和params查询出ResultSet，然后通过rh把ResultSet转换成对应的类型再返回

### 五、ResultSetHandler结果集处理类
* 执行select语句之后得到的是ResultSet，然后对ResultSet进行转换，得到最终我们想要的数据。可以把ResultSet的数据放到一个List中，也可以放到一个Map中，或是一个Bean中。

* DBUtils提供了一个接口ResultSetHandler，它就是**用来将ResultSet转换成目标类型的工具。**

![](http://upload-images.jianshu.io/upload_images/2762413-dc7fd6a358cd1df6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 六、DBUtils工具类
closeQuietly（Connection conn）关闭连接，如果有异常try后不抛出

commitAndCloseQuietly（Connection conn）提交并关闭连接

rollbackAndCloseQuietly（Connection conn）回滚并关闭连接

### 综合案例
* 案例——删除
![](http://upload-images.jianshu.io/upload_images/2762413-dde9d58656ba0501.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 案例——查询1

```
public void fun1() throws SQLException {
		DataSource ds = JdbcUtils.getDataSource();
		QueryRunner qr = new QueryRunner(ds);
		String sql = "select * from tab_student where number=?";
		Map<String,Object> map = qr.query(sql, new MapHandler(), "S_2000");
		System.out.println(map);
	}
```
* 案例——查询2

```
public void fun2() throws SQLException {
		DataSource ds = JdbcUtils.getDataSource();
		QueryRunner qr = new QueryRunner(ds);
		String sql = "select * from tab_student where number=?";
		Student stu = qr.query(sql, new BeanHandler<Student>(Student.class), "S_2000");
		System.out.println(stu);
	}
```
### 八、JavaBean组件
* 概念：JavaBean就是一个类，在开发中常用于封装数据

* 特性
  1. 需要实现接口：java.io.Serializable （通常省略不写）
  2. 提供私有字段：private 类型 字段名;
  3. 提供getter/setter方法
  4. 提供无参函数

  * 举例
![](http://upload-images.jianshu.io/upload_images/2762413-0160736da1297bf0.png?imageMogr2/auto-orient/s