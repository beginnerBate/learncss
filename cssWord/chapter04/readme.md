# 第四章 盒尺寸四大家族
> 盒尺寸的4个盒子 content box 、padding box、 border-box、 margin box 分别对应css世界中的content 、padding 、 border 、margin

## 4.1 深入理解content

###  4.1.1 content与替换元素
1. 什么是替换元素
```
内容可以被替换 如: img 标签
img object video iframe 或者表单元素 textarea 和 input 
```
> 替换元素的特性
1. 内容外观不受页面上css的影响 需要用appearance属性
2. 有自己的尺寸 默认是 300px × 150px 
3. 在很多CSS属性上有自己的一套表现规则 vertical-align 在替换元素中基线 是baseline
---
2. 替换元素的默认 display 值
3. 替换元素的尺寸计算规则
> 分为3类 固有尺寸、HTML尺寸和CSS尺寸
```css
<!-- css重置加上 -->
img { display: inline-block; }
```
###  4.1.2 content内容生成技术
1. content辅助元素生成
```CSS
.clear:after{
  content:'';
  display:table; /* 也可以是block */
  clear:both;
}
```
2. 两端对齐 
2. content 字符内容生成技术 跳过 有点复杂css 计数器
## 4.2 温和的padding属性

### 4.2.1 padding与元素的尺寸
在 默认情况下 padding 会加入行盒高度计算 
### 4.2.2 padding的百分比值
1. 不支持负值
2. 支持百分比 百分比的值无论是水平方向还是垂直方向的都是相对宽度计算的！
### 4.2.3 标签元素内置的padding
1. ol/ul 列表内置的padding-left 单位是px chrome下面是40px 22px 是比较好的设定值
2. 很多表单元素都内置padding
```HTML
    <input>/<textarea>
    <button></button>
    <select></select>
    <!-- button的padding 最难控制 -->
``` 
```CSS
  button{padding:0;}
  button::-moz-focus-inner {padding:0;}
  button:{overflow:visiable;}
```
> <label>元素实现button
```css
 <!-- html -->
 <button id="btn"></button>
 <label for="btn">按钮</label>
 <!-- css -->
 button {
   position:absoulte;
   clip:rect(0 0 0 0);
 }
 label{
   display:inline-block;
   line-height:20px;
   padding:10px;
 }
```
### 4.2.4 padding 与图形绘制 
1. 三道杠css padding实现
``` CSS
.icon-menu{
  display:inline-block;
  width:140px;
  height:10px;
  padding:35px 0;
  border-top:10px solid;
  border-bottom:10px solid;
  background-color:currentColor;
  background-clip:content-box;
}
```
2. 双层圆点实现
```css
.icon-dot{
  display:inline-block;
  width:100px;
  height:100px;
  padding:10px;
  border:10px solid;
  border-radius:50%;
  background-color:currentColor;
  background-clip:content-box;
}
```
## 4.3 激进的margin属性

### 4.3.1 margin 与元素尺寸以及相关布局
#### 元素尺寸
1. 元素尺寸 height + padding + border == offsetHeight
2. 元素内部尺寸 padding + height == clientWidth 元素可视尺寸
3. 元素外部尺寸 padding + border + margin + height 大小肯能是负数
#### margin 与元素的内部尺寸
1. 只要元素的尺寸表现符合“充分利用可用空间”, 无论是水平方向还是垂直方向，都可以通过margin改变尺寸
2. 通过margin 负值实现两端对齐
```css
  ul{
    margin-right:-20px;
  }
  ul > li {
    float:left;
    width:100px;
    margin-right:20px;
  }
```
#### margin 与元素的外部尺寸
1. margin 尺寸实现等高布局经典案例
```css
  .column-box{
    overflow: hidden;
  }
  .column-left,
  .column-right{
    margin-bottom:-9999px;
    padding-bottom:9999px;
  }
```
### 4.3.2 margin的百分比值
>相对于宽度计算
### 4.3.3 正确看待css世界里的margin合并
#### 1.什么是margin合并? <br>
>块级元素的上外边距（margin-top）与下外边距（margin-bottom）有时会合并为单个外边距这样的现场称为"margin 合并"

