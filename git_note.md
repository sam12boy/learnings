参考了如下资料： [链接](https://git-scm.com/book/zh/v2/)  
## 0. 查看帮助  
第一种：```$ git help```  
第二种：```$ git add -h```   

## 1. 配置
显示配置：```$ git config --list```   
显示配置路径：```$ git config --list --show-origin```   
显示具体某项配置：```$ git config user.name(具体某项属性)```  

修改用户：```$ git config --global user.name "ABC"```   
修改用户：```$ git config --global user.email "ABC@CDE.com"```   
修改代码编辑器（可以改成Vim,Notepad++等等）：```$ git config core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"```  

## 2. 建立git仓库  
通常有两种获取 Git 项目仓库的方式：  
&emsp;&emsp;  1.将尚未进行版本控制的本地目录转换为 Git 仓库；  
&emsp;&emsp;  2.从其它服务器 克隆 一个已存在的 Git 仓库。  

2.1  初始化本地的仓库
```
$ git init
$ git add 文件名1,文件名2
$ git add 文件名3
$ git commit -m "add some modify description"
```

