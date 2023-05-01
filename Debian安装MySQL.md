# Debian安装MySQL

> Linux发行版：Debian 11

MySQL官网下载[deb文件](https://dev.mysql.com/downloads/repo/apt/)，

安装，

`sudo dpkg -i mysql-apt-config_0.8.25-1_all.deb`，

报错，`mysql-apt-config pre-depends on wget, wget is not installed.`，

缺少前置依赖项`wget`，执行安装，

`sudo apt-get install wget`，

重试安装MySQL deb文件，成功进入安装的设置界面，

当前安装的是mysql-8.0（可选mysql cluster），设置好后，选择ok退出设置界面，

更新，

`sudo apt-get update`，

软件库已经出现mysql的地址，

开始安装，

`sudo apt-get install mysql-server`，按照提示操作即可。

连接数据库，创建新的远程连接账户，

```sql
create user 'USER_NAME'@'%' indentified by 'PASSWORD'
```

完成！
