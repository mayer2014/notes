# CentOS 7 更新yum源

1.  备份原有的源
  
    **mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup**

2.  进入yum源目录
  
    **cd /etc/yum.repos.d**

3.  下载163源
  
    **wget http://mirrors.163.com/.help/CentOS7-Base-163.repo**

4.  清除yum缓存
  
    **yum clean all**

5.  缓存新yum源服务器的软件包信息
  
    **yum makecache**
