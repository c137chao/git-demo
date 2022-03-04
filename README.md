![](https://img-blog.csdnimg.cn/img_convert/cf32fcc41799d64541cb6c9b5f9373a2.png)

>Workspace：工作区  
Index / Stage：暂存区  
Repository：仓库区（或本地仓库，版本库）  
Remote： 远程仓库  

工作区是我们本地目录管理的代码文件，版本库就是git所管理的代码文件，可以进行版本回退，看到有哪些未提交的修改等等。  
暂存区是我们add但没有commit的代码文件。

---
## 1.基本操作

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

## 2.远程仓库

在github网页新建一个epoh后

```git
git remote add origin git@github.com:YourUserName/git-demo.git
git branch -M main
git push -u origin main
```

[关于SSH无法链接github.com](https://blog.csdn.net/vosang/article/details/50499300)