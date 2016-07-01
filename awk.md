# Awk 简要教程
> Awk是一种处理结构数据并输出格式化结果的编程语言，通常被用来进行格式扫描和处理，通过扫描一个或多个文件中的行，查看是否匹配指定的正则表达式，并执行相关的操作。  

#### 语法摘要
> 单引号的作用是包裹起来防止shell截断
``` shell
awk '/Pattern1/{Actions}    
     /Pattern2/{Actions}' file
```

#### 工作方式
> * Awk一次读取文件中的一行
* Pattern和Action是可选的，但是必须提供其中一个
* 如果Action未提供，则默认打印出该行的数据
* Awk包含许多内建的变量，对于每行的记录，Awk默认按照空格进行分割，并将分隔后的值存入对应的$n变量中，其中$0代表整行，$1表示第一个字段，$NF表示最后一个字段

#### 例子文件
> **vim employee.log**
``` shell
1  Tom     Manager    Sales       $5,000    
2  Jac     Developer  Technology  $5,500    
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
5  Ran     DBA        Technology  $6,000
```

#### 例子说明
> * **awk '{print;}' employee.log**
``` shell
1  Tom     Manager    Sales       $5,000    
2  Jac     Developer  Technology  $5,500    
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
5  Ran     DBA        Technology  $6,000
```
* **awk '/San/**  
**/Tim/' employee.log**
``` shell
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
```
* **awk '{print $2,$NF;}' employee.log**
``` shell
Tom $5,000    
Jac $5,500    
San $7,000    
Tim $9,500    
Ran $6,000
```
* **awk '$1 > 2' employee.log**
``` shell    
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
5  Ran     DBA        Technology  $6,000
```
* **awk '$4 ~ /Technology/' employee.log**
``` shell    
3  San     Sysadmin   Technology  $7,000    
2  Jac     Developer  Technology  $5,500    
5  Ran     DBA        Technology  $6,000
```
* **awk 'BEGIN { count=0;}  
$4 ~ /Technology/ { count++; }  
END { print "Number of employees in Technology Dept =",count;}' employee.txt**
