---
title: "CSS学习"
date: 2022-02-15T09:28:06+08:00
draft: false
---

### 选择器

| element           | p       | 选择所有 \<p\> 元素。                    |
| ----------------- | ------- | ---------------------------------------- |
| element.class     | p.intro | 选择 class="intro" 的所有 \<p\> 元素。   |
| element,element   | div, p  | 选择所有 \<div\> 元素和所有 \<p\> 元素。 |
| element element   | div p   | 选择 \<div\> 元素内的所有 \<p\> 元素。   |
| element>element   | div > p | 选择父元素是 \<div\> 的所有 \<p\> 元素。    |
| element+element   | div + p | 选择紧跟 \<div\> 元素的首个 \<p\> 元素。   |
| element1~element2 | p ~ ul  | 选择前面有 \<p\> 元素的每个 \<ul\> 元素。  |

### 选择器的权重

选择器权重（从上往下优先级变低）：

* 内联样式

* id选择器

* 类和伪类选择器

* 元素选择器
* 通配选择器
* 继承优先级（没有优先级）

比较优先级时，需要将所有选择器的优先级相加计算，最后优先级越高的优先显示（分组选择器是单独计算的）

```css
div#box     (相加计算)
div,p,span	(单独计算)
```

如果优先级计算后相同，则根据代码最后设置的样式显示。

可以在样式后后面添加`!important`，可以获得最高优先级（慎用）

a标签样式顺序：https://www.cnblogs.com/Yirannnnnn/p/4540061.html

### 像素和百分比

#### 像素

屏幕实际是由一个一个的小像素点组成，不同的屏幕像素大小不同，像素越小的屏幕像素点密集，图像效果显示越清晰，所以同样写200px在不同的屏幕显示的效果不一样。

#### 百分比

相对于父元素属性的百分比，设置百分比可以使子元素跟随父元素改变。

#### em

相对元素字体大小计算的单位，1em = 1 font-size。会跟随字体的大小改变而改变。

#### rem

相对根元素（html字体大小）字体大小计算。

### RGB值

RGB通过三种颜色的不同浓度来调配出不同的颜色

R red, G green,B blue

每一种颜色的范围在0 - 255 (0% - 100%) 之间，语法: RGB(红色，绿色,蓝色)

#### RGBA

就是在rgb的基础上增加了一个a表示不透明度，需要四个值，前三个和rgb一样，第四个表示不透明度（最大值1），1表示完全不透明0表示完全 透明5 半透明。

#### 十六进制的RGB值

\#红色绿色蓝色

两位重复可以缩写

#### HSL值

H	色相（0-360）

S	饱和度，颜色的浓度（0-100%）

L	亮度，颜色的亮度（0-100%）

HSLA

## 布局

### 文档流(normal flow)

网页是一个多层的结构，一层摞着一层通过CSS可以分别为每一层来设置样式，作为用户来讲只能看到最顶上一层，这些层中，最底下的一层称为文档流，文档流是网页的基础，我们所创建的元素默认都是在文档流中进行排列，对于我们来元素主要有两个状态：

* 在文档流中
* 不在文档流中(脱离文档流)

元素在文档流中有什么特点:

* 块元素
  * 块元素会在页面中独占一行(自上向下垂直排列) 
  * 默认宽度是父元素的全部(会把父元素撑满)
  * 默认高度是被内容撑开(子元素)
* 行内元素
  * 行内元素不会独占页面的一行，只占自身的大小
  * 行内元素在页面中左向右水平排列，如果行之中不能则元素 会换到第二行继续自左向右排列(书写习惯一样)
  * 行内元素的默认宽度和高度都是被内容撑开

### 盒子模型(box model)

CSS页面将所有的元素设置为了一个**矩形**的盒子，对页面的布局就变成了将不同的盒子摆放到不同的位置。每一个盒子都有一下几个部分组成：

* 内容区(content)
* 内边距(padding)
* 边框(border)
* 外边距(margin)

