---
title: node包管理工具--nvm
categories:
  - 前端
  - 工具
tags:
  - node
  - 前端
comments: false
abbrlink: 8241
date: 2018-12-27 02:04:27
img:
---

> mac 用nvm 管理node版本; (直接使用npm安装nrm, 不需要其他配置)
> windows 安装nvw-windows 使用nvm工具； 

#### windows使用nvm-noinstall.zip安装
> nvm-noinstall.zip 这个是绿色免安装版本，但是使用之前需要配置
1. [nvm-windows 下载](https://github.com/coreybutler/nvm-windows/releases) 
 下载最新版本 Assets下 nvm-noinstall.zip文件

2. 把nvm_noinstall.zip解压到比如 `C:/dev/nvm` 中(其它盘也可以)；

3. 右键以管理员的身份运行install.cmd . 直接按回车,在C盘根目录下会生成一个settins,txt.并拷贝到C:/dev/nvm.修改内容:

```
root: C:\dev\nvm
path: C:\dev\nodejs
arch: 64
proxy: none
node_mirror: http://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/

```
> root 配置为当前nvm.exe所在的目录；
> path 配置为node快捷方式所在的目录；
> arch 配置为当前操作系统的位数（32/64）；
> proxy 表示代理，一般不用配置，有的直接设置为none；
> 使用nvm install 8.11.1 下载node v8.11.1 版本，可能网速慢或者需要翻墙导致error下载失败，这里配置使用淘宝node镜像node_mirror和淘宝npm镜像npm_mirror

4. 配置环境变量
   打开‘控制面板主页->高级系统设置->高级->环境变量’后会有‘用户变量’和‘系统变量’两个选项，建议在‘用户变量’里面设置:
   ```
    变量名: NVM_HOME    变量值: C:\dev\nvm
    变量名: NVM_SYMLINK 变量值: C:\dev\nodejs
    变量名: PATH:       变量值: %NVM_HOME%;%NVM_SYMLINK%  (在PATH的最后添加%NVM_HOME%;%NVM_SYMLINK%)
   ```
5. npm 相关配置
   * npm全局安装
    - `npm config set prefix "c:\dev\nvm\npm"`  配置用npm下载包时全局安装的包路径
   * 配置npm环境变量
    - 变量名: NPM_HOME 变量值: c:\dev\nvm\npm (一定要放在NVM_SYMLINK之前;第4步：在PATH的最后添加%NVM_HOME%;%NPM_HOME%;%NVM_SYMLINK%);

6. nrm 安装和使用
   直接下载： `npm install –g nrm` 
   镜像下载： `npm install nrm –g --registry=https://registry.npm.taobao.org`

   ```bash
   nrm ls         // 列出所有镜像(下载源)
   nrm use taobao     // 选择使用淘宝镜像
   ```

7. nvm 使用
   * `nvm list` 列出所有已经安装的nodejs版本
   * `nvm install lastest ` 下载最新版本的nodejs
   * `nvm install 8.11.1 ` 下载版本为v8.11.1的nodejs
   * `nvm use 8.11.1`   使用指定版本 为v8.11.1的nodejs (注意：如果操作系统为32位的，使用nvm use [版本号] 命令时，后面要加上32。也就是nvm use 8.11.1 32 ）
   * `nvm ls available` 查看可用的（可下载的）全部node版本

   > `node -v` 查看nodejs的版本号
