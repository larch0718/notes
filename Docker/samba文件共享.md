Samba文件共享
====

### 准备工作
**创建共享文件夹并赋予权限**
```
sudo mkdir /shared
sudo chmod 775 /shared
```

### 拉取镜像
**运行命令**
```
docker pull dperson/samba
```

### 运行镜像，创建容器
**运行命令**
```
docker run -it -p 139:139 -p 445:445 \
-v /shared:/mount \
--name samba \
-d dperson/samba \
-p \
-u "larch;123456;1000;larch;1000" \
-g "force user = larch" \
-g "force group = larch" \
-s "public;/mount;yes;no;no;larch;larch;larch"
```
#### 说明
* 第1行映射端口
* 第2行映射目录
* 第3行设置容器的名称
* 第4行使用的镜像
* 第5行设置共享的所有权和权限
* 第6行以分号间隔，分别是：
	* 用户名
	* 密码
	* 用户ID(uid)
	* 所属组(group)
	* 组ID(gid)
* 第7行设置共享目录中创建的文件的所有者
* 第8行设置共享目录中创建的文件的所属组
* 第9行以分号为间隔，分别是：
	* 共享文件夹的名称；
	* 共享在samba容器中的路径；
	* 共享名称对所有工作组用户可见；
	* 不是只读（也就是说可写）；
	* 不允许guest用户；
	* 指定共享的所有权用户；
	* 指定共享的超级用户；
	* 指定具有写权限的用户；

**使用参考[官方文档](https://github.com/dperson/samba)**

### 开启/关闭容器
**运行命令**
```
docker start samba # 开启容器
docker stop samba #关闭容器
```
