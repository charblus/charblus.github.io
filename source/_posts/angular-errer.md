---
title: ngular6开发不完全笔记（三）-- 报错指南
categories:
  - angular
  - 分类2
tags:
  - 前端
  - 标签2
comments: false
abbrlink: 4817
date: 2019-01-22 22:01:25
img:
---

#### router
> Uncaught Error: Template parse errors:
> 'router-outlet' is not a known element:
> 1. If 'router-outlet' is an Angular component, then verify that it is part of this module.
> 2. If 'router-outlet' is a Web Component then add 'CUSTOM_ELEMENTS_SCHEMA' to the '@NgModule.schemas' of this component to suppress this message.

* 解决方法
1. 每个模块中都添加 `import { RouterModule } from '@angular/router';`   然后 import即可 
2. 【推荐】建立shared模块 在分享模块中导入 `RouterModule` 然后导出，其他有使用 `<router-outlet></router-outlet>` 的模块都导入 shared模块
> 主要是导入RouterModule指令， 根据自己的写法调整， 二者选一即可