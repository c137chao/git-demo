![](https://img-blog.csdnimg.cn/img_convert/cf32fcc41799d64541cb6c9b5f9373a2.png)

>Workspace：工作区  
Index / Stage：暂存区  
Repository：仓库区（或本地仓库，版本库）  
Remote： 远程仓库  

工作区是我们本地目录管理的代码文件，版本库就是git所管理的代码文件，可以进行版本回退，看到有哪些未提交的修改等等。  
暂存区是我们add但没有commit的代码文件。
<br/>
<h1 align="right">git学习记录</h1>

---
git学习资料：[官方教程](https://git-scm.com/book/zh/v2)，[廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600/896067074338496) ，[CSDN看到的另一份参考资料](https://blog.csdn.net/u011535541/article/details/83379151)

---
设置自己的username（仓库地址里的那个username）和 email
```git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
<h2><center>1.基本操作 </center></h2>

**创建本地仓库(版本库)**

```git
git init 
```
**把文件添加到暂存区**
```git
git add README.md 
```
**将暂存区提交到本地仓库(版本库)**
```git
git commit -m"commit a README file"
```
或者 `git commit -am"commit a README file"`一步搞定

<br/> 

查看当前状态（当前分支，是否有需要提交的修改）
```git
git status
```
查看具体的修改信息
```git
git diff
```
记得经常提交自己的修改
查看commit的版本记录
```git
git log
```
想要**版本回退**的话
```git
git reset --hard HEAD^  # 回退到上个版本
git reset --hard HEAD^^ # 回退到上上个版本
git reset --hard HEAD~100 #回退到前100个版本 
git reset --hard 版本号 # 回退到某个特定版本
```
版本号可以通过 `git log` 或 `git reflog`获取  

<br/>
  
**放弃当前工作对某个文件的修改**
```git
git checkout --filename
```

<h2><center>2.远程仓库 </center></h2

在github网页新建一个 repo 后

```git
git remote add origin git@github.com:YourUserName/git-demo.git
git branch -M main
git push -u origin main
```

[关于SSH无法链接github.com](https://blog.csdn.net/vosang/article/details/50499300)

看到 **origin** 可以理解为他就是我们 github 上的远程仓库的默认名字  

`git remote add <远程仓库名> <远程仓库地址>` 把本地库关联到远程库  

`git push -u origin main` 把当前分支推送到远程库的main分支
`-u`表示会把本地 main 分支与远程库 main 分支  关联起来  

以后再提交只需要 `git push origin main`

<br/>
查看关联的远程分支

 ```git
 git remote -v

origin  git@github.com:c137chao/git-demo.git (fetch)
origin  git@github.com:c137chao/git-demo.git (push)
 ```

 与远程分支解除关联  
 ```git
 git remote rm origin
 ```

 远程仓库克隆到本地（例如）
 ```
git clone git@github.com:c137chao/git-demo.git
 ```

<h2><center>3.分支管理</center></h2>

**创建并切换分支**
```git
git checkout -b <Branch Name>
```
`-b`表示创建并切换，相当于以下两条命令
```git
$ git branch <Branch Name>
$ git checkout <Branch Name>
```
通过`git branch`**查看当前分支**
```
* CreateBranch
  main
```
提交修改并push到远程库的新分支
```git
git commit -am"Create a New Branch"
git push -u origin CreateBranch
```

**Note**
如果是clone的别人的repo，可以添加自己的远程库
```git
git remote add summer git@github.com:c137chao/git-demo.git
git push summer <Branch Name>
```

切换回 main 分支 `git checkout main`


<br/>

**合并到当前分支**  
```git
git merge <Branch Name>
```

*合并以后就可以**删除刚才创建的分支** 
```git
git branch -d <Branch Name>
```