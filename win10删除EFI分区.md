win10 删除EFI分区
====

### 1. win+r，输入cmd，打开命令提示符窗口

### 2. 输入diskpart命令

### 3. 在打开的新窗口中，输入list disk命令，可以看到输出了两个磁盘
![img1](./IMG/IMG_001.png)

### 4. 根据磁盘的编号选中相应的磁盘(0或1)，使用sel disk 1即可选中磁盘1
**至于要选0还是1，就要看要删除的EFI分区在哪个磁盘中**
![img2](./IMG/IMG_002.png)

### 5. 输入list partition命令查看该磁盘下的分区
![img3](./IMG/IMG_003.png)

### 6. 选中系统分区sel partition 7	
![img4](./IMG/IMG_004.png)

### 7. 最后执行下面的命令
```
	SET ID=ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
```
![img5](./IMG/IMG_005.png)

在磁盘管理中EFI分区就可以删除了

### 完整截图
![img6](./IMG/IMG_006.png)

参考文件链接: [windows10删除EFI分区(绝对安全)](https://blog.csdn.net/sinat_29957455/article/details/88726797)