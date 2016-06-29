# Git简要教程
> Git是一个分布式的版本控制系统，最初由Linus Torvalds编写，用作Linux内核代码的管理。    —— [百度百科](http://baike.baidu.com/link?url=oTyn9kHmPS2fiBhhZMYJztsVHGzxhxsORndyVKGm5soYJS68vrpsF7yRzM6gJEZf2Hcn3yrLE-MjIcCkNw1Cqq)  
  
#### 安装Git
``` shell
sudo apt-get install git (Debian系)
yum install git (Red Hat系)
```

#### 设置用户名和邮箱
``` shell
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```

#### 创建新的版本库
``` shell
mkdir git
cd git
git init
```

#### 提交文件
``` shell
echo "Git is a version control system.">>readme.txt
git add readme.txt
git commit -m "add readme"
```

#### 查看状态
``` shell
git status
```

#### 查看修改内容
``` shell
git diff readme.txt
```

#### 查看日志
``` shell
git log
```

#### 查看操作日志
``` shell
git reflog
```

#### 版本回退
``` shell
git reset --hard HEAD^
```

#### 撤销工作区修改
``` shell
git checkout -- readme.txt
```

#### 撤销暂存区修改
``` shell
git reset HEAD readme.txt
```

#### 删除文件
``` shell
git rm readme.txt
```
#### 创建SSH Key
> 在用户主目录里查看是否存在.ssh目录，里面是否有id_rsa和id_rsa.pub两个文件，如果存在，则跳过这一步。
``` shell
ssh-keygen -t rsa -C "youremail@example.com"
```
