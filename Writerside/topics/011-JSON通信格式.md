# 011-JSON通信格式

在实际生产开发过程中，前端和后端之间的通信的数据一般使用JSON格式作为规范。

可以使用浏览器抓包工具查看，参考豆瓣电影。https://movie.douban.com/

JSON格式数据如下：

```json
{
            "episodes_info": "30集全",
            "rate": "",
            "cover_x": 5512,
            "title": "迎风的青春",
            "url": "https:\/\/movie.douban.com\/subject\/36481598\/",
            "playable": true,
            "cover": "https://img3.doubanio.com\/view\/photo\/s_ratio_poster\/public\/p2910682117.jpg",
            "id": "36481598",
            "cover_y": 8269,
            "is_new": false
        }



{"code": 200, "message": "查询成功", data: [user1, user2, user3 ]}
```

> 注意：JSON格式数据虽然与Python中的字典数据格式类似，但JSON格式中的键名为严格的双引号，不能使用单引号。

## 1.返回JSON格式数据

在springboot程序中，controller如果直接返回一个对象，springboot会直接转换成JSON数据进行返回。但返回值为基本数据类型时，就需要自行封装成JSON格式返回。

此时可以新建一个pojo类Result专门用于基本数据类型返回，一般需要包含以下三项

- code：返回码，前端用于校验返回结果；
- message：返回信息；
- data：需要返回的数据；

示例Result如下：

```java
public class Result<T> {
    private Integer code;
    private String message;
    private T data;


    public static <E> Result<E> success(E data){
        return new Result<>(1, "操作成功", data);
    }

    public static Result success(){
        return new Result(1, "操作成功", null);
    }

    public static Result error(String message){
        return new Result(-1, message, null);
    }

    public Result() {
    }

    public Result(Integer code, String message, T data) {
        this.code = code;
        this.message = message;
        this.data = data;
    }

    public Integer getCode() {
        return code;
    }

    public void setCode(Integer code) {
        this.code = code;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }
}
```

此时我们可以尝试将我们原有的添加用户接口修改为JSON格式返回，修改UserController中的添加用户接口；

```java
@PostMapping("/insertUser")
public Result insertUser(User user) {
    int row = userService.insertUser(user);
    if (row > 0) {
        return Result.success();
    }
    return Result.error("添加用户失败");
}
```

#### 课堂练习： 将修改和删除用户接口也修改为JSON格式返回并测试。 {id="json_1"}

## 2. 接收JSON格式的数据

在SpringBoot程序中，可以通过@RequestBody注解来解析请求中快速携带的JSON数据。

可以使用postman工具对springboot程序发送JSON数据。

在请求url下方依次选择Body -> raw，在下方输入需要发送的JSON数据，

```json
{
    "userId": 1001,
    "username": "zhangsan",
    "password": "123456"
}
```

在SpringBoot程序中，新建一个测试接口，在TestController中新建方法，

```java
@GetMapping("/json")
public String json(@RequestBody User user) {
    System.out.println(user);
    return "hello world!";
}
```

重启程序使用postman发送JSON数据，在控制台查看输出。

```text
User{userId=1001, username='zhangsan', password='123456'}
```

#### 课堂练习： 将修改和添加用户的请求接口也修改为JSON格式接收并发送数据进行测试。