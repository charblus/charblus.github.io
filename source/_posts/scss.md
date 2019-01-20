---
title: scss
categories:
  - 前端
  - 分类2
tags:
  - 前端
  - css
comments: false
abbrlink: 20366
date: 2019-01-10 03:59:01
img:
---

### sass嵌套
1. 选择器嵌套
> 这里的 & 代表 nav a ,理解起来有点 像js中this 的意思

```html
<header>
    <nav>
        <a href="#">home</a>
        <a href="#">page</a>
    </nav>
</header>

```

```css

    nav a {
        color:red;
    }
    header nav a {
        color:green;
    }
```

```scss
nav {
  a {
    color: red;
    
    header & {
      color:green;
    }
  }  
}
```

2. 属性嵌套(有相同的属性前缀)
> 如 font, background等，也有可能是 -webkit-

```css
.box {
     font-size: 12px;
     font-weight: bold;
}
```

```scss
.box {
  font: {
   size: 12px;
   weight: bold;
  }  
}
```

3. 伪类嵌套
> 同上选择器嵌套一样  使用 & 关键字 

```scss
.clearfix{
&:before,
&:after {
    content:"";
    display: table;
  }
&:after {
    clear:both;
    overflow: hidden;
  }
}
```

```css
clearfix:before, .clearfix:after {
  content: "";
  display: table;
}
.clearfix:after {
  clear: both;
  overflow: hidden;
}
```

### 占位符：
语法：%placeholder，
用法：占位符不被 @extend 调用不产生任何代码

```scss
%bg {
  background-color: #FF0;
}
%w {
  width: 100px;
}
.box {
  @extend %w;
  height: 100px;
  @extend %bg;
}
```

### sass 语法
允许使用变量 以 $ 开头

```
$test: #ff9500
div{
       color: $test;
}
```

也可以字符串拼接

```
$side : left;
  
.rounded { 
        border-#{$side}-radius: 5px;
 }
```

也可以加减乘除 简单计算




### sass分享：
内容：全局、默认、局部变量
使用：默认变量 在局部中无效，覆盖 默认变量 不分上下顺序

```html
<div class="box1">
  <div class="box2">box2</div>
</div>
```

```scss
$backgroundColor: #FF0;                  // 全局变量
$backgroundColor: #000 !default;      // 默认变量
$color: #F0F;

.box1 {
  $color: #CCC;                                   // 局部变量
  width: 100px;
  height: 100px;
  background-color: $backgroundColor; // #FF0
  .box2 {
    color: $color;                                      // #CCC
  }
}
```


### 控制指令 (Control Directives)
混合指令

mixin  技术文档翻译  混合类型
mixing  混合 （mix 的现在分词）

mixin    sass官方文档称  混合指令
@mixin  为定义混合指令
@include   为引用楼上定义的混合指令

```html
<div class= "parent">
111
</div>
<div class= "child">
222
</div>
<div class= "test">
333
</div>

```

```scss
.parent {
  color: red;
}
.child {
  @extend .parent;
  font-size: (21px * 3);
}
@minxin auto {
  margin: 0 auto;
}
.test {
  width: 200px;
  @include auto;
}

```

####  sass 的 @if  控制指令

```html
<div class="demo"></div>

```

单独使用@if：
> 当@if 的表达式不是false或者null时， 条件成立， 输出{} 内的代码

```scss
.demo{
  $fx: bottom;
  @if ($fx == top) {
    border-color: transparent transparent pink transparent;
    border-style: dashed dashed solid dashed;
  }
  @else if($fx == right){
    border-color: transparent transparent transparent pink;
    border-style: dashed dashed dashed solid;
  }
  @else if($fx == bottom){
    border-color: pink transparent transparent transparent;
    border-style: solid dashed dashed dashed;
  }
  @else if($fx == left){
    border-color: transparent pink transparent transparent;
    border-style: dashed solid dashed dashed;
  }

  width: 0px;
  height: 0px;
  overflow: hidden;
  border-width: 60px;
}

```

混合指令 + @if 指令

