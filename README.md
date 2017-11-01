# just-border
## 1 边框基本语法

`border：border-width  border-style  border-color`
- 三个属性没有先后顺序，其中，border-style为<strong>必需<strong>。
- border-width默认值为<strong>“ medium”</strong>（大约3～4px）。

好哒～试试利用border制作三角形

![lALOhxAXYczhzJA_144_225.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/df3f678f5af2ffcaf35b5f693331694c.png)

```
    width: 0;
    height: 0;
    border-left: 20px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 40px solid blue;
```

<strong>原来：如果宽度和高度为0，border也可以组成一个框。<strong>
分割原理如下图：
![screenshot.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/1e9e446bb05b9ddb369a67c7f747ac7a.png)
## 2 边框颜色属性

`border-color：[<color> |  transparent ] {1,4} | inherit`
border-color通常最多接受四值语法。
如果设置了大于四个的颜色会怎样呢？
试一把～

![lALOhqb7sVHNAuY_742_81.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/e3f15047c3f479df72d80ff9e67175b1.png)
```
border: 10px solid transparent;
-moz-border-top-colors: red blue red blue red blue red blue;
```
<strong>这里border-color能实现一个渐变效果，但目前兼容性较差，且不是标准写法（以下实例来自火狐3.0以上）。</strong>
<strong>将标准写法拆分为四个边框，使用多色才会有效。</strong>
<strong> 如果设置n个颜色，且边框宽度为n的话，每种颜色显示1px，如果宽度大于颜色数量，前面每个颜色显示1px，剩下所有宽度显示最后一个颜色。</strong>

## 3 图片边框属性
```
border-image ： none | <image> [ <number> | <percentage>]{1,4} [ / <border-width>{1,4} ]? [ stretch | repeat | round ]{0,2}
```
- none:是border-image的默认值，如果取值为none时，表示边框无背景图片；
- image：设置border-image的背景图片；
- number：number是一个数值，用来设置边框的宽度，其单位是px
- percntage：percntage也是用来设置边框的宽度，跟number不同之处是，其使用的是百分比值来设置边框宽度；
- stretch,repeat,round:他们是用来设置边框背景图片的铺放方式，其中stretch是拉伸，repeat是重复，round是平铺，stretch为默认值。

图片边框是一个相对复杂的属性，因为它有一个剪切特性，然后结合图片排列方式能产生神奇效果。

原始图片如下：
![lALOhqj0sszMzMs_203_204.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/2e526c7d4d7f7a17d11a41ca94fc6eee.png)

然而花样可以是这样：
![下载.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/ce61593682c52bdf55704a2da8f1ff28.png)

还可以是这样：
![images.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/aa804a88d9a379eae1bf0162c43622dd.png)


<strong>原理就是通过设置其四个方位的宽度将原始图片slice成九宫格，然后设置图片（原始图片中黄色部分，也就是效果展示区域）的铺放方式。</strong>
<strong>注意repeat和round差别：repeat是边框从中间向两边平铺，round会对切片压缩或拉伸以适应宽度。</strong>

## 4 圆角边框属性
`border-radius ： none | <length>{1,4} [/ <length>{1,4} ]`
### 4.1 各种圆角
![101030377763963.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/059c76a8d5f4026256a0d847041c38ad.png)
<strong>注意内半径与外半径区别。当boder-radius半径小于或等于boder宽度时 内部圆角不明显。</strong>
<strong>boder-radius 在img 和 table上的应用有差别。当table border-collapse是collapse时 表格不能显示圆角 只有为separate 时 ，表格圆角才能显示。</strong>

### 4.2 圆角属性画半圆
 ![screenshot.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/fc75e36b906e91aa5e314c1ba124676e.png)
```
.left{
    width: 50px;
    height: 100px;
    border-radius: 50px 0 0 50px;
}
```
<strong>半圆：把宽度设为高度的一半（宽度设为高度的一半），并且也只设置左上角和左下角的半径或右上上和右下（左上和右上 或 右下和左下）。</strong>

### 4.3 圆角属性画四分之一圆
![screenshot.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/7a68856fac72b2a455298a310e445039.png)
```
.top{
    width: 100px;
    height: 100px;
    border-radius: 100px 0 0 0;
}
```
<strong>四分之一圆：把宽高相等，只设置一个角的圆角半径，且值与宽高相等。</strong>

## 5 盒子阴影属性
`box-shadow：none | [inset? && [ <offset-x> <offset-y> <blur-radius>? <spread-radius>? <color>? ] ]#`
- 需要注意阴影层级关系：边框>内阴影>背景图片>背景色>外阴影 。
- 内阴影使用在img元素上无效果 。
- 有多层阴影效果。
![screenshot.png](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/78160aaf3476b9a319cc0edfb9e0248a.png)

```
box-shadow:0px 0px 0px 5px #0032ff,
           0px 0px 0px 10px #fe1d03,
           0px 0px 0px 15px #fffb00,
           0px 0px 0px 20px #0e7d00;
```
<strong>需注意阴影顺序！</strong>


## 6 总结
有一些细节使用之前确实母鸡啊～
