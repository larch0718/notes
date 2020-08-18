Ubuntu安装docker
====
### 卸载旧版本的docker
**运行代码**
```
sudo apt-get remove docker docker-engine docker.io containerd runc --purge
```

### 更新源
**运行命令**
```
sudo apt update
```

### 安装依赖
** 运行命令 **
```
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common --no-install-recommends
```

### 导入apt-key
**运行命令**
```
curl -fsSL https://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
```
### 添加仓库
```
sudo add-apt-repository \
   "deb [arch=amd64] https://mirrors.aliyun.com/docker-ce/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

### 安装docker
**运行命令**
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
### 验证是否安装完成
**运行命令**
```
docker --version
```
### 不使用sudo运行docker
**运行命令**
```
sudo usermod -aG docker $(whoami)
```
需要重启才会有效

### 开启/关闭docker服务
**运行命令**
```
# 开启服务
sudo service docker start
# 关闭服务
sudo service docker stop
```
