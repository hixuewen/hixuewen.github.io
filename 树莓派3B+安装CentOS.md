## 下载镜像

下载链接： https://mirrors.xtom.com/centos-altarch/7.9.2009/isos/armhfp/

 ![image-20220213134124817](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213134124817.png)

## 烧写镜像

 ![image-20220213133944977](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213133944977.png)

## 配置IP

电脑保留1个网口，将其配置为静态IP（192.168.0.xxx）,用网线将其与树莓派连接

 ![image-20220213140607953](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213140607953.png)

 开启Open DHCP Server，打开http://127.0.0.1:6789/查看树莓派获取到的IP地址![image-20220213140647217](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213140647217.png)

然后ssh链接上去

 ![image-20220213140802454](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213140802454.png)

再通过nmtui命令配置WIFI

 ![image-20220213141238580](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213141238580.png)

## 拓展SD卡空间

```
在终端中输入fdisk /dev/mmcblk0进入硬盘分区软件 
在软件中输入： 
p——查看旧分区情况 
d——删除分区，并按照提示删除第三个分区 
n——添加一个分区，空间起始位置按照系统默认（默认是最大空间）  //这里特别注意分区开始位置要与p命令查到的一致 
p——查看新分区情况 
w——写入分区信息并退出软件 
在终端中输入：reboot重启树莓派 
在树莓派开机后在终端输入：resize2fs /dev/mmcblk0p3重新加载分区信息
```



## 更换华为源

 ![image-20220213145743953](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213145743953.png)

```
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#
#
 
[base]
name=CentOS-$releasever - Base - mirrors.huaweicloud.com
baseurl=https://mirrors.huaweicloud.com/centos-altarch/$releasever/os/$basearch/
gpgcheck=1
gpgkey=https://mirrors.huaweicloud.com/centos-altarch/$releasever/os/$basearch/RPM-GPG-KEY-CentOS-7
 
#released updates 
[updates]
name=CentOS-$releasever - Updates - mirrors.huaweicloud.com
baseurl=https://mirrors.huaweicloud.com/centos-altarch/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=https://mirrors.huaweicloud.com/centos-altarch/$releasever/os/$basearch/RPM-GPG-KEY-CentOS-7
 
#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras - mirrors.huaweicloud.com
baseurl=https://mirrors.huaweicloud.com/centos-altarch/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=https://mirrors.huaweicloud.com/centos-altarch/$releasever/os/$basearch/RPM-GPG-KEY-CentOS-7
 
#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus - mirrors.huaweicloud.com
baseurl=https://mirrors.huaweicloud.com/centos-altarch/$releasever/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://mirrors.huaweicloud.com/centos-altarch/$releasever/os/$basearch/RPM-GPG-KEY-CentOS-7
```

```
#CentOS-armhfp-kernel.repo 
[centos-kernel]
name=CentOS Kernels for armhfp
baseurl=https://repo.huaweicloud.com/centos-altarch/$releasever/kernel/$basearch/kernel-$kvariant
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
       file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-AltArch-Arm32
```

 ![image-20220213145957740](https://oobbss.oss-cn-shenzhen.aliyuncs.com/image-20220213145957740.png)