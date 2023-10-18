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



## 回滚

用`HEAD`表示当前版本，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`

```
git reset --hard HEAD^
git reset --hard 1094a
```

`HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`

穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本

要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本



## 修改

`git checkout -- file`可以丢弃工作区的修改：

```
git checkout -- readme.txt
```

命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。



用命令`git reset HEAD `可以把暂存区的修改撤销掉（unstage），重新放回工作区

```
git reset HEAD readme.txt
```

## 删除

一是确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`

先手动删除文件，然后使用git add 和git rm效果是一样的

另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：

```
$ git checkout -- test.txt
```

## 远程remote

```
git remote add origin  https://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@github.com/end1e55/git-learn.git

执行完上述命令后origin =  https://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@github.com/end1e55/git-learn.git
```

```
git remote -v 可以查看 有哪些 存好的仓库地址

git remote rm origin 可以删除
```

```
本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令

从现在起，只要本地作了提交，就可以通过命令：
git push origin master
```



## 分支管理

`HEAD`严格来说不是指向提交，而是指向`master`，`master`才是指向提交的，所以，`HEAD`指向的就是当前分支


create a new branch dev
create a new branch is quick & simple
