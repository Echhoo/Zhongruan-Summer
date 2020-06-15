# 安装centOS遇到的坑和解决方法

## 安装VMware

> 大火都是软件工程的学生。。。

## 安装CentOS7

1. 下载CentOS Minimal
   > http://mirrors.aliyun.com/centos/7.8.2003/isos/x86_64/
2. 在VMware中安装centOS7
   > 这里选择的都是默认配置，20GB硬盘，1GB内存

## 配置CentOS7

### 配置网络

1. 虚拟机选择NAT模式
2. Mac终端获取vmnet8的gateway地址
   ```
   cat /Library/Preferences/VMware\ Fusion/vmnet8/nat.conf
   ```
   获得内容如下
   ```
   # NAT gateway address
   ip = 172.16.11.2
   netmask = 255.255.255.0
   ```
3. 修改Centos7中ifcfg-xxx文件
   centOS中
   ```
   cd /etc/sysconfig/network-scripts
   ```
   备份并ls获取文件，在我的MAC上获取的是ifcfg-ens33
   ```
   cp ./ifcfg-ens33 ./ifcfg-ens33.back
   ```
   编辑此文件，增加或修改BOOTPROTO,IPADDR,NETMASK,DNS1,DNS2,GATEWAY,ONBOOT配置。其中IPADDR为需要设定的静态ip值；NETMASK为mac的NETMASK；DNS1,DNS2也是mac中的dns配置；GATEWAY就是第2步中找到的gateway addr下的ip值
   同时更改IPV6_PRIVACY=no, PREFIX=24
   