---
title: windows 常用快捷键和dos命令 
categories:
  - windows
  - 工具
tags:
  - 命令行
  - 工具
comments: false
abbrlink: 58024
date: 2018-12-31 05:27:26
img:
---

### 快捷键
win + R 打开dos命令行窗口
win + E 打开资源管理窗口 （计算机）

shift + 鼠标右击  + select 在此处打开命令窗口   可在资源管理目录下打开dos命令

#### windows下chrome 快捷键
ctrl + E   地址栏foucs搜索(默认搜索引擎) 

## 常用dos命令
> win键 + R  点击确定，打开命令行窗口 或 运行的设置窗口，在输入栏里输入cmd，然后点击确定

> 注： mac 和linux 目录都是 c:/dev/nvm  而windows 是 c:\dev\nvm

### del 删除

`del /?`   // 查看删除帮助
`del c:\settings.txt`     // 删除指定文件
`del /F /S /Q c:\dev `      // 删除文件夹

```
  /P            删除每一个文件之前提示确认。
  /F            强制删除只读文件。
  /S            删除所有子目录中的指定的文件。
  /Q            安静模式。删除全局通配符时，不要求确认
  /A            根据属性选择要删除的文件
```
