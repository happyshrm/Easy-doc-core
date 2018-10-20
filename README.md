![logo](logo.png)
# Easy-Doc
简单易用的java接口文档生成，基于javadoc生成接口文档，对代码0侵入。

提供接口文档展示，调用测试，压力测试，mock数据(开发中)等功能，目前已上传测试版本，可以使用

# 原理
- 基于反射和正则表达式实现，依赖于spring，并且需要对源文件进行扫描。
- 核心扫描方法为DocReader中的singleReader
- 核心渲染方法为BaseReader中的render
- 所有反射相关的操作都位于ReflectUtils
- jar包生成接口文档需要使用插件处理 

# 引入依赖方法
使用maven引入
```xml
<repositories>
    <repository>
	<id>oss</id>
	<name>oss</name>
	<url>https://oss.sonatype.org/content/groups/public</url>
    </repository>
    <repository>
        <id>aliyun-repository</id>
        <name>aliyun repository</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    </repository>
</repositories>

<dependency>
    <groupId>com.stalary</groupId>
    <artifactId>easy-doc</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```

# 初始化配置
如果source设置为false

使用maven需要[easydoc-maven-plugin](https://github.com/Easy-doc/easydoc-maven-plugin)

使用gradle需要[easydoc-gradle-plugin](https://github.com/Easy-doc/easydoc-gradle-plugin)

生成一份过滤后的源码文件


```yml
com:
  stalary:
    easydoc:
      name: swagger demo # 项目名称
      contact: stalary@613.com # 项目联系人
      description: swagger测试项目 # 项目描述
      path: com.stalary.swagger # 解析的包路径(包括data和controller的包)
      open: true # 是否开启
      source: true # 是否读取源码,false则为读取resources中的easydoc.txt
```

# 注释书写规则

> demo具体可以查看ResourceController|TestBody|TestResponse等


注释名 | 解释
--- | ---
@method | 方法名   
@description | 类/方法/实体描述
@author | 类作者
@throws | 抛出的异常
@return | 方法返回值，第一行为code 介绍，后面为对应code的每个参数的含义
@param | 参数名
@model | 实体标识
@field | 实体的参数

# 返回样例
[接口地址](http://easydoc.stalary.com/api)