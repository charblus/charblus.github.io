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