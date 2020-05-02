reids
====

### 准备工作
* 创建配置文件保存目录
```
sudo mkdir /usr/local/docker/redis/conf
```
* 创建持久化数据保存目录
```
sudo mkdir /usr/local/docker/redis/data
```

### 拉取镜像
```
docker pull redis
```

### 运行镜像，创建容器
1、 下载redis配置文件
```
sudo wget http://download.redis.io/redis-stable/redis.conf -P /usr/local/docker/redis/conf
```

2、 创建容器
```
docker run --name redis \
-d \
-p 6379:6379 \
-v /usr/local/docker/redis/conf:/etc/redis \
-v /usr/local/docker/redis/data:/data \
redis \
redis-server /etc/redis/redis.conf
```

### 创建宿主机redis-cli命令
1、创建redis-cli文件
```
sudo touch  /usr/local/docker/bin/redis-cli
sudo chmod +x /usr/local/docker/bin/redis-cli
```
2、 redis-cli文件中填入以下内容：
```
#!/bin/bash
res=$(docker ps | grep -c redis)
if (( ${res} == 0 ));then
        echo "redis容器未创建或者未启动"
        exit 1
fi
docker exec -it redis redis-cli "$@"
exit 0
```
3、 调用
```
/usr/local/docker/bin/redis-cli #直接调用
redis-cli #将/usr/local/docker/bin加入到环境变量中后才可以这么调用
```