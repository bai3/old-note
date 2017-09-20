---
title: CSS3
date: 2017-06-08 18:44:31
tags: 
	- CSS
	- CSS3
categories: note
---

# CSS3初步认识

## CSS3简介

### CSS3模块

一些重要的CSS3模块

- 选择器
- 盒模型
- 背景和边框
- 文字特效
- 2D/3D转换
- 动画
- 多列布局
- 用户界面<!--more-->

## CSS3边框

### CSS3圆角

在CSS3中border-radius属性被创建圆角

### CSS3盒阴影

在CSS3中添加box-shadow属性

实例

```css
div{
  box-shadow: 10px 10px 5px #888888;
}
```

### CSS3边界图片

你可以使用图像创建一个边框

## CSS3 圆角

### CSS3 border-radius -指定每个圆角



## CSS33背景

CSS3背景属性：

- background-image
- background-size
- background-origin
- background-clip

### CSS3 background-image属性

CSS3中可以通过background-image属性添加背景图片。

不同的背景图像用逗号隔开，所有图片中显示在最顶端(最顶层)的为第一张。

实例：

```css
#example{
  background-image: url(img_flwr.gif),url(paper.gif);
  background-position: right bottom,left top;
  backgrond-repeat: no-repeat, repeat;
}
```



### CSS3 background-size属性

background-size指定背景图像的大小

> 你也可以指定像素或百分比大小，指定的大小是相对于父元素的宽度和高度的百分比的大小



### CSS3  background-Origin属性



background-Origin属性指定了背景图像的位置区域

content-box，padding-box和border-box区域内可以放置背景图片

### CSS3 background-clip属性

 CSS3中background-clip背景剪裁属性是从指定位置开始绘制的

content-box，padding-box和border-box三个可选参数



## CSS3渐变

CSS3定义了两种类型的渐变

- 线性渐变-向下/向上/向左/向右/对角方向
- 径向渐变-由它们的中心定义

### 使用透明度

CSS3渐变也支持透明度，可以创建减弱变淡的效果。



## CSS3文本效果

- text-shadow
- box-shadow
- text-overflow（文本溢出）
- word-wrap(单词换行)
- word-break（文本拆分换行）



## CSS3字体

### 使用你需要的字体

在新的@font-face规则中，你必须首先定义字体的名称，然后指向该字体文件。

如需为HTML元素使用字体，请通过font-family属性来引用字体的名称

```css
<style>
@font-face{
  font-family: myFirstFont;
  src: url(sansation_light.woff);
}
div{
  font-family: myFirstFont;
}
</style>
```

## CSS3 2D转换

- translate()移动
- rotate()旋转
- scale()元素的增减
- skew()坐标轴的倾斜角度
- matrix()包含上面所有功能

## CSS3 3D转换

- rotateX()
- rotateY()

## CSS3过渡

### 它是如何工作？

CSS3过渡是元素从一种样式改变为另一种的效果。

要实现这一点，必须规定两项内容：

- 指定要添加效果的CSS属性
- 指定效果的持续时间

实例：

```css
div{
  transition-property: width;
  transition-duration: 1s;//过渡效果花费的时间1s
  transition-timing-function: linear;//规定过渡效果的时间曲线
  transition_delay: 2;//延迟2秒执行
}
```

## CSS3动画

### CSS3@keyframes规则

@keyframes规则是创建动画。@keyframes规则内指定一个CSS样式和动画将逐步从目前的样式更改为新的样式。



### CSS3动画

当在@keyframes创建动画，把它绑定到一个选择器，否则动画不会有任何效果。指定至少这两个CSS3的动画属性绑定向一个选择器：

- 规定动画的名称
- 规定动画的时长

### CSS3动画是什么？

动画是使元素从一种样式逐渐变化为另一种的效果。

你可以改变任意多的样式任意多的次数，

请用百分比来规定变化发生的时间，或用关键词“from”和“to“，等同于0%和100%。

0%是动画开始，100%是动画的完成



## CSS3多列

### CSS3多列属性

- column-count
- column-gap
- column-rule-style
- column-rule-width
- column-rule-color
- column-rule
- column-span
- column-width

### CSS3 创建多列

column-count属性指定了需要分割的列数。

### CSS3列与列的间隙

column-gap属性指定了列与列间的间隙

### CSS3列边框

column-rule-style 属性指定了列与列间的边框样式。

column-rule-width属性指定了两列的边框厚度

column-rule-color属性指定两列的边框颜色



## 指定元素跨越多少列

### 指定列的宽度

column-width属性指定了列的宽度

## CSS3用户界面

- resize
- box-sizing
- outline-offset



### CSS3 调整尺寸

CSS3中，resize属性指定一个元素是否应该由用户去调整大小



### CSS3 方框大小调整

box-sizing属性允许你以确切的方式定义适应某个区域的具体内容

### CSS3外形修饰

outline-offset属性对轮廓进行偏移，并在超出边框边缘的位置绘制轮廓。

轮廓与边框有两点不同：

- 轮廓不占用空间
- 轮廓可能是非矩形

## CSS3图片

### 响应式图片

响应式图片会自动适配各种尺寸的屏幕

实例：

```css
img{
  max-width: 100%;
  height: auto;
}
```

### 图片滤镜

CSS filter属性可为元素添加可是效果（例如模糊或饱和度）

