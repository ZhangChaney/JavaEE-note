# 013-Vite创建Vue3工程

## 一、环境准备

- 下载安装好nodejs
- 下载安装好webstorm或者vscode

## 二、创建工程

进入需要创建项目的目录，在地址栏输入cmd回车打开命令行窗口。

![image-20240925211807172](./assets/image-20240925211807172.png)

![image-20240925211819479](./assets/image-20240925211819479.png)

在命令行窗口输入以下命令创建项目

```shell
npm init vite
# 如果提示询问y/n则输入y然后回车
```

项目名输入`class01`回车

框架选择`Vue`回车

语法选择`TypeScript`回车

![image-20240925212127510](./assets/image-20240925212127510.png)

此时在回到项目目录可以看到项目已经完成构建，项目目录下成功创建了一个class01的文件夹

![image-20240925212230695](./assets/image-20240925212230695.png)

此时项目构建成功，使用webstorm打开该文件夹。

![image-20240925212353753](./assets/image-20240925212353753.png)



## 三、安装依赖包并启动

使用webstorm打开项目后，找到终端按钮并打开（一般在左下角，和你的cmd窗口长得一样，输入命令的）

![image-20240925213002186](./assets/image-20240925213002186.png)

打开后先换源，在终端中输入如下命令

```shell
npm config set registry https://registry.npmmirror.com/
```

![image-20240925213121718](./assets/image-20240925213121718.png)

然后输入下方`npm i`安装依赖包

![image-20240925213216658](./assets/image-20240925213216658.png)

完成后输入`npm run dev`启动项目

![image-20240925213252949](./assets/image-20240925213252949.png)

点击链接打开项目页面

![image-20240925213335081](./assets/image-20240925213335081.png)

完成项目构建！

