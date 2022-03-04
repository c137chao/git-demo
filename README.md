![](https://img-blog.csdnimg.cn/img_convert/cf32fcc41799d64541cb6c9b5f9373a2.png)

Workspace：工作区  
Index / Stage：暂存区  
Repository：仓库区（或本地仓库）  
Remote： 远程仓库  

---
### 1.基本操作

**创建本地仓库**

```git
git init 
```
**把文件添加到暂存区**
```git
git add README.md 
```
**把文件提交到本地仓库**
```git
git commit -m"commit a README file"
```

查看当前状态（当前分支，是否有文件未提交，修改状态等）
```git
git status
```