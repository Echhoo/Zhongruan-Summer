# yum
```
yum -y update
```
升级所有包同时也升级软件和系统内核
 
```
yum -y upgrade 
```
只升级所有包，不升级软件和系统内核 

```
yum check-update
```
检测可更新软件包
```
yum update <package_name>　　
```
更新指定包
```
yum update --security　　
```
安全更新

```
yum install
yum remove
yum list
```
```
yum list pam*
```
找出所有以pam开头的包