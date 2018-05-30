# 2018年css学习历程 
前言
2014年参加工作到2018年三年多了，本以为css掌握已经很好了，但是看了cssword之后发现自己的css的水平还有待提高，所以打算把css好好学习一下，并且记录一下。
# button 按钮 
> 写一个按钮类 以后直接使用
## 1.需求分析
主题按钮
信息按钮
警告按钮
危险按钮
## 2.使用 label 和 button 配合
label-btn.css
```
<!-- html -->
<button id="btn"></button>
<label for="btn">按钮</label>
button{
  position: absoulte;
  clip:rect(0 0 0 0)
}
label{
  display:inline-block;
  line-height:20px;
  padding:10px;
}
``` 