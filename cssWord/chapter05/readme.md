# 第五章 内联元素与流
## 5.1 字母x ----CSS世界中隐匿的举足轻重的角色
### 5.1.1 字母x 与css世界的基线
>字母 x 的下边缘（线）就是我们的基线
### 5.1.2 字母 x 与 CSS 中的 x-height
### 5.1.3 字母 x 与 CSS 中的 ex
>不受字体和字号影响的内联元素的垂直居中对齐效果
```css
.icon-arrow{
  display:inline-block;
  width:20px;
  height:1ex;
  background: url(awwow.png) no repeat center;
}
```
## 5.2 内联元素的基石 line-height
>本节中 line-height 的内容会涉及很多内联盒模型的知识，因此，务必先要掌3.4.2节关于内联盒模型的知识。另外，下文中所有的“行高”指的就是 line-height
### 5.2.1 内联元素的高度之本 line-height
>1. <div>高度是由行高决定
>2. 行距 = line-height - font-size
>3.  line-height 不仅是内联元素高度的基石，而且还是整个 CSS 世界高度体基石。
### 5.2.2 为什么line-height可以让内联元素“垂直居中”

### 5.2.3 深入line-height的各类属性值
>line-height 的默认值是 normal，还支持数值、百分比值以及长度值。
```css
body {
line-height: 1.42858;
font-size: 14px;
}
```
### 5.2.4 内联元素line-height的“大值特性”
>无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的
## 5.3 line-height的好朋友vertical-align
### 5.3.1 vertical-align家族基本认识
```css
/* 线类 baseline (default)、top、middle、bottom */
/* 文本类 text-top、text-bottom */
/* 上下标类, sub、super */
/* 数值百分比类 20px 2em 20% */
```
### 5.3.2 vertical-align作用前提
>只能应用于内联元素以及 display 值为 table-cell 的元素。
>对 table-cell 元素而言，vertical-align 起作用的是 table-cell
### 5.3.3 vertical-align和 line-height 之间的关系
```css
  .box {line-height:32px;}
  .box > span {font-size:34px;}
  <div class="box">
   x<span>文字</span>
  </div>
  /* 
  （1）图片块状化。可以一口气干掉“幽灵空白节点”、line-height 和 vertical-
align。
（2）容器 line-height 足够小。只要半行间距小到字母 x 的下边缘位置或者再往上，自
然就没有了撑开底部间隙高度空间了。比方说，容器设置 line-height:0。
（3）容器 font-size 足够小。此方法要想生效，需要容器的 line-height 属性值和当
前 font-size 相关，如 line-height:1.5 或者 line-height:150%之类；否则只会让下
面的间隙变得更大，因为基线位置因字符 x 变小而往上升了。
（4）图片设置其他 vertical-align 属性值。间隙的产生原因之一就
是基线对齐，所以我们设置 vertical-align 的值为 top、middle、
bottom 中的任意一个都是可以的。
   */
```
### 5.3.4 深入理解 vertical-align 线性类属性值
#### inline-block和baseline
### 5.3.5 深入理解 vertical-align 文本类属性值
```HTML
<p>
  • vertical-align:text-top ：盒子的顶部和父级内容区域的顶部对齐。
  • vertical-align:text-bottom ：盒子的底部和父级内容区域的底部对齐。
</p>
```
### 5.3.6 简单了解 vertical-align 上标下标类属性值
>vertical-align 上标下标类属性值指的就是 sub 和 super 两个值
### 5.3.7 无处不在的 vertical-align
### 5.3.8 基于 vertical-align 属性的水平垂直居中弹框
