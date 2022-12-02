# idea链接mysql配置

## 安装idea

https://download.jetbrains.com.cn/idea/ideaIC-2022.2.4.exe

![](../image/idea/30.png)
![](../image/idea/31.png)
![](../image/idea/32.png)

下图是重启，保存好后再finish

![](../image/idea/33.png)
![](../image/idea/34.png)
![](../image/idea/35.png)
![](../image/idea/36.png)

注意：下图中打开的是老师发的shiyi-blog master的项目，打开shiyi-blog-master文件夹里面的blog

![](../image/idea/37.png)


![](../image/idea/38.png)

至此idea配置完成且打开了老师的项目，继续mysql

## mysql配置

https://dev.mysql.com/downloads/mysql/

![](../image/idea/1.png)
![](../image/idea/2.png)

然后等待下载完成，下载的是zip压缩包

![](../image/idea/3.png)

将其完全解压出来（可以解压到别的地方）

并打开解压后的文件夹

![](../image/idea/4.png)

打开bin目录，复制并目录的路径名

![](../image/idea/5.png)

然后打开环境变量，在系统变量中双击path

![](../image/idea/6.png)

点击新建

![](../image/idea/7.png)

将刚复制的路径粘贴进去然后确定

![](../image/idea/8.png)

在mysql的根目录中新建用于初始化的my.ini文件

![](../image/idea/9.png)

将下面代码段复制进去(mysql的安装目录改成自己的，数据存放目录也要改)

```
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=E:\\software\\mysql\\mysql-8.0.11-winx64   # 切记此处一定要用双斜杠，单斜杠我这里会出错，不过看别人的教程，有的是单斜杠。自己尝试吧
# 设置mysql数据库的数据的存放目录
datadir=E:\\software\\mysql\\mysql-8.0.11-winx64\\Data   # 此处同上
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8
```

在搜索框中输入cmd并选择管理员身份运行

![](../image/idea/10.png)

先通过cd命令打开mysql根目录下的bin文件夹

![](../image/idea/11.png)

在此目录中输入mysqld --initialize --console

![](../image/idea/12.png)

等待运行完成后出现下图，红圈内的一串就是初始密码（无空格），在没有更新密码前，保存好这个密码，登录要用

![](../image/idea/13.png)

如下图继续输入mysqld --install [服务名]
后面的服务名可以不写，默认的名字为 mysql。如果你需要安装多个MySQL服务，就可以在[服务名]处起名字

![](../image/idea/14.png)

然后通过命令net start mysql启动MySQL服务

注：net stop mysql停止服务;sc delete MySQL/mysqld -remove卸载MySQL服务

![](../image/idea/15.png)

然后输入mysql -u root -p
会提示输入密码，这个密码就是之前生成的密码，输入进去

然后输入修改密码的命令
```ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';```
（新密码处填修改后的密码），打码的地方是输错了的，不用管

![](../image/idea/16.png)

mysql服务安装完成了，接下来需要下载驱动文件

进入链接：https://dev.mysql.com/downloads/connector/j/

按下图显示下载文件

![](../image/idea/20.png)

下载完成后将其全部解压到你需要的文件夹里面

然后打开idea
在右边栏选数据库，点开加号，选择数据源，在数据源中找到mysql

如果你右边没有数据库看下面两张图

![](../image/idea/44.png)

![](../image/idea/45.png)

安装完成后重启ide就行，然后叫base browser在左边

![](../image/idea/46.png)

![](../image/idea/47.png)

点击上图第三步会出现下图的结果

![](../image/idea/48.jpg)

然后打开文件，项目结构

![](../image/idea/27.png)

如下图说明操作，其中第二步的名字不一定一样，右边先选择依赖再执行第三步（导入的jar文件和前面设置驱动文件的jar文件一样）

![](../image/idea/28.png)

新建一个测试的java类，输入下面的代码运行

## 注意（我这个是新建的项目中调试的，如果你是直接打开的老师的博客代码，就不需要重新创建了，直接运行老师的就行 ##

```
import java.sql.*;
public class Test1 {
    public static void main(String[] args) throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        String url = "jdbc:mysql://localhost/mysql?user=root&password=123456";
        Connection conn = DriverManager.getConnection(url);
        DatabaseMetaData dbmd = conn.getMetaData();
        System.out.print("JDBC驱动程序："+dbmd.getDriverName()+","+dbmd.getDriverVersion()+"\nJDBC URL:"+dbmd.getURL()+"\n数据库:"+dbmd.getDatabaseProductName()+",版本:"+dbmd.getDatabaseProductVersion()+"，用户名:"+dbmd.getUserName());
        conn.close();
    }
}
```

代码中的password=这里填写的是你修改过后的密码

下图即为结果

![](../image/idea/29.png)

> 上面已将mysql成功连接idea

> 接下来可以看老师发的txt文件（后台运行步骤-1669294052067.txt）

老师给的步骤就不一步一步做了

注意点：

1.运行redis-server.exe时，弹出黑框后即刻闪退解决：

在你下载完redis并完全解压后，在地址栏中输入cmd，进入redis根目录的命令提示符

输入redis-server.exe redis.windows.conf

如下图（路径别错了，在redis根目录）

![](../image/idea/39.png)

所有内容都搭建好后会和下面几张图99%相似

1.redis

![](../image/idea/39.png)

2.navicat

![](../image/idea/43.png)

3.Android（按下图输入的mysql代码是能正常运行的）

![](../image/idea/41.png)

4.idea（博客也能正常运行）

![](../image/idea/42.png)
