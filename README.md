
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

### 本地启动

``` bash
$ hexo server
```

### 生成静态html 

``` bash
$ hexo generate
```

### 部署远程服务
> 项目已添加travis Ci 持续集成,部署直接部署`hexo d`就可以了

``` bash
$ hexo deploy
```

### hexo 命令简写

```bash
hexo s == hexo server   用于生成静态文件
hexo g == hexo generate   用于启动服务器，主要用来本地预览
hexo d == hexo deploy    用于将本地文件发布到github等git仓库上,并通过travis Ci 持续集成
hexo n == hexo new     用于新建一篇名为“my article”的文章 `hexo n “my article”`
```

### 创建菜单
* sourse 添加文件夹 `_name` , 文件中添加index.md文件
* 修改主题的配置文件_config.yml,增加一个标签页菜单