```scss
// 画三角形@mixin声明
@mixin sj($fx:top,$size:100px,$color:red){

  @if ($fx == top) {
    border-color: transparent transparent $color transparent;
    border-style: dashed dashed solid dashed;
  }
  @else if($fx == right){
    border-color: transparent transparent transparent $color;
    border-style: dashed dashed dashed solid;
  }
  @else if($fx == bottom){
    border-color: $color transparent transparent transparent;
    border-style: solid dashed dashed dashed;
  }
  @else if($fx == left){
    border-color: transparent $color transparent transparent;
    border-style: dashed solid dashed dashed;
  }

  width: 0px;
  height: 0px;
  overflow: hidden;
  border-width: $size;

}

//mixin的调用
.demo{
  @include sj(left, 66px, pink);
}
```



less 与sass有个很明显的区别
变量
 咱们sass 变量用   $  开头     
less  是以 @ 开头的


###  sass语法  @for 控制指令
> @for 指令可以在限制的范围内重复输出格式，每次按要求（变量的值）对输出结果做出变动；

这个指令包含两种格式：
@for $var from <start> through <end>，
  或者
  @for $var from <start> to <end>


```html
<ul>
  <li class="item-1">至尊魔法师</li>
  <li class="item-2">王</li>
  <li class="item-3">奇异博士</li>
  <li class="item-4">莫度男爵</li>
  <li class="item-5">哈姆雷特</li>
  <li class="item-6">蜘蛛侠</li>
  <li class="item-7">非人哉</li>
</ul>

```

from ... through

// 当使用 through 时，条件范围包含 <start> 与 <end> 的值

// 个人分析： 可以将一个页面，不同div中嵌套的元素设置样式，只要命名符合一定的规律

```scss
@for $i from 1 through 7 {
  .item-#{$i} { 
    width: 6em * $i;
    background: pink;
    margin: 6px 0;
  }
}
```

from ... to
> 使用 to 时条件范围只包含 <start> 的值不包含 <end> 的值。另外，$var 可以是任何变量，比如 $i；<start> 和 <end> 必须是整数值。
```scss
@for $i from 1 to 7 {
  .item-#{$i} { 
    width: 6em * $i;
    background: pink;
    margin: 6px 0;
  }
}

```



```
@each $usr in nezha, aolie, xiaoyu, xiaotian {
    .#{$usr}-avatar {
        background-image: url('/img/#{$usr}.png');
     }
}
```



@each 后面的 $usr 变量用于保存每次遍历到的元素，然后使用差值语法（#{var}）来拼接正确的图片路径




//@each 指令同样可以用于循环输出，和 @for 的差别在于，@each 通过遍历 list 或者 map 实现循环输出
// 如果遍历的对象是一个 map，那么我们就可以使用两个变量来存储元素的 key 和 value

```
$frz: ( usr1:xiaotian, usr2:sanyan, usr3:shancai, usr4:longnv );

@each $key, $usr in $frz {
    .#{$usr}-avatar {
        background-image: url('/img/#{$usr}.png');
    }
}

```


运算的坑
> 加号居然可以不需要空格隔开,但必须单位统一

```scss

$sidebar-width: 220px;
$content-width: 720px;
$gap-width: 20px;
$other-width: 2em;

.container {
    // width: $sidebar-width+$content-width + $gap-width;
    width: $sidebar-width + $other-width;
    margin: 0 auto;
}

```


>  还可以做字符连接

1. 如果有引号的字符串被添加了一个没有引号的字符串 （也就是，带引号的字符串在 + 符号左侧）， 结果会是一个有引号的字符串。 
2. 如果一个没有引号的字符串被添加了一个有引号的字符串 （没有引号的字符串在 + 符号左侧）， 结果将是一个没有引号的字符串。


```scss
p:before {
  content: "bing" + jian;
  font-family: sans- + "serif";
}
```

编译后


```css
p:before {
  content: "bingjian";
  font-family: sans-serif;
}
```


> 减法 - 需要注意空格了，否则就完蛋喽

```scss
$full-width: 960px;
$sidebar-width: 200px;

.content {
  width: $full-width - $sidebar-width;
}
```
> 乘法
能够支持多种单位（比如 em ,px , %）；
如果进行乘法运算时，两个值单位相同时，只需要为一个数值提供单位即可(多个乘数中只需要一个乘数提供单位，否则报错)。

