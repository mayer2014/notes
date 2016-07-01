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

#### 例子文件
> **vim employee.log**
``` shell
1  Tom     Manager    Sales       $5,000    
2  Jack    Developer  Technology  $5,500    
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
5  Ran     DBA        Technology  $6,000
```

#### 例子说明
> * **awk '{print;}' employee.log**
``` shell
1  Tom     Manager    Sales       $5,000    
2  Jack    Developer  Technology  $5,500    
3  San     Sysadmin   Technology  $7,000    
4  Tim     Manager    Marketing   $9,500    
5  Ran     DBA        Technology  $6,000
```
* **awk '/San/**  
**\> /Tim/' employee.log**

