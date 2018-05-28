# 第三章 流、元素与基本尺寸
## 3.1 块级元素
### 3.1.1 为什么list-item 元素会出现项目符号
> 因为块级元素和内联元素不能满足需求，于是加了一个 '标记盒子'
### 3.1.2 display:inline-table的盒子是怎样组成的
> 外面是内联盒子 里面是块级盒子
### 3.1.3 width和height作用在哪个盒子上面
> 里面的盒子
## 3.2 width/height作用的具体细节
> width 的 默认值 是auto  4种不同的宽度表现
1. 充分利用可用空间。 div p 默认宽度100% 于父级容器
2. 收缩与包裹。 浮动 绝对定位 , inline-block table 元素
3. 收缩到最小
4. 超出容器限制 > 恰如一江春水向东流，流到断崖也不回头 ---max-content
### 3.2.1 深藏不露的width:auto
> 外部尺寸与流体特性
1. 正常宽度流
2. 格式化宽度 <绝对定位模型中出现>
> 内部尺寸与流体特性
1. 包裹性
2. 首选最小宽度  <中文和英文字符一样> word-break:break-all
3. 最大宽度 连续内联盒子的宽度

### 3.2.2 width值作用的细节
1. 流动性丢失
1. 与现实世界表现不一致的困扰

### 3.2.3 CSS流体布局下的宽度分离原则

> css中的width属性不与影响宽度的padding/border 属性共存

1. 为何要宽度分离  不需要烧脑子去计算了，而且页面结构反而更稳固
1. 可能的挑战

### 3.2.4 改变width/height作用细节的box-sizing
```javascript
 input, textarea, img, video, object {
  box-sizing: border-box;
  }
````
### 3.2.5 相对简单而单纯的height:auto

### 3.2.6 关于height:100%

1. 为何height：100% 无效

## 3.3 CSSmin-width/CSSmax-width 和 min-height/max-height二三事
> 1. 为流体而生的min-width/max-width
> 1. 与众不同的初始值
``` javascript
  min-height/min-width 的初始值auto
  max-width max-height 的初始值none
```
> 1. 超越!important ,超越最大
## 3.4 内联元素
### 3.4.1  哪些元素是内联元素
display的外面盒子的值是display
### 3.4.2  内联事件深入的基础---内联盒模型
** css进阶标志知识点 需要反复拿来体味
1. 内容区域 围绕文字看不见的盒子 ，其大小受字符本身特性控制
```
<p> 这是一行普通的文字，这里有个<em>em</em>标签。</p>
```
2. 内联盒子
```
<span> <a> <em>  匿名内联盒子

```
3. 行框盒子 （line box）
```
<p> [jdjdjdjdjjd] </p>
```
4. 包含盒子
```
<p>
```
### 3.4.3  幽灵空白节点