```scss
.box {
  width: 10px * 2;
}
```
否则

```
.box {
  width: 10px * 6px;
}
```
> error: 60px*px isn't a valid CSS value.


> 除法

众所周知“/”符号在 CSS 中已做为一种符号使用。其在 CSS 中通常起到分隔数字的用途，
因此在 Sass 中做除法运算时，直接使用“/”符号做为除号时，将不会生效，
编译时既得不到我们需要的效果，也不会报错。
需要给运算的外面添加一个小括号()才能执行除法运算

```scss
.box {
  width: (100px / 2);
}
```

总结: ”/  ”符号被当作除法运算符时有以下几种情况：
   　　 如果数值或它的任意部分是存储在一个变量中或是函数的返回值。
    　　如果数值被圆括号包围。
    　　如果数值是另一个数学表达式的一部分。


```scss
p {
  font: 10px/8px;        // 纯 CSS，不是除法运算
  $width: 1000px;
  width: $width/2;          // 使用了变量，是除法运算
  width: round(1.5)/2;        // 使用了函数，是除法运算
  height: (500px/2);          // 使用了圆括号，是除法运算
  margin-left: 5px + 8px/2px;  // 使用了加（+）号，是除法运算
}

```


还有一种情况
> Sass 的除法运算还有一个情况。先回忆一下，在乘法运算时，如果两个值带有相同单位时，做乘法运算时，出来的结果并不是我们需要的结果。但在除法运算时，如果两个值带有相同的单位值时，除法运算之后会得到一个不带单位的数值。　

```scss
.box {
  width: (1000px / 100px);ß
}
```

> 颜色运算 - 分段运算

　　所有算数运算都支持颜色值，并且是分段运算的。也就是说，红、绿和蓝各颜色分段单独进行运算。如：

```scss
p {
  background-color: #012423 + #120923;
  color: #324334 * 2
}

```


















### 有顺工作

将所有的Mixins、Placeholder、Functions和变量放置在一起。将他们放置一起，可以确认他们可以很快的编写以及将来重复使用。

1. 整站的元素应该放在一个base文件夹中。base文件夹应该包括全局的变量，如字体和颜色等
2. 对于特定模块的Mixins、Functions 和变量，为了保证模块能正常运行，需要将这些集中放置在module文件中


### 限制嵌套
**使用嵌套的黄金规则：**

1. 嵌套永远不要超过三个层级
2. 确保输出的CSS简洁、可重用
3. 使用嵌套是很有意义的，而不是默认选项

> 过度的嵌套会导致很多问题的发生,代码变得复杂，而且太过于依赖HTML结构。这样将导致后面的样式需要使用!important来覆盖




## scss 基本用法

1. 变量（局部/全局）声明：$+变量名：变量值；默认变量在变量名后加default，!global变成全局变量。
2. 混合宏（可重用的代码块）：声明混合宏@mixin border-radius { }； 调用混合宏 @include。 border-radius; 声明的时候还可以带默认参数，调用可以传参。
3. 继承： @extend .btn; 继承btn class。任何选择器都能继承，可以连续继承。
4. 占位符%：占位符声明的代码如果不被@extend调用，就不会被编译产生css代码。
5. 插值：#{$参数名}，插入传入或定义的参数。
6. 注释：/* */ :会在编译出来的css文件中显示；//内容：不会显示。/!/：重要注释，任何style的css文件中都会有，一般放置css文件版权说明等信息。
7. 加减法：同单位的数值之间可以做加减法。
8. 乘除法：只能乘数值；如果除式中没有变量或者不是在一个数学表达式中（有加法减法等），就要将除式运算用小括号括起来，否则“/”不会被当做除号运算。
9. 颜色运算：算术运算都支持颜色值，并且是分段计算的，01+05=06
10. 字符串连接：+，$content: "Hello" + "" + "Sass!";cursor: e + -resize；有引号的字符串和没有引号的字符串相加，以左边字符有无引号为准。
11. 父类选择器：&，表示引用父元素，
12. if语法：@if,@else,
13. 循环语法：@for,@while,@each,
14. 函数：@function double ($number){ @return $number*2; }
15. import：导入其他的scss

