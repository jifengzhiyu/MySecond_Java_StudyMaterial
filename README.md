# MySecond_Java_StudyMaterial
第二轮学习（系统）：黑马V12.5

# IDEA快捷键（Mac）

- Option 选取多列
- .sout--打印
- 变量+fori---for循环

# 依赖

- 数据库链接池Druid
- mybatis：

```xml
<!--mybatis-config.xml 并将该文件放置在 resources 下-->

<?xml version="1.0" encoding="UTF-8" ?> 
<!DOCTYPE configuration 
PUBLIC "-//mybatis.org//DTD Config 3.0//EN" 
"http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration> 
  <!--起别名--> 
  <typeAliases> 
    <package name="com.itheima.pojo"/>
  </typeAliases>
  
  <environments default="development"> 
    <environment id="development">
      <transactionManager type="JDBC"/> 
			<dataSource type="POOLED">
        <property name="driver" value="com.mysql.jdbc.Driver"/> 
        <!--useSSL:关闭SSL安全连接 性能更高 
				useServerPrepStmts:开启预编译功能
 				&amp; 等同于 & ,xml配置文件中不能直接写 &符号
 				--> 
        <property name="url" value="jdbc:mysql:///db1? useSSL=false&amp;useServerPrepStmts=true"/>
        <property name="username" value="root"/>
        <property name="password" value="1234"/>
      </dataSource> 
    </environment>
  </environments>
  <mappers> 
    <!--扫描mapper-->
    <package name="com.itheima.mapper"/>
  </mappers>
</configuration> 
```

```xml
<dependency> 
  <groupId>org.mybatis</groupId> 
  <artifactId>mybatis</artifactId>
  <version>3.5.5</version> 
</dependency>
```

- mysql驱动：

````xml
<dependency>
  <groupId>mysql</groupId> 
  <artifactId>mysql-connector-java</artifactId> 
  <version>5.1.34</version>
</dependency>
````

- junit单元测试：<groupId>junit</groupId> <artifactId>junit</artifactId>
- Logback-core依赖：<groupId>ch.qos.logback</groupId> <artifactId>logback-core</artifactId> +配置文件（彩色log）
- Servlet依赖

```xml
<dependency>
  <groupId>javax.servlet</groupId> 
  <artifactId>javax.servlet-api</artifactId> 
  <version>3.1.0</version>
  <!--此处为什么需要添加该标签? provided指的是在编译和测试过程中有效,最后生成的war包时不会加入 因为Tomcat的lib目录中已经有servlet-api这个jar包，如果在生成war包的时候生效就会和Tomcat中的jar包冲突，导致报错 -->
  <scope>provided</scope>
</dependency>
```

-  JSP依赖

```xml
<dependency> 
  <groupId>javax.servlet.jsp</groupId>
  <artifactId>jsp-api</artifactId>
  <version>2.2</version>
  <scope>provided</scope>
</dependency>
<!--该依赖的 scope 必须设置为 provided ，因为 tomcat 中有这个jar包了，所以在打包时我们是不希望将该依赖打进到我们
工程的war包中。-->
```

- JSP标准标签库(Jsp Standarded Tag Library) ，使用标签取代JSP页面上的Java代码

```xml
<dependency> 
  <groupId>jstl</groupId> 
  <artifactId>jstl</artifactId>
  <version>1.2</version>
</dependency> 

<dependency>
  <groupId>taglibs</groupId>
  <artifactId>standard</artifactId>
  <version>1.1.2</version>
</dependency> 
<!-->
在JSP页面上引入JSTL标签库
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
-->
```



# Maven插件

- 集成本地Tomcat8.5用的多；Tomcat插件支持到7

```xml
<build> 
  <plugins>
    <!--Tomcat插件 --> 
    <plugin>
      <groupId>org.apache.tomcat.maven</groupId>
      <artifactId>tomcat7-maven-plugin</artifactId> 
      <version>2.2</version> 
      <configuration>
        <port>80</port>
<!--访问端口号 -->
<!--项目访问路径 未配置访问路径: http://localhost:80/tomcat-demo2/a.html 
配置/后访问路径: http://localhost:80/a.html 
如果配置成 /hello,访问路径会变成什么? 答案: http://localhost:80/hello/a.html --> <path>/</path>
    </configuration>
    </plugin> 
  </plugins>
</build>
```



# IDEA插件

- Maven-Helper--快速进行Maven指令操作（快速启动项目，选中项目，右键-->Run/Debug Maven --> tomcat7:run）。
- MyBatisX--写接口自动生成映射文件的statment；映射文件和接口快速定位
- 
