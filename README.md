# MySecond_Java_StudyMaterial
第二轮学习（系统）：黑马V12.5

# IDEA快捷键（Mac）

- Option 选取多列
- .sout--打印
- 变量+fori---for循环

# 依赖

## 数据库链接池Druid

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.1.16</version>
</dependency>

<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.1.23</version>
</dependency>
```

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.1.23</version>
</dependency>
```

## c3p0连接池

```xml
<dependency>
    <groupId>c3p0</groupId>
    <artifactId>c3p0</artifactId>
    <version>0.9.1.2</version>
</dependency>
```

## mybatis

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

```xml
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.3.0</version>
</dependency>
```

## mybatisPlus

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.4.1</version>
</dependency>

<!--代码生成器-->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-generator</artifactId>
    <version>3.4.1</version>
</dependency>

<!--velocity模板引擎-->
<dependency>
    <groupId>org.apache.velocity</groupId>
    <artifactId>velocity-engine-core</artifactId>
    <version>2.3</version>
</dependency>
```

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.4.2</version>
</dependency>
```

## mysql connector 驱动

mysql-connector-java 是mysql实现的java客户端；用来和mysql交互；

````xml
<dependency>
  <groupId>mysql</groupId> 
  <artifactId>mysql-connector-java</artifactId> 
  <version>5.1.34</version>
</dependency>
````

SpringBoot里：

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

junit单元测试

```xml
<dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>4.12</version>
</dependency>
```

```xml
<!--spring整合junit-->
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-test</artifactId>
  <version>5.1.9.RELEASE</version>
</dependency>
<!--junit的依赖至少要是4.12版本,可以是4.13等版本-->
```

## Logback-core依赖

<groupId>ch.qos.logback</groupId> <artifactId>logback-core</artifactId> +配置文件（彩色log）



## Servlet依赖

```xml
<dependency>
  <groupId>javax.servlet</groupId> 
  <artifactId>javax.servlet-api</artifactId> 
  <version>3.1.0</version>
  <!--此处为什么需要添加该标签? provided指的是在编译和测试过程中有效,最后生成的war包时不会加入 因为Tomcat的lib目录中已经有servlet-api这个jar包，如果在生成war包的时候生效就会和Tomcat中的jar包冲突，导致报错 -->
  <scope>provided</scope>
</dependency>
```

## JSP依赖

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

## JSP标准标签库

(Jsp Standarded Tag Library) 

- 使用标签取代JSP页面上的Java代码

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

## Spring 

```xml
<dependencies>
    <!--导入spring的坐标spring-context，对应版本是5.2.10.RELEASE-->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>
</dependencies>
```

## javax.annotation

@PostConstruct和@PreDestroy注解是jdk中提供的注解，从jdk9开始，jdk中的javax.annotation包被移除了，也就是说这两个注解就用不了了，可以额外导入一下依赖解决这个问题。

```xml
<dependency>
  <groupId>javax.annotation</groupId>
  <artifactId>javax.annotation-api</artifactId>
  <version>1.3.2</version>
</dependency>
```

## AOP

```xml
<dependencies>
    <!--spring核心依赖，会将spring-aop传递进来-->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>
<!--切入点表达式依赖，目的是找到切入点方法，也就是找到要增强的方法-->
    <dependency>
        <groupId>org.aspectj</groupId>
        <artifactId>aspectjweaver</artifactId>
        <version>1.9.4</version>
    </dependency>
</dependencies>
```

## SpringMVC+Servlet

```xml
<dependencies>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <scope>provided</scope>
    </dependency>
  <!--导入spring-webmvc坐标自动依赖spring相关坐标-->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>
</dependencies>
```

## JSON相关

### Fastjson  

spring boot默认使用的json解析框架是jackson,使用fastjson需要配置

是阿里巴巴提供的一个Java语言编写的高性能功能完善的 ，是目前Java语言中最快的 JSON 库，可以实现 Java 对象和 JSON 字符串的相互转换。

```xml
<dependency>
  <groupId>com.alibaba</groupId>
  <artifactId>fastjson</artifactId>
  <version>1.2.76</version>
</dependency>

<!--
Java对象转JSON
String jsonStr = JSON.toJSONString(obj);

JSON字符串转Java对象
User user = JSON.parseObject(jsonStr, User.class);
-->
```

### Jackson

- 添加json数据转换相关坐标

```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.9.0</version>
</dependency>
```

## SSM

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>

    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-jdbc</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>

    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-test</artifactId>
        <version>5.2.10.RELEASE</version>
    </dependency>

    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis</artifactId>
        <version>3.5.6</version>
    </dependency>

    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis-spring</artifactId>
        <version>1.3.0</version>
    </dependency>

    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>5.1.47</version>
    </dependency>

    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>druid</artifactId>
        <version>1.1.16</version>
    </dependency>

    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>

    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <scope>provided</scope>
    </dependency>

    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
        <version>2.9.0</version>
    </dependency>
