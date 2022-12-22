# MySecond_Java_StudyMaterial
第二轮学习（系统）：黑马V12.5

# IDEA快捷键（Mac）

- Option 选取多列
- .sout--打印
- 变量+fori---for循环

# 依赖

- 数据库链接池Druid
- mybatis：<groupId>org.mybatis</groupId> <artifactId>mybatis</artifactId>+配置文件
- mysql驱动：<groupId>mysql</groupId><artifactId>mysql-connector-java</artifactId>
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
