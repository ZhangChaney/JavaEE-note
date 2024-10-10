# 017-ElementPlus安装使用

官网及文档：https://element-plus.org/zh-CN/

## 安装引入

npm命令行安装

```sh
npm install element-plus --save
```

在main.ts文件中加入以下内容，全局引入

```ts
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'

// 引入ElementPlus
app.use(ElementPlus)
```

## 测试

将**Home.vue**中的路由标签`RouterLink`修改为用ElmentPlus的按钮标签装饰，查看是否生效

```vue
  <el-button type="primary">
    <RouterLink to="/child-01">第一个子路由</RouterLink>
  </el-button>
```
