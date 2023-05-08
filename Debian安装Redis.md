# Debian安装Redis

> Linux发行版：Debian 11

安装过程在[Redis官网](https://redis.io/docs/getting-started/)有详细的介绍，

导入Redis资源索引，并进行安装，

1. `curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg`
2. `echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list`
3. `sudo apt-get update`
4. `sudo apt-get install redis`

> `curl command not found`是因为curl命令未安装，执行`sudo apt install curl -y`安装。

测试Redis是否可用，执行命令`redis-cli ping`，返回`PONG`表明已可用。

或者，执行命令`sudo systemctl status redis-server`，查看Redis运行状态。

Redis默认只能本地连接，远程连接需要注释掉`/etc/redis/redis.conf`中的`bind 127.0.0.1 -::1`。

远程连接默认开启保护模式，可以在`redis.conf`中将`protected-mode yes`改为`no`，将保护模式关闭，或者，在`requirepass`配置行中设置密码。

完成后，执行命令`sudo systemctl restart redis-server`，重启redis。

如果使用了ufw防火墙，需要允许redis端口远程连接，执行命令`sudo ufw allow redis`。

> 如果没有配置用户名，远程连接时的用户名为`default`，也可以不填写用户名
