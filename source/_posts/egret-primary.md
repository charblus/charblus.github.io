---
title: Egret引擎开发基础（一）
categories:
  - Egret
  - 分类2
tags:
  - 标签1
  - 标签2
comments: false
abbrlink: 38481
date: 2019-01-07 01:25:06
img:
---



#### 显示图片

```
  var batman:egret.Bitmap = new egret.Bitmap( RES.getRes('hexo-huaheshang_png'));
  batman.x = 0;
  batman.y = 20;
  this.addChild( batman );

```

### 改变图片显示深度（层级）

```
     var batman:egret.Bitmap = new egret.Bitmap( RES.getRes('hexo-huaheshang_png'));
        batman.x = 0;
        batman.y = 20;
        this.addChild( batman );

        var batman1:egret.Bitmap = new egret.Bitmap( RES.getRes('hexo-huaheshang_png'));
        batman1.x = 60;
        batman1.y = 60;
        this.addChild( batman1 );


        var batman2:egret.Bitmap = new egret.Bitmap( RES.getRes('hexo-huaheshang_png'));
        batman2.x = 120;
        batman2.y = 80;
        this.addChild( batman2 );

        this.setChildIndex(batman1, this.getChildIndex( batman2 )); // 获取batman2 深度 给batmain1

```


#### Tween 动画
```
  this.stage.addEventListener(egret.TouchEvent.TOUCH_TAP, () => {
  egret.Tween.get(batman).to({x: batman1.x}, 300, egret.Ease.circIn )
  egret.Tween.get(batman1).to({x: batman.x}, 300, egret.Ease.circIn )

  egret.Tween.get( batman1 ).to( {scaleX: .4, scaleY:.4, alpha: .3}, 300, egret.Ease.circIn).to({scaleX: 1, scaleY: 1, alpha: 1}, 300, egret.Ease.circIn)
  
  }, this);


```

#### 声音

```
  var sound:egret.Sound = RES.getRes('jimp_mp3'); sound.play();

```


### 手册
[文档](http://edn.egret.com/cn/docs/)
[命令行手册](http://edn.egret.com/cn/docs/page/582)
* UI扩展库 旧版GUI 新版EUI
