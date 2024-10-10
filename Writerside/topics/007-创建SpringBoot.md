# 007-创建SpringBoot

## 一、Idea新建项目

1.点击Idea新建项目，选择Empty Project（空项目）,项目名为SpringBoot

2.打开项目后，点击file -> settings配置本地maven后确定

3.点击file -> project structure，在project中选择jdk版本(1.8.0_1.31)和java level(java 8)后确定。

4.右键顶层目录，选择new -> module，左侧选择Maven项目，模块名称为SprintBootTest，创建空Maven项目。

5.删除resources目录下的所有内容，创建src/main/java目录，并新建com.javaee包。

6.创建src/test/java目录，并新建com.javaee包。

7.修改pom.xml文件，改成下面内容。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.javaee</groupId>
  <artifactId>SprintBootTest</artifactId>
  <version>1.0-SNAPSHOT</version>

  <properties>
    <maven.compiler.source>8</maven.compiler.source>
    <maven.compiler.target>8</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

  <dependencies>

  </dependencies>

</project>
```

## 二、构建SpringBoot构建

1.在pom.xml文件中添加springboot继承，添加位置为groupId标签上方，添加以下内容

```xml
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.7.6</version>
  </parent>
```

2.在dependencies标签中添加springmvc启动依赖，添加内容如下：

```xml
 <!--springboot工程依赖-->
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
```

添加完成后刷新maven检查依赖是否引入

## 三、工程项目搭建

1.在com.javaee包下分别新建controller,mapper,pojo,service四个包

2.在com.javaee包下新建启动类SprintBootTestApplication，代码如下

```java
@SpringBootApplication
public class SprintBootTestApplication {
    public static void main(String[] args) {
        SpringApplication.run(SprintBootTestApplication.class, args);
    }
}

```

3.在controller包下新建TestController类，内容如下：

```java
@RestController
@RequestMapping
public class TestController {
    @GetMapping("/test")
    public String test() {
        return "hello world!";
    }
}

```

## 四、启动测试

1.在BookManagerApplication类中启动程序。

2.在浏览器中输入127.0.0.1:8080/test测试是否可以访问。







