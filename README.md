# git的简单使用
刚接触git，记录一些git的学习

参考的B站技术蛋老师视频和廖雪峰的git教程以及菜鸟教程

(刚学习，有理解错误请见谅或者指出)



## git 是分布式版本控制系统

- 工作区(其实就是目前在的这个文件夹)
- 暂存区 (stage 或 index。一般存放在 **.git** 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）)
- 本地仓库(工作区有一个隐藏目录 **.git**，这个不算工作区，而是 Git 的版本库)

![image-20231017200546847](C:\Users\admin\Desktop\test\git-learn\README.assets\image-20231017200546847.png)



Q: 暂存区的意义？

A:工作区的多个文件可以 add 到暂存区，然后暂存区多个文件进行commit就可以完成一次提交。

可以一次提交多个文件，写一个commit的description。在git log中对应一条修改



## 创建仓库

初始化一个Git仓库，使用`git init`命令

添加文件到Git仓库，分两步：

1. 使用命令`git add `，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m `，完成

`git status`可以查看仓库状态

`git diff filename` 可以查看指定文件修改的内容

`git clone` 可以将仓库克隆到本地

如果我们需要克隆到指定的目录，可以使用以下命令格式：

```
git clone <repo> <directory>
```

`git log`可以查看修改的