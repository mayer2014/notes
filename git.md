# Git简要教程
> Git是一个分布式的版本控制系统，最初由Linus Torvalds编写，用作Linux内核代码的管理。    —— [百度百科](http://baike.baidu.com/link?url=oTyn9kHmPS2fiBhhZMYJztsVHGzxhxsORndyVKGm5soYJS68vrpsF7yRzM6gJEZf2Hcn3yrLE-MjIcCkNw1Cqq)  
  
#### 安装Git
* sudo apt-get install git (Debian系)
* yum install git (Red Hat系)
 
#### 设置用户名和邮箱
* git config --global user.name "Your Name"
* git config --global user.email "email@example.com"
 
#### 创建新的版本库
* mkdir git
* cd git
* git init

#### 提交文件
* echo "Git is a version control system.">>readme.txt
* git add readme.txt
* git commit -m "add readme"
