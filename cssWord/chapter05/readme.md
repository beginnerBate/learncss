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
### 5.2.4 内联元素line-height的“大值特性”
## 5.3 line-height的好朋友vertical-align