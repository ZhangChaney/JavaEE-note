# 009-整合Mybatis

## 一、添加依赖

在pom.xml文件中添加mybatis整合springboot的依赖以及mysql驱动

```xml
    <!--mybatis依赖-->
    <dependency>
      <groupId>org.mybatis.spring.boot</groupId>
      <artifactId>mybatis-spring-boot-starter</artifactId>
      <version>3.0.0</version>
    </dependency>
    <!--mysql驱动-->
    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.23</version>
    </dependency>
```

## 二、配置数据源

在application.yaml文件中配置数据库连接信息。

```yaml
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://1.95.0.144:3306/mybatis
    username: root
    password: 123456

#下划线转驼峰    
mybatis:
  configuration:
    map-underscore-to-camel-case: true
```

## 三、工程测试

在pojo包下新建实体类User

```java
public class User {
    private int userId;
    private String username;
    private String password;

    public int getUserId() {
        return userId;
    }

    public void setUserId(int userId) {
        this.userId = userId;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }


    @Override
    public String toString() {
        return "User{" +
                "userId=" + userId +
                ", username='" + username + '\'' +
                ", password='" + password + '\'' +
                '}';
    }
}
```

在mapper包下新建UserMapper接口

```java
@Mapper
public interface UserMapper {

    @Select("select * from user where user_id = #{userId}")
    User getUserById(Integer userId);

}
```

在service包下新建UserService接口

```java
public interface UserService {

    User getUserById(int userId);
}
```

在service包下新建impl包并创建UserServiceImpl实现类

```java
@Service
public class UserServiceImpl implements UserService {

//    @Autowired
    @Resource
    private UserMapper userMapper;

    @Override
    public User getUserById(int userId) {
        return userMapper.getUserById(userId);
    }
}
```

在controller包下新建UserController类

```java
@RestController
@RequestMapping
public class UserController {
    @Resource
    private UserService userService;

    @GetMapping("/user")
    public User getUserById(Integer userId) {
        return userService.getUserById(userId);
    }
}
```

在SprintBootTestApplication中启动程序，浏览器输入127.0.0.1:8888/start/user?userId=1测试，得到数据库中的数据。

```tex
{"userId":1,"username":"zhangsan","password":"123456"}
```

## 四、PostMan安装使用

课堂讲解。

## 五、课后作业

- 编写api接口，实现通过postman发送请求，对用户的添加，修改和删除操作









