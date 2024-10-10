# 003-Idea连接MySQL

## Idea连接MySQL数据库

1. 按下图顺序依次点击

   ![image-20240909194828507](./assets/image-20240909194828507.png)

2. 配置数据库连接信息。

   ![image-20240909195115331](./assets/image-20240909195115331.png)

3. 配置连接完成后显示如下图。

   ![image-20240909195722684](./assets/image-20240909195722684.png)

4. 点击上图中红色部分，选择第一个all schema查看现有数据库，如下图

   ![image-20240909195817853](./assets/image-20240909195817853.png)

5. 右键顶层连接(mybatis)，依次选择new -> schema创建新数据库mybatis。

   ![image-20240909200010615](./assets/image-20240909200010615.png)

6. 配置新数据库mybatis如下图。

   ![image-20240909200106293](./assets/image-20240909200106293.png)

7. 选中新数据库mybatis，右键new -> table

   ![image-20240909200212036](./assets/image-20240909200212036.png)

8. 新建数据库user，配置如下。

   ![image-20240909200326112](./assets/image-20240909200326112.png)

9. 右键columns，new -> column配置如下

   ![image-20240909200442199](./assets/image-20240909200442199.png)

10. 将user_id设置为主键，右键user_id，new -> primary key

    ![image-20240909200618239](./assets/image-20240909200618239-1725883582380-19.png)

11. 继续重复第9步，分别创建username，password列，类型设置为varchar(64)，完成后ok，如下图。

    ![image-20240909201049003](./assets/image-20240909201049003.png)

12. 完成后右侧双击user表进行查看。

    ![image-20240909201137293](./assets/image-20240909201137293.png)



