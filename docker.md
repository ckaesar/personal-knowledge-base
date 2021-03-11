## docker

### docker下安装Redis

###### 查看镜像来源

`$ docker search redis `

###### 获取最新版本的redis镜像

`$ docker pull redis`

###### 查看本地镜像

`$ docker images`

###### 下载redis.conf

文件[从官网下载](http://download.redis.io/redis-stable/redis.conf)

redis.conf配置文件放在/Users/chengkai/opt/data/redis目录下。

然后修改启动默认配置：

> ```
> bind 127.0.0.1 #注释掉这部分，用来限制redis只能本地访问
> protected-mode no #默认yes表示开启保护模式，用来限制redis只能本地访问
> daemonize no #默认no，改为yes意为以守护进程方式启动，可后台运行，除非kill进程（可选）；改为yes会使配置文件方式启动redis失败
> dir /Users/chengkai/opt/data/redis/data/ #输入本地redis数据库存放文件夹（可选）
> appendonly yes #redis持久化（可选）
> databases 20 #数据库个数，这里设置redis最多有20个数据库
> ```

### docker下安装MongoDB

###### 拉取MongoDB最新的镜像

`$ docker pull mongo:latest`

###### 运行启动命令

`$ docker run -p 27017:27017 -v /Users/chengkai/data:/data/db --name mongodb -d mongo`

>  -p 映射容器服务的 27017 端口到宿主机的 27017 端口。外部可以直接通过 宿主机 ip:27017 访问到 mongo 的服务
>
> -v 为设置容器的挂载目录，这里是将本机的“/data/mongo”目录挂载到容器中的/data/db中，作为 mongodb 的存储目录
>
> --name 为设置该容器的名称
>
> -d 设置容器以守护进程方式运行

###### 查看容器启动运行情况

`$ docker ps`

### docker下安装mysql

###### 查看可用的mysqll版本

`$ docker search mysql`

###### 拉取mysql最新版本的镜像

`$ docker pull mysql:latest`

###### 查看本地镜像是否已安装mysql

`$ docker images`	

###### 运行容器

`$ docker run -itd --name mysql-localhost -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql` 

###### 查看是否安装成功

`$ docker ps`

###### 进入容器

`$ docker exec -it ac9fdd1e17c6 bash`

> ac9fdd1e17c6为容器id

###### 登录mysql

`root@ac9fdd1e17c6:/# mysql -u root -p`

###### 配置文件和数据文件地址

```
$ cd /root/mysql/etc:/etc/mysql # mysql配置文件位置
$ cd /root/mysql/data:/var/lib/mysql # mysql数据文件位置
```

###### 用户密码

root/123456

### docker下修改postgresql的密码

###### 进入容器

`$ docker exec -it 480ed4ef8ad1 bash`

> 480ed4ef8ad1为CONTAINER ID

###### 使用postgres登录

`$ su postgres`

###### 连接数据库

`$  psql -U postgres`

###### 修改postgresql用户密码

`$ alter user postgres with password '123456'`

###### 退出数据库连接

`$  \q`

###### 用户密码

postgres/postgres
