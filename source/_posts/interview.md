---
title: 前端面试interview之一面
categories:
  - 前端
  - 分类2
tags:
  - 标签1
  - 标签2
comments: false
abbrlink: 11745
date: 2019-03-26 18:34:27
img:
---

一面：
页面布局类。  
css盒模型  
dom事件类   
HTTP协议。
原型链类。  
面向对象 
通信类
前端安全类。
前端算法类

#### 页面布局类
1. 题目：假设高度已知，请写出三栏布局，其中左栏、右栏宽度各位300px，中间自适应
方案： 第一浮动，第二绝对定位，第三个flexbox弹性布局。第四种：表格布局。第五种：网格布局
code: 
* 在生成代码之前，需要对初始样式清除，html*{padding：0；margin：0}，设置高度。

* section标签包裹，article做包围框。div.left+div.right+div.center可以快速生成。中间部分写一点内容撑开。注意 .layout.float .left 是什么意思。它指的是ID为.layout.float下的子元素.left。中间没有逗号。

#### css盒模型 

根据 W3C 的规范，元素内容占据的空间是由 width 属性设置的，而内容周围的 padding 和 border 值是另外计算的。不幸的是，IE5.X 和 6 在怪异模式中使用自己的非标准模型。这些浏览器的 width 属性不是内容的宽度，而是内容、内边距和边框的宽度的总和。
[盒子模型（标准盒模型、怪异盒模型）和 css3指定盒子模型种类的box-sizing属性](https://www.imooc.com/article/68238)

#### dom事件类   
#### HTTP协议。
#### 原型链类。  
#### 面向对象 
#### 通信类
#### 前端安全类。
#### 前端算法类
