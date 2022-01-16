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

add 其实就是把文件摆在待推送的状态  
commit就是执行这个推送

**尽量不要使用 $git commit 后面不加参数**  
因为不加参数之后，commit以后会跳到编辑器（windows下git Bash默认是vim编辑器）
点 "i" ，并把光标移动到第一行进行编辑  编辑结束点ESC   然后输入":x"或":wq" 保存，退出并执行commit 

**查看修改提交状态**  
```
$ git status————查看哪些文件add了，哪些修改了还没add.....
$ git diff————查看add的文件与当前文件之间变化
$ git diff --cached（或者 $ git diff --staged）————查看add的文件与上次commit的文件之间变化
```

**撤销提交**  
```$ git commit --amend```  
其实原理是再提交一遍，但是会覆盖上次的提交记录  
**去除多余add的文件**  
```$ git restore --staged```  

## 3. 分支
3.1 分支操作  
**添加分支**  
```$ git branch 新分支名```  
**切换（移动）分支**  
```$ git checkout 分支名```  
**查看历史分支（版本）**  
```$ git log --oneline --decorate //用了oneline参数比较简略，省略了提交人等信息```  
**创建新分支,并立即切换**  
```git checkout -b <newbranchname>```   
**删除分支**  
```git checkout -d <branchname>```  
**合并分支**  
具体操作在3.3节中，简单的合并语句如下  
```
git checkout master
git merge other
```  
实现的效果是把other和master合并，然后master分支移动到新的合并后节点（提交对象）去

3.2 分支介绍  

![alt text](https://git-scm.com/book/en/v2/images/commit-and-tree.png)  
上图中有三个部分：灰色为提交对象（树对象指针和提交信息），蓝绿色为树对象（目录结构，blob索引），黄色部分为blob对象（文件快照）  


![alt text](https://git-scm.com/book/en/v2/images/commits-and-parents.png)  
上图为不断提交的提交对象和树结构

![alt text](https://git-scm.com/book/en/v2/images/branch-and-history.png)  
上图为分支和提交历史，head指向的是当前分支


3.3 合并分支  
这里先讨论两种情况，一种是合并同一条链上的分支，第二种是合并非同一链上的分支（前提不冲突） 
##### 第一种、合并同一条链上分支  
![alt text](https://git-scm.com/book/en/v2/images/basic-branching-4.png)  
上图 合并前状态  

![alt text](https://git-scm.com/book/en/v2/images/basic-branching-5.png)  
上图 合并后状态  

##### 第二种、合并非同一链上的分支  
![alt text](https://git-scm.com/book/en/v2/images/basic-branching-6.png)  
上图 合并前状态  

![alt text](https://git-scm.com/book/en/v2/images/basic-merging-1.png)  
上图 合并中所用的快照  

![alt text](https://git-scm.com/book/en/v2/images/basic-merging-2.png)  
上图 合并的结果，新建了一个快照    
