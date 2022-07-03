@[TOC](Ubuntu/Linux系统安装(非虚拟机))

# 参考链接
[Ubuntu官方文档](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

### 具体步骤

+ Ubuntu官网，在下载中找到桌面版，如果想用服务器则选另一个，下载iso文件
+ 根据当前系统下载 balenaEtcher，安装后，打开。在第一个选项中选择刚才下载好的iso文件
![a\b\20220626223059_6c39fc322058d73b4894f50c37ff4157.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626223059_6c39fc322058d73b4894f50c37ff4157.png)
+ 准备一个空U盘
![a\b\20220626223129_50efe55e1ae6c776ad0ad8f53579c773.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626223129_50efe55e1ae6c776ad0ad8f53579c773.png)
+ 单击Flash
![a\b\20220626223204_38242274eb948bd0bf907f80f440e93e.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626223204_38242274eb948bd0bf907f80f440e93e.png)
![a\b\20220626223220_1df10f752445f459b52c08bcbc71e7cf.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626223220_1df10f752445f459b52c08bcbc71e7cf.png)

经过上述步骤，U盘配置好后，插入要装linux的电脑，重启进入BIOS界面配置U盘启动。
之后步骤参考[4. Boot from USB flash drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

### 可能遇到的问题及解决方案
我的旧电脑用了太多年了，BIOS界面怎么也进不去，最后把硬盘全格式化了，电脑开机识别不到任何系统，然后用U盘启动的。

##### U盘格式化失败，写保护,磁盘管理显示RAW
![a\b\20220626225449_c12cfa9fd4c8557fc798276f716a8fcc.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626225449_c12cfa9fd4c8557fc798276f716a8fcc.png)
参考[如何在Windows 11/10/8/7 中格式化U盘的RAW？](https://www.disktool.cn/content-center/format-raw-file-system-pen-drive-2111.html)
```shell
diskpart   //cmd.exe命令
list disk（根据列表磁盘信息，检查哪个磁盘是您的U盘）
select disk #（# 是您的RAW文件系统U盘的编号）
clean
create partition primary
format fs=ntfs（或者输入：format fs=fat32）// 可能时间很长，我当时直接把U盘拔了再插上，正常格式化就好了
assign
```
![a\b\20220626230027_a3ded73084c0113f323c69c3b0148058.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626230027_a3ded73084c0113f323c69c3b0148058.png)

![a\b\20220626230006_8b08436af4ff3fdd61f9200c1a2ed274.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626230006_8b08436af4ff3fdd61f9200c1a2ed274.png)
clean
create partition primary
![a\b\20220626230244_f6fbc1a31d5f6bcd9417347535e1c83b.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626230244_f6fbc1a31d5f6bcd9417347535e1c83b.png)
format fs=ntfs 后时间很长，直接拔掉，正常格式化
![a\b\20220626230517_8c4fee99d41db1cc679bba3820cc5de0.png](https://lcg-pic-tencent-1258286866.cos.ap-chengdu.myqcloud.com/a%5Cb%5C20220626230517_8c4fee99d41db1cc679bba3820cc5de0.png)

##### 其他

[安装ubuntu出现的EFI boot partition问题](https://blog.csdn.net/visoprkx/article/details/85390254)
[linux系统硬盘需要分区吗,Linux下为什么要进行磁盘的分区](https://blog.csdn.net/weixin_30939909/article/details/116608072)
[Linux——磁盘分区选择、目录树结构、文件系统、挂载](https://blog.51cto.com/u_14149663/5067030#:~:text=A%EF%BC%9A%E5%88%9D%E6%AC%A1%E6%8E%A5%E8%A7%A6Linux%EF%BC%9A%E5%8F%AA%E8%A6%81%E5%88%86%E5%8C%BA%E3%80%8E%20%2F%20%E3%80%8F%E5%8F%8A%E3%80%8Eswap%E3%80%8F%E5%8D%B3%E5%8F%AF%EF%BC%9A%20%E9%80%9A%E5%B8%B8%E5%88%9D%E6%AC%A1%E5%AE%89%E8%A3%85,Linux%20%E7%B3%BB%E7%BB%9F%E7%9A%84%E6%9C%8B%E5%8F%8B%E4%BB%AC%EF%BC%8C%E6%88%91%E4%BB%AC%E9%83%BD%E4%BC%9A%E5%BB%BA%E8%AE%AE%E4%BB%96%E7%9B%B4%E6%8E%A5%E4%BB%A5%E4%B8%80%E4%B8%AA%E6%9C%80%E5%A4%A7%E7%9A%84%E5%88%86%E5%8C%BA%E6%A7%BD%E3%80%8E%20%2F%20%E3%80%8F%E6%9D%A5%E5%AE%89%E8%A3%85%E7%B3%BB%E7%BB%9F%E3%80%82)
[Linux系统安装时分区的选择（推荐）](https://blog.csdn.net/linjcai/article/details/81033048)
[sda1，sda2，sdb1，hda1是什么东西](https://blog.csdn.net/u013176681/article/details/37764567)
[Linux：COW 写时拷贝技术](https://blog.csdn.net/lqy971966/article/details/118784913?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-118784913-blog-116640140.pc_relevant_paycolumn_v3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-118784913-blog-116640140.pc_relevant_paycolumn_v3&utm_relevant_index=4)
[COW、ROW快照技术原理](https://support.huawei.com/enterprise/zh/doc/EDOC1100196336)