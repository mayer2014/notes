# CentOS 7 更新yum源
> * 备份原有的源
``` shell
 mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```
* 进入yum源目录
``` shell
 cd /etc/yum.repos.d
```
* 下载163源
``` shell
 wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
```
* 清除yum缓存
``` shell
 yum clean all
```
* 缓存新yum源服务器的软件包信息
``` shell
 yum makecache
```
