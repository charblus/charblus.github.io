---
title: 经查-- git使用报错及解决办法
categories:
  - git
  - 工具
tags:
  - git
  - 工具
comments: false
abbrlink: 52025
date: 2018-12-31 16:14:34
img:
---

### git push 错误 ```error: failed to push some refs to 'git@github.com:charblus/ ...' ```

> 本地和远程的文件应该合并后才能上传本地的新文件
解决办法1： 先拉(pull)后推(push)  
解决办法2： 导致这种报错2是因为没有git add 就去提交空，一般因为这个出现这个问题，此报错上还有一行: `error: src refspec master does not match any.`

### git pull 错误 ``` fatal: refusing to merge unrelated histories```
> 更新代码失败
`git pull origin master --allow-unrelated-histories`
后面加上 --allow-unrelated-histories ， 把两段不相干的 分支进行强行合并

`git add .` && `git commit -m "***"` && `git push origin master`
[cankao](http://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories)

### git branch 错误 ```fatal: Not a valid object name: 'master'.```

git项目下没有任何文件可以commit，或没有新项目没有一次commit ,是不能创建分支的；只有先commit之后才会真正建立master分支，此时才可以建立其它分支。

由于刚创建的git仓库默认的master分支要在第一次有效的commit之后（可以先不push）才会真正建立，否则就像你声明了个对象但没初始化一样。

