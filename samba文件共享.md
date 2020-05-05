samba文件共享
====

### 准备工作
**创建共享目录并给权限**
```
sudo mkdir /shared
sudo chmod 777 /shared
```

### 安装samba
```
sudo apt install samba --no-install-recommends
```

### 添加samba用户
```
sudo smbpasswd -a larch
```
### 配置samba（/etc/samba/smb.conf）
```
[public]
  security = user
  comment = "public shared"
  path = /shared
  browseable = yes
  read only = no
  guest ok = no
  create mask = 0664
  directory mask = 0775
  writeable = yes
  write list = larch
```

### 重启samba服务
```
sudo service smbd restart
```

### 开机启动samba服务
```
sudo systemctl enable smbd
```
