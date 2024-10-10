# 005-logback配置

## 一、pom.xml文件中添加依赖

```xml
 <!-- slf4j日志 -->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>1.7.32</version>
        </dependency>
        <!-- logback-classic依赖 -->
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
            <version>1.2.11</version>
        </dependency>
        <!-- logback-core依赖 -->
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-core</artifactId>
            <version>1.2.11</version>
        </dependency>
```

## 二、创建logback.xml文件

在resources目录下创建logback.xml,内容如下

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration>
    <appender name="Console" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>[%level] %blue(%d{HH:mm:ss.SSSS}) %cyan([%thread]) %green(%logger{15}) - %msg %n</pattern>
        </encoder>
    </appender>

    <logger name="com.javaee" level="debug" additivity="false">
        <appender-ref ref="Console"/>
    </logger>
</configuration>
```

## 三、修改UserMapper.xml文件

将其中的namespace修改为com.javaee.ex01，内容如下

```xml
<mapper namespace="com.javaee.ex01">
    <select id="selectAllUser" resultType="com.javaee.ex01.pojo.User">
        select * from user;
    </select>
    <insert id="insertUser">
        insert into user(username, password) values(#{username}, #{password});
    </insert>
</mapper>
```

## 四、修改测试用例中的sql语句选择

```java
List<User> users = session.selectList("com.javaee.ex01.selectAllUser");
```

## 五、运行测试用例，查看是否有日志输出

```tex
[DEBUG] 08:40:52.0152 [main] c.j.e.selectAllUser - ==>  Preparing: select * from user; 
[DEBUG] 08:40:52.0211 [main] c.j.e.selectAllUser - ==> Parameters:  
[DEBUG] 08:40:52.0321 [main] c.j.e.selectAllUser - <==      Total: 5 
```

