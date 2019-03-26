---
title: Hexo blog使用指南
categories:
  - 前端
tags:
  - hexo
  - 前端
comments: false
abbrlink: 7251
date: 2018-12-27 02:04:27
img: 
---

What?
Hexo 是一个快速、简洁且高效的博客框架。可以使用markdown 解析成文章，在几秒内，即可利用靓丽的主题生成静态网页。
Why?
笔记需要整理
How?
github 创建 [charblus.github.io](charblus.github.io) 项目
使用markdown 记录开发笔记和文章
日复一日

链接：
[Hexo官方网站](https://hexo.io/)
[Hexo官方主题](https://hexo.io/themes/)

## 快速开始

```bash
hexo n "hexo-post"
hexo g
hexo s
hexo d

```

### 创建一篇文章

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### 本地启动

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### 生成静态html 

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### 部署远程服务

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

### hexo 命令简写

```bash
hexo s == hexo server   用于生成静态文件
hexo g == hexo generate   用于启动服务器，主要用来本地预览
hexo d == hexo deploy    用于将本地文件发布到github等git仓库上
hexo n == hexo new     用于新建一篇名为“my article”的文章 `hexo n “my article”`
```

### 创建菜单
* sourse 添加文件夹 `_name` , 文件中添加index.md文件
* 修改主题的配置文件_config.yml,增加一个标签页菜单


### 参考文章
   [https://hexo.io/zh-cn/docs/index.html](https://hexo.io/zh-cn/docs/index.html)

   [HEXO搭建个人博客](https://blog.csdn.net/flappy8023/article/details/72453350)

   [在Github上面搭建Hexo博客（一）：部署到Github](http://www.cnblogs.com/cherishzy/p/5694658.html)

   [Hexo在Github中搭建博客系统(4)建菜单写文章](https://blog.csdn.net/chwshuang/article/details/52350518)