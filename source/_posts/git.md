---
title: git
categories:
  - 工具
  - 前端
tags:
  - git
  - 前端
comments: false
abbrlink: 43167
date: 2018-12-25 09:23:27
img:
---

Git是分布式的代码管理工具，远程的代码管理是基于SSH的，所以要使用远程的Git则需要SSH的配置。

git 命令
[TOC]

### 设置git

* 基本配置
```
$ git config --global user.name "charblus"
$ git config --global user.email "charblus7582@gmail.com"

```

* 生成ssh 密钥
1. 查看是否已经有了ssh密钥：`cd ~/.ssh` ; 如果没有密钥则不会有此文件夹，有则备份删除
2. 生成密钥  （email@email.com是github的账号，即上面的email）
```
$ ssh-keygen -t rsa -C “email@email.com”
```
> 按3个回车，密码为空； 如果不执行第一步或没有删除：第一个回车后会出现coverage 提示你是否覆盖文件 yes/no；最后得到了两个文件：id_rsa和id_rsa.pub

### git remote

```
 git remote 不带参数，列出已经存在的远程分支
 git remote -v | --verbose 列出详细信息，在每一个名字后面列出其远程url
 git remote add origin ssh://***.git   添加远程仓库
 git remote show origin  显示远程信息
```

### git-flow 
> git-flow 是一个 git 扩展集，按 Vincent Driessen 的分支模型提供高层次的库操作
[git-flow 备忘清单](http://danielkummer.github.io/git-flow-cheatsheet/index.zh_CN.html)

### git merge 与 git rebase
* git merge 和 git rebase 都是将远程分支与本地分支合并的一种方法，git merge 会生成一个新的节点，例如A和B都位于同一个HEAD，A提交了2个commit C1和C2，B 提交了2个commit C3和C4，git merge的结果是在C3和C4之后合并生成C5，这样提交历史比较清晰，但多了一个C5
* 假设A已经将C1和C2 push到了远程分支，那么B 使用git rebase则会将C3和C4缓存到.git/rebase中，恢复到之前的状态，更新C1和C2，然后再将C3和C4作为补丁应用到C2的状态上。结果如下：
原始状态 ` ->C1->C2->C3'->C4' `，C3'和C4'为git 根据C3和C4生成的补丁，log是一条直线，而且没有多余的C5，但是平行信息丢失。
[git pull和git pull --rebase之间的区别](https://stackoverflow.com/questions/18930527/difference-between-git-pull-and-git-pull-rebase)


### 参考
[廖雪峰git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)