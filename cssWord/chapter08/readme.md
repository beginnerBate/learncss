# 第八章 强大的文本处理能力

## 1. 关于font-size
### 1.1 font-size和ex、em、rem的关系
1. ex是字符x的高度 
1. 1em的计算值等同于当前元素所在font-size计算值
```html
<!-- em使用场景 -->
  1. 图文内容展示场景，对此进行弹性布局 如<h1> 到 <h5> <p> 等语文本内容展示的元素margin都是用em作为单位
  2. 如果使用svg图片的建议svg高度如下
  svg{
    width:1em;
    height:1em;
  }
```
1. rem 就是root em 根元素em的大小 rem是css3单位 IE9以上兼容
### 1.2font-size的关键字属性值
1. 相对尺寸关键字 larger smaller 分别对应 <big> <small>
2. 绝对尺寸关键字 
* xx-large --h1  
* x-large -- h2 
* large   ---h3 
* medium---初始值
* small  --h5
* x-small  --h6
* xx-small  
#  大佬划重点了！！！
1. 即使是定宽的传统桌面端网页，也需要做响应式处理，尤其是针对 1200 像素宽度设
计的网页，但只需要响应到 800 像素即可，可以保证至少有 1.5 倍的缩放空间，如果做到这一
步，那么是否需要响应浏览器的字号设置这一点就可以忽略
2. 如果困各种原因无法做响应式处理，也没有必要全局都使用相对单位，毕竟成本等现
实问题摆在那里，其实只需要在图文内容为主的重要局部区域使用可缩放的 font-size 处理
即可。例如，小说网站的阅读页、微信公众号文章展示区、私信对话内容区、搜索引擎的落地
页、评论区等，都强烈建议摒弃 px 单位，而采用下面的实践策略
* 容器设置 font-size:medium，此时，这个局部展示区域的字号就跟着浏览器的设
置走了，默认计算值是 16px。
* 容器内的文字字号全部使用相对单位，如百分比值或者 em 都可以，然后基于 16px 进
行转换。例如：
```css
  .article{ font-size:medium}
  .article h1 {font-size:2em; margin:.875em 0;}
  .article p {font-size:87.5%; margin:1em 0}
```
同时使用自适应流体布局，间距什么的也使用相对单位，例如上面 margin 使用的是
em 单位。于是，当用户改变了浏览器的字号后，整个阅读区域的所有字样甚至布局都
会跟着放大，文字一下子就看清楚了。这种局部处理的好处在于，页面的导航、侧边
栏这些不需要长时间阅读的模块还是原来的像素布局，还是那么精致，丝毫不受影响。
就这么很微小的变动，就可以让你的网页在可访问性这一块超越大多数的网站，何乐
而不为？
可以看到，绝对尺寸关键字在实际项目中还有很有价值的，但有价值的仅仅是 medium，
至于其他关键字，作用仅限于字面上的那点儿，大家了解一下即可。
### 1.3 font-size:0 与文本隐藏
```css
/* 隐藏logo 对应元素的文字 */
.logo{
  font-size:0;
}
```
## 2. 关于font-family
1. 属性值: 字体名|字体族
```css
/* 字体名  */
body {
font-family: 'PingFang SC', 'Microsoft Yahei';
}
/* 字体族 */
/* 但是，“字体族”分为很多类，MDN 上文档分类如下： */
font-family: serif;
font-family: sans-serif;
font-family: monospace;
font-family: cursive;
font-family: fantasy;
font-family: system-ui;
/* 具体含义解释如下。 */
• serif：衬线字体。
• sans-serif：无衬线字体。
• monospace：等宽字体。
• cursive：手写字体。
• fantasy：奇幻字体。
• system-ui：系统 UI 字体。
```
2. 了解衬线字体和无衬线字体
```css
所谓衬线字体，通俗讲就是笔画开始、结束的地方有额外
装饰而且笔画的粗细会有所不同的字体

无衬线字体没有这些额外的装饰，而且笔画的粗细差不多

我们在移动端 Web 开发的时候，虽然设备的默认中文字体不一样，但都是无衬线，都挺好
看的，因此可以直接使用下面的 CSS 代码：
body {
font-family: sans-serif;
}
```
3. 等宽字体了解一下 朋友
```
1．等宽字体与代码呈现
2．等宽字体与图形呈现案例一则

3．ch 单位与等宽字体布局
1ch 表示一个0字符的宽度 是个css属性 
```
## 3. 字体家族其他成员
1. font-weight
1. font-style
```css
font-style: normal;
font-style: italic;
font-style: oblique;
```
## 4. 关于font
1. 使用关键字值的 font 属性
```css
font:caption | icon | menu | message-box | small-caption | status-bar

• caption：活动窗口标题栏使用的字体。
• icon：包含图标内容所使用的字体，如所有文件夹名称、文件名称、磁盘名称，甚至浏览器窗口标题所使用的字体。
• menu：菜单使用的字体，如文件夹菜单。
• message-box：消息盒里面使用的字体。
• small-caption：调色板标题所使用的字体。
• status-bar：窗体状态栏使用的字体。
```
# 大佬划重点了！！！
```css
/* 三选一即可 */
html { font: menu; }
body { font-size: 16px; }

html { font: small-caption; }
body { font-size: 16px; }

html { font: status-bar; }
body { font-size: 16px; }
“我有选择恐惧症，不知该使用哪一个”，那就选最短最好记的那个：
html { font: menu; }
body { font-size: 16px; }
```
## 5. @font face有需要了解一下？ 朋友
```css
@font-face {
font-family: 'example';
src: url(example.ttf);
font-style: normal;
font-weight: normal;
unicode-range: U+0025-00FF;
}
```
## 6. 关于文本控制 
1. text-indent 与内联元素缩进
```
（1）text-indent 仅对第一行内联盒子内容有效。
（2）非替换元素以外的 display 计算值为 inline 的内联元素设置 text-indent 值无
效，如果计算值是 inline-block/inline-table 则会生效。因此，如果父级块状元素设置
了 text-indent 属性值，子 inline-block/inline-table 需要设置 text-indent:0
重置。
（3）<input>标签按钮 text-indent 值无效。
（4）<button>标签按钮 text-indent 值有效，但是存在兼容性差异，IE 浏览器理解为
单标签，百分比值按照容器计算，而 Chrome 和 Firefox 浏览器标签内还有其他 Shadow DOM 元
素，因此百分比值是按照自身的尺寸计算的。
（5）<input>和<textarea>输入框的 text-indent 在低版本 IE 浏览器下有兼容问题
```
2. letter-spacing 与字符间距
3. word-spacing 与单词间距
```
（1）都具有继承性。
（2）默认值都是 normal 而不是 0。通常情况下，两者表现并无差异。
（3）都支持负值，都可以让字符重叠，但是对于 inline-block 和 inline-table 元素
却存在兼容性差异，Chrome 浏览器下可以重叠，IE 和 Firefox 浏览器下则再大的负值也不会重
叠，因此不适合使用 word-spacing 来清除空白间隙。
（4）都支持小数值，如 word-spacing:0.5px。
（5）在目前的 CSS2.1 规范中，并不支持百分比值，但新的草案中新增了对百分值的支持，
是根据相对于字符的“步进宽度”（advance width）计算的。这属于新世界内容，本书不做介绍。
（6）间隔算法都会受到 text-align:justify 两端对齐的影响。
```
4. 了解 word-break 和 word-wrap 的区别
5. white-space 与换行和空格的控制
## 7. :first-letter/:first-line伪元素了解一下嘛？朋友 :)=<