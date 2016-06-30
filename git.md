# Git简要教程
> Git是一个分布式的版本控制系统，最初由Linus Torvalds编写，用作Linux内核代码的管理。    —— [百度百科](http://baike.baidu.com/link?url=oTyn9kHmPS2fiBhhZMYJztsVHGzxhxsORndyVKGm5soYJS68vrpsF7yRzM6gJEZf2Hcn3yrLE-MjIcCkNw1Cqq)  
  
#### 安装Git
> Debian系使用apt-get方式安装，Red Hat系使用yum方式安装
``` shell
sudo apt-get install git
yum install git
```

#### 设置用户名和邮箱
> Git是分布式版本控制系统,需要设置用户名和邮箱
``` shell
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```

#### 创建新的版本库
> 创建目录并在目录中初始化版本库
``` shell
mkdir git && cd git
git init
```

#### 提交文件
> 新建一个readme.txt文件并提交到版本库 
``` shell
echo "Git is a version control system.">>readme.txt
git add readme.txt
git commit -m "add readme"
```

#### 查看状态
> 
``` shell
git status
```

#### 查看修改内容
> 比较工作区与暂存区的文件区别
``` shell
git diff readme.txt
```
比较暂存区跟版本库的文件区别
``` shell
git diff --cached readme.txt
```
比较工作区跟暂存区的区别
``` shell
git diff
```
比较工作区与版本库的区别
``` shell
git diff HEAD
```
比较最近两个版本的区别
``` shell
git diff HEAD^ HEAD

#### 查看日志
> 如果记录太多，可添加--pretty=oneline只显示一行
``` shell
git log --pretty=oneline
```

#### 查看操作日志
> 
``` shell
git reflog
```

#### 版本库回退
> 
``` shell
git reset --hard HEAD^
```

#### 撤销工作区修改
> 
``` shell
git checkout -- readme.txt
```

#### 撤销暂存区修改
>
``` shell
git reset HEAD readme.txt
```

#### 删除文件
>
``` shell
git rm readme.txt
```

#### 创建SSH Key
> 在用户主目录里查看是否存在.ssh目录，里面是否有*id_rsa*和*id_rsa.pub*两个文件，如果存在，则跳过这一步。
``` shell
ssh-keygen -t rsa -C "youremail@example.com"
```
登陆GitHub，打开“Account settings”，进入“SSH and GPG keys”页面，点“New SSH key”，填上任意Title，在Key文本框里粘贴*id_rsa.pub*文件的内容
  
#### 添加远程仓库
> 首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的空仓库
``` shell
git remote add origin git@github.com:mayer2014/notes.git
git push -u origin master
```

#### 推送更新到Github
> 
``` shell
git push origin master
```

#### 从Github克隆
> 
``` shell
git clone git@github.com:mayer2014/notes.git "可重命名目录名"
```

#### 创建分支
> 
``` shell
git checkout -b dev
```
或
``` shell
git branch dev
git checkout dev
```

#### 查看分支
> 
``` shell
git branch
```

#### 切换分支
> 
``` shell
git checkout master
```

#### 合并分支
> 合并到当前分支，可以使用--no-ff方式普通合并，强制禁用Fast forward模式，Git就会在merge时生成一个新的commit
``` shell
git merge dev
```
或
``` shell
git merge --no-ff -m "merge with no-ff" dev
```

#### 删除本地分支
> 删除已合并的分支 
``` shell
git branch -d dev
```
删除未合并的分支
``` shell
git branch -d dev
```

#### 删除远程分支
> 
``` shell
git push origin :dev
```
或
``` shell
git push origin --delete dev
```

#### 保存工作区
> 保存工作目录的中间状态——修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中。
``` shell
git stash
```
保存工作区时忽略已暂存的文件
``` shell
git stash --keep-index
```
保存工作区时包含新创建的文件
``` shell
git stash -u
```

#### 查看保存的工作区
> 
``` shell
git stash list
```

#### 恢复工作区
> 恢复最近一次保存的工作区
``` shell
git stash pop
```
恢复指定的工作区
``` shell
git stash pop stash@{id}
```
或
``` shell 
git stash apply stash@{id}
git stash drop stash@{id}
```