</dependencies>

<build>
    <plugins>
        <plugin>
            <groupId>org.apache.tomcat.maven</groupId>
            <artifactId>tomcat7-maven-plugin</artifactId>
            <version>2.1</version>
            <configuration>
                <port>80</port>
                <path>/</path>
            </configuration>
        </plugin>
    </plugins>
</build>
```

## SpringBoot整合JUnit

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

## commons-lang

CommonsLang是对JDK中java.lang包的补充，提供了各种各样的Utilities工具类

```xml
<dependency>
  <groupId>commons-lang</groupId>
  <artifactId>commons-lang</artifactId>
  <version>2.6</version> 
</dependency>
```

##  Lombok

简化POJO实体类开发，@Data，@Slf4j

```xml
 	<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.20</version>
</dependency>
```

## Jedis

 是 Redis 的 Java 版本的客户端实现。

```xml
<dependency>
	<groupId>redis.clients</groupId>
	<artifactId>jedis</artifactId>
	<version>2.8.0</version>
</dependency>
```

## Redis相关

### Spring Data Redis 

Spring Data Redis 是 Spring 的一部分，提供了在 Spring 应用中通过简单的配置就可以访问 Redis 服务，对 Redis 底层开发包进行了高度封装。在 Spring 项目中，可以使用Spring Data Redis来简化 Redis 操作。

Spring **对 Redis 客户端进行了整合**（比如jedis），提供了 Spring Data Redis，在Spring Boot项目中还提供了对应的Starter，即 spring-boot-starter-data-redis。

maven坐标：

~~~xml
<dependency>
	<groupId>org.springframework.data</groupId>
	<artifactId>spring-data-redis</artifactId>
	<version>2.4.8</version>
</dependency>
~~~

Spring Boot提供了对应的Starter，maven坐标：

~~~xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
~~~

###  SpringCache

基于注解的缓存功能

在项目中使用，我们会选择使用redis来做缓存，主要需要操作以下几步： 

pom.xml

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-cache</artifactId>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

## ShardingJDBC

Sharding-JDBC定位为轻量级Java框架，在Java的JDBC层提供的额外服务。 它使用客户端直连数据库，以jar包形式提供服务，无需额外部署和依赖，可理解为增强版的JDBC驱动，完全兼容JDBC和各种ORM框架。

使用Sharding-JDBC可以在程序中轻松的实现数据库读写分离。

Sharding-JDBC具有以下几个特点： 

1). 适用于任何基于JDBC的ORM框架，如：JPA, Hibernate, Mybatis, Spring JDBC Template或直接使用JDBC。

2). 支持任何第三方的数据库连接池，如：DBCP, C3P0, BoneCP, Druid, HikariCP等。

3). 支持任意实现JDBC规范的数据库。目前支持MySQL，Oracle，SQLServer，PostgreSQL以及任何遵循SQL92标准的数据库。



依赖: 

```xml
<dependency>
    <groupId>org.apache.shardingsphere</groupId>
    <artifactId>sharding-jdbc-spring-boot-starter</artifactId>
    <version>4.0.0-RC1</version>
</dependency>
```

# Maven插件

## Tomcat

- 集成本地Tomcat8.5用的多；Tomcat插件支持到7
- tomcat 8.5版本之后GET请求就不再出现中文乱码问题，但是我们使用的是tomcat7插件，所以会出现GET请求中文乱码问题。
- 在pom.xml添加tomcat7插件处配置UTF-8字符集，解决GET请求中文乱码问题。

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

```xml
<!--解决GET请求中文乱码问题-->
<build>
    <plugins>
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.1</version>
        <configuration>
          <port>80</port><!--tomcat端口号-->
          <path>/</path> <!--虚拟目录-->
          <uriEncoding>UTF-8</uriEncoding><!--访问路径编解码字符集-->
        </configuration>
      </plugin>
    </plugins>
  </build>
```

## spring-boot-maven-plugin

https://docs.spring.io/spring-boot/docs/2.2.1.RELEASE/maven-plugin/

https://www.cnblogs.com/acm-bingzi/p/mavenSpringBootPlugin.html

maven项目的pom.xml中，添加了*org.springframework.boot:spring-boot-maven-plugin*插件，当运行“mvn package”进行打包时，会打包成一个可以直接运行的 JAR 文件，使用“Java -jar”命令就可以直接运行。

```xml
<plugins>
  <plugin>
    <groupId>org.springframework.boot</groupId> 
    <artifactId>spring-boot-maven-plugin</artifactId>
    <version>2.4.5</version>
  </plugin> 
</plugins>
```



# IDEA插件

- Maven-Helper--快速进行Maven指令操作（快速启动项目，选中项目，右键-->Run/Debug Maven --> tomcat7:run）。
- MyBatisX--写接口自动生成映射文件的statment；映射文件和接口快速定位
- 

# APP

## IDEA

## Navicat

## PostMan