#### 2.margin合并的3种情况
```html
<!-- 1.相邻兄弟元素margin合并 -->
p{ margin: 1em 0;}
<p> 第一行 </p>
<p> 第二行 </p>

<!-- 2. 父级和第一个/最后一个子元素 -->
<div class="father">
  <div class="son" style="margin-top:80px"></div>
</div>
<div class="father">
  <div class="son" style="margin-top:80px"></div>
</div>
<div class="father" style="margin-top:80px">
  <div class="son" style="margin-top:80px"></div>
</div>

<!-- 
  对于margin-top合并 可以进行如下操作 {满足一个即可} 
  • 父元素设置为块状格式化上下文元素；
  • 父元素设置 border-top 值；
  • 父元素设置 padding-top 值；
  • 父元素和第一个子元素之间添加内联元素进行分隔
  -->

<!-- 对于margin-bottom 可以进行如下操作 {满足一个即可}
    • 父元素设置为块状格式化上下文元素；
    • 父元素设置 border-bottom 值；
    • 父元素设置 padding-bottom 值；
    • 父元素和第一个子元素之间添加内联元素进行分隔
-->


<!-- 3.空块级元素的 margin 合并 -->
<style>
  .father{
    overflow:hidden;
  }
  .son{ margin:1em 0;}
</style>
<div class="father"> 
  <div class="son"></div>
</div>
<!-- 
如果有人不希望空<div>元素有 margin 合并，可以进行如下操作：
• 设置垂直方向的 border；
• 设置垂直方向的 padding；
• 里面添加内联元素（直接 Space 键空格是没用的）；
• 设置 height 或者 min-height。
 -->
```
#### 3.margin合并的计算规则
> 正正取最大 正负值相加 负负最负值
#### 4.margin合并的意义
```CSS
<!-- 无须担心列表之间的间距会很大 -->
.list {
margin-top: 15px;
margin-bottom: 15px;
}
```
### 4.3.4 深入理解css中的margin：auto
> margin:auto 填充规则如下:
> 1. 如果一侧定值，一侧auto，auto为剩余空间大小
> 1. 如果两侧均是auto 那么评分剩余空间 
### 4.3.5 margin无效情形解释
```html
<!-- 
  1. display计算值inline的非替换元素的垂直margin无效
  2. 表格中的<tr> <td> 元素或者设置display计算值是table-cell或者
    table-row的元素的margin都是无效的。
  3. margin合并的时候，更改margin值可能是没有效果的
  4. 绝对定位元素非定位方位的 margin 值“无效”
  5. 定高容器的子元素的 margin-bottom 或者宽度定死的子元素的 margin-right 的
定位“失效
 -->
```

## 4.4 功勋卓越的border
### 4.4.1 为什么border-width-width不支持百分比值
border-width支持若干关键字 
```css
thin : 薄薄的，等同于1px
medium(默认值) : 3px
thick: 4px 
```
### 4.4.2了解各种border-style类型
```
<!-- 1.border-style:none 默认值-->
div{
  border:1px solid;
  border-bottom:0 none;
}

<!-- 2.border-style:solid 实线边框 -->
<!-- 3.border-style:dashed 虚线边框 -->
<!-- 4.border-style:dotted 虚点边框 -->
ie8中的圆角
.box{
  width:150px;
  height:150px;
  overflow:hidden;
}
.dotted{
  width:100%;
  height:100%;
  border:149px dotted #cd0000;
}
<!-- 5.border-style:double 双线边框 -->
.icon-menu{
  display:inline-block;
  width:120px;
  height:20px;
  border-top:60px double;
  border-bottom:20px solid;
}
```
### 4.4.3 border-color和color
```css
border-color 默认值:color
```
### 4.4.4 border与透明边框技巧
```css
  /* 1.右下方background定位的技巧 */
  .box{
    border-right:50px solid transparent;
    background-position:100% 50%;
  }
  /* 2.优雅地增加点击区域大小 */
  .icon-clear{
    height:16px;
    width:16px;
    border:11px solid transparent;
  }
  /* 3. 三角等图形绘制 */
  div{
    width:0;
    border:10px solid;
    border-color:#f30 transparent transparent;
  }
```
### 4.4.5 border与图形构建
```css
/* 4.3.html */
```
### 4.4.6 border等高布局技术