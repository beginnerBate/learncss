# 第六章 流的破坏与保护

## 6.1 魔鬼属性float
### 6.1.1 float 的本质与特性
>浮动的本质就是为了实现文字环绕效果
### 6.1.2 float的作用机制
>父元素的高度塌陷
### 6.1.3 float 更深入的作用机制
```html
  <h3>标题<a>更多</a></h3>
  <!-- 浮动锚点 浮动参考指的是浮动元素对齐参考的实体 -->
```
### 6.1.4 float 和流体布局
>利用margin-left 和 margin-right 实现两栏布局 或者三栏布局
##6.2 float的天然克星clear 
#### 6.2.1 什么是 clear 属性
```css
clear:both
```
#### 6.2.2 成事不足败事有余的 clear

##6.3 CSS世界的结界 ---- BFC
> BFC 全称为 block formatting context，中文为“块级格式化上下文”
1. BFC 元素是不可能发生 margin 重叠的
1. BFC 元素也可以用来清除浮动的影响
```html
• <html>根元素；
• float 的值不为 none；
• overflow 的值为 auto、scroll 或 hidden；
• display 的值为 table-cell、table-caption 和 inline-block 中的任何一个；
• position 的值不为 relative 和 static
换言之，只要元素符合上面任意一个条件，就无须使用 clear:both 属性去清除浮动的
影响了。因此，不要见到一个<div>元素就加个类似.clearfix 的类名，否则只能暴露你孱
弱的 CSS 基本功。
```
#### 6.3.2 BFC与流体布局
>BFC 的结界特性最重要的用途其实不是去 margin 重叠或者是清除 float 影响，而是实现更健壮、更智能的自适应布局
##6.4 最佳结界overflow
```css
这里分享一个可以让页面滚动条不发生晃动的小技巧，即使用如下 CSS 代码：
html {
overflow-y: scroll; /* for IE8 */
}
:root {
overflow-y: auto;
overflow-x: hidden;
}
:root body {
position: absolute;
}
body {
width: 100vw;
overflow: hidden;
}
```
##6.5 float的兄弟position:absolute

##6.6 absolute 与 overflow

##6.7 absolute 与 clip

##6.8 absolute的流体特征

##6.9 position:relative才是大哥

##6.10 强悍的position:fixed固定定位