![](https://www.w3school.com.cn/i/css/boxmodel.gif)

#### 内容区(content)

内容区大小由 width 和 height 两个属性来设置。

#### 边框(border)

**盒子的边缘**，边框里面是盒子内部，外面是盒子外部，边框的大小会影响到盒子的大小。边框至少需要设置三个样式：

- 边框的宽度 border-width

默认3px。简写值可有四个：

四个值：上、下、左、右

三个值：上、左右、下

两个：上下、左右

一个值：上下左右

还可以写成border-xxx-width，其中xxx可选top、right、bottom、left指定某一个边的宽度

- 边框的颜色 border-color

规则同边框的宽度 border-width，如果忽略自动使用color颜色

- 边框的样式 border-style

规则同边框的宽度 border-width，默认值是none，solid表示实线、dotted点状虚线、dashed虚线、double双线

边框可以简写一个属性border按以上三个属性值顺序使用

#### 内边距(padding)

四个方向：top、right、bottom、left。内边距设置会影响**盒子大小**，背景颜色会延伸到内边距上。一个盒子的可见框大小由内容区、内边距、边框共同决定，计算时都要加上。padding简写形式同 边框的宽度 border-width。

#### 外边距(margin)

外边距不会影响盒子可见框大小，影响**盒子位置**，一个四个方向同padding，通常是设置左上外边距，右下外边距会移动其他元素，bottom的值会影响下方元素移动。简写同上

### 水平方向的布局

元素在其父元素水平方向的位置由以下七个属性共同决定

```
margin-left + border-left + padding-left + width + padding-right + border-right + margin-right = 其父 元素内容区的宽度(必须满足)
```

如果等式不成立，则成为**过度约束**，等式会自动调整。调整情况：

* 如果七个值**没有**值为auto的情况，浏览器会调整margin

* 如果某**一个**属性值为auto，则调整此属性的值使等式成立

* 如果将一个**宽度**和一个**外边距**设置为auto，则宽度会调整到最大，设置为auto的外边距会自动为0

* 如果将**三个值**都设置为auto，则外边距都是0，宽度最大

* 如果将**两个外边距**设置为auto，**宽度固定值**，则会将外边距设置为相同的值所以我们经常利用这个特点来使一个元素 在其父元素中水平居中

  > 示例:
  > width:xxxpx;
  > margin:0 auto;
  
  

### 垂直方向的布局

子元素在父元素内容区排列，如果子元素大小超过了父元素，则会从父元素中溢出(overflow)，使用overflow属性设置父元素对溢出子元素的处理。可选值：

* visible 默认值子元素会从父元素中溢出，在父元素外部的位置显示
* hidden 溢出内容将会被裁剪不会显示
* scroll 生成**两个滚动条**，通过滚动条来查看完整的内容
* auto **根据需要**生成滚动条

### 垂直外边距折叠


相邻的垂直方向外边距会发生重叠现象。有以下两种情况

1. 兄弟元素之间
   兄弟元素间的相邻垂直外边距会取两者之间的较大值(两者都是正值)
   特殊情况:

   * 如果相邻的外边距一正一负，则取两者的和。
   * 如果相邻的外边距都是负值，则取两者中绝对值较大的

   同号折叠(取最大值)，异号相加。兄弟元素之间的外边距的重叠，对于开发是有利的，所以不需要进行处理

2. 父子元素
   父子元素间相邻外边距，子元素的会传递给父元素(上外边距) ，父子外边距的折叠会影响到页面的布局，必须要进行处理

### 行内元素盒模型

行内元素不支持设置宽度和高度，但是可以设置padding、border、margin，设置属性后不垂直方向不会影响页面布局。

`display`用来设置元素显示类型，可选值：

* inline 将元素设置为行内元素
* block 将元素设置为块元素
* inline-block 将元素设置为行内元素，行内块，既可以设置高宽又不会独占一行
* table 将元素设置为一个表格
* none 元素不在页面中显示

`visibility`用来设置元素的显示状态，可选值：

* visible 默认值，元素在页面中正常显示
* hidden 元素在页面中隐藏不显示，但是**占据页面位置**

### 浏览器默认样式

通常情况，浏览器都会为元素设置一些默认样式，默认样式会影响页面布局，需要去除浏览器默认样式。

```
*{
	margin: 0;
	padding: 0;
}
```

真正项目还是需要一个一个标签清除标签。

清除默认样式表

[normalize.css](https://github.com/necolas/normalize.css)	对默认样式进行了统一

[reset.css](https://meyerweb.com/eric/tools/css/reset/reset.css)	直接去除了浏览器的默认样式

### 盒子的尺寸

默认情况下，盒子可见框大小由内容区、内边距、边框共同决定。可以设置`box-sizing`属性值设置盒子尺寸计算方式：

* content-box 默认值，宽度高度设置内容区大小
* border-box 宽度高度值设置整个盒子可见框大小，即会调整自动调整内容区大小

### 轮廓阴影和圆角

`box-shadow`设置元素阴影样式，阴影不会影响页面布局。缩写格式

```
box-shadow: 水平偏移量 垂直偏移量 阴影的模糊半径 阴影的颜色
```

`outline`属性用来设置元素的轮廓线，用法和`border`一样，区别是轮廓线不会影响可见框大小，边框占用可见框大小。

`border-radius`属性设置圆角，圆角设置园的半径大小

浮动

## 浮动

浮动主要作用是让页面中的元素进行水平排列。

浮动的特点：

1. 浮动的元素会完全脱离文档流，不在占据文档中的位置。不需要满足水平等式
2. 设置浮动会向父元素的左侧或右侧移动。浮动元素默认不会从父元素中移出
3. 浮动元素向左向右移动时不会超过它前面的元素。向上也不会高过前一个兄弟元素。

脱离文档流的特点：

**块元素**不在独占页面一行，高度和宽度默认被内容撑开。**行内元素**脱离文档流以后会变成块元素，特点和块元素一样。脱离文档流以后，不需要区分块元素和行内元素了。

### 高度塌陷

指在浮动布局中，父元素的高度是由子元素撑开的，但是子元素设置浮动以后脱离文档流，无法撑起父元素导致父元素高度丢失。父元素高度丢失后进一步导致页面布局混乱。

解决办法：为父元素开启BFC（Block Formatting Context）块级格式化环境，开启BFC以后该元素会变成一个独立的布局区域。特点包括：

* 不会被浮动元素所覆盖
* 子元素和父元素外边距不会重叠
* 元素可以包含浮动的子元素

开启BFC的方法：

* 设置元素浮动（不推荐）
* 设置元素为行内块元素（会失去宽度）
* 设置overflow属性为一个非visible的值(hidden)

[Block formatting context](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Block_formatting_context)

### clear属性

如果不希望某个元素受到其他浮动元素的影响而改变位置，可以设置`clear`属性清除影响。可选值：`left`、`right`、`both`（清除两侧中最大影响的那侧）。原理：设置清除浮动以后，浏览器会为元素添加一个上边距，使其位置不受其他元素影响。

### 使用after伪解决高度塌陷

使需要浮动的子类后跟一个清除浮动影响的兄弟类，并设置为块元素独占一行。

```css
.box1::after{
	display: block;
	clear: both;
}
```

同样的概念可以解决父类和子类外边距重叠问题

```css
.box1::before{
	display: table;
}
```

**clearfix**类可以同时解决**高度塌陷**和**外边距重叠**问题

```
.clearfix::before,
.clearfix::after{
	content:'';
	display: table;
	clear: both;
}
```

## 定位

通过定位可以将元素摆放到页面中的任意位置，使用`position`属性来设置定位。可选值：

* static，默认值，元素是静止的没有开启定位
* relative，相对定位
* absolute，绝对定位
* fixed，固定定位
* sticky，粘滞定位

### 相对定位

使用**relative**相对定位以后，需要设置`offset`偏移量来设置元素位置，可选值：top、bottom、left、right，偏移量相对的位置是元素原来在文档流中的位置。

开启相对定位以后会提升元素层级，但是没有脱离文档流。不会元素的性质（块、行内）

### 绝对定位

使用**absolute**绝对定位以后：

1. 元素会从文档流中脱离，并且改变元素性质（行内变块，宽高被内容撑开） 

2. 元素提升一个层级
3. 绝对定位是相对于去**包含块**进行定位的

**包含块**指离当前元素最近的祖先块元素，行内元素可不能算。

**绝对定位的包含块**：离元素最近的，并且开启了定位的祖先元素，如果所有祖先元素都没有开启，则根元素html就是初始包含块。自绝父相

### 固定定位

**fixed**固定定位大部分特点和**absolute**绝对定位相同，唯一不同的是固定定位永远参照于浏览器的窗口进行定位。~~广告位~~

### 粘滞定位

**sticky**粘滞定位大部分特点和**relative**相对定位相同，唯一不同的是可以设置`offset`属性在其经过滚动到达某个位置时将其固定。IE不兼容

### 补充

开启定位后，水平方向布局等式需要添加`offset`属性的值。

开启定位以后，可以通过设置`z-index`属性来设置元素层级。越大层级越高，如果为设置层级，则根据元素顺序显示最后的元素。祖先元素的层级再高也不会盖住后代元素
