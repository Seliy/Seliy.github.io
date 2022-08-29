## CSS

### CSS的优先级顺序: 

~~~
tag中的style  >  id   >   class > tag 
~~~

### CSS/CSS3

#### animation
**实现一个动画效果**

* 使用

  ~~~
  <div class="text-animation"></div>
  style
  .text-animation{
  	width:100px;
  	height:100px;
  	background:red;
  	animatoion: divmove 2s infinite;//infinite 无限次
  	-webkit-animation: divmove 2s infinite;
  	animation-direction: alternate;//到达以后反向运动
  }
  @keyframes divmove{
  	from{
  		left:0px;
  	}
  	to{
  		left:50px;
  	}
  }
  ~~~

  

#### transition

**CSS过渡**

* 方法一：transition-property，transition-duration，transition-delay

> ```css
> #delay {
> font-size: 14px;
> transition-property: font-size;
> transition-duration: 4s;
> transition-delay: 2s;
> }
> 
> #delay:hover {
> font-size: 36px;
> }
> ```

* transition: width 2s, height 2s, background-color 2s, transform 2s;

> ```css
> .box {
>  border-style: solid;
>  border-width: 1px;
>  display: block;
>  width: 100px;
>  height: 100px;
>  background-color: #0000FF;
>  transition: width 2s, height 2s, background-color 2s, transform 2s;
> }
> ```



#### display
**元素的内部和外部显示类型**
* 属性值
| value              | explain                                        |
| ------------------ | ---------------------------------------------- |
| none               | 不会被显示                                     |
| block              | 显示为块级                                     |
| inline             | 默认，显示为内联，元素前后没有换行符           |
| inline-block       | 行内块级元素                                   |
| list-item          | 展示为列表                                     |
| run-in             | 此元素会根据上下文作为块级元素或内联元素展示   |
| table              | 作为块级表格展示                               |
| inline-table       | 作为内联表格来显示                             |
| table-row-group    | 作为一个或多个行的分组来展示                   |
| table-header-group | 作为一个或多个行的分组来展示                   |
| table-footer-group | 作为一个或多个行的分组来展示                   |
| table-row          | 作为一个表格行显示（类似<tr>）                 |
| table-column-group | 作为一个或多个列的分组来显示（类似<colgroup>） |
| table-column       | 作为一个单元格列显示<col>                      |
| table-cell         | 作为一个表格单元格显示<td><th>                 |
| table-caption      | 作为一个表格标题显示（<caption>）              |



#### position
**定位**
* 属性值
| value    | explain                                              |
| -------- | ---------------------------------------------------- |
| static   | 默认值，没有定位                                     |
| relative | 相对定位，相对于其正常位置进行定位                   |
| absolute | 绝对定位，相对于static定位以外的第一个父元素进行定位 |
| fixed    | 绝对定位，相对于浏览器窗口进行定位                   |
| inherit  | 继承父元素position属性的值                           |

#### transform

* rotate(旋转)
* scale(缩放)
* skew(拉伸)
* translate(平移)

* 属性值
| value         | explain      |
| ------------- | ------------ |
| rotate(angle) | 规定角度旋转 |

### sass

##### 介绍

* sass是一个层叠样式表语言
* sass是一个css预处理器
* sass文件后缀为.scss

##### 特点

* sass是一个css扩展语言，可以帮助我们减少css重复的代码，节省开发时间
* sass完全兼容所有版本的css
* sass扩展了css3，增加了规则，变量，混入，选择器，继承，内置函数
* sass生成良好格式化的css代码，易于组织和维护

##### 安装

* npm 安装

  ~~~
  npm install -g sass
  ~~~
  
##### 使用

##### 引入

~~~
@import "@/styles/scrollbar.scss";
//使用@import 引用指定的外部css文件
~~~



##### 变量

~~~
/* 定义变量与值*/
$bgcolor:lightblue;
$fontsize:12px;

/* 使用变量 */
body{
	background-color:$bgcolor;
	font-size:$fontsize;
}
~~~

##### 作用域

###### !gobal

* 介绍

  * 更改全局变量的样式

* 使用

  ~~~
  $gobalColor:red;
  h1{
  	$gobalColor:green !gobal;
  }
  ~~~

  

##### 语法

###### @mixin

* 介绍

  * 定义一个可以在整个样式表中重复使用的样式

* 使用

  ~~~scss
  @mixin important-text{
  	color:red
  }
  ~~~

  

###### @include

* 介绍

  * 可以将混入（mixin）引入到文档中

* 使用

  ~~~scss
  @mixin important-text{
  	color:red
  }
  selector{
  	@include important-text;
  }
  ~~~


###### @extend

* 介绍

  * @extend 指令 告诉Sass 一个选择器的样式从另一个选择器继承

* 使用

  ~~~
  .common-style{
  	border:1px solid red;
  	font-size:1rem;
  }
  .left-style{
  	@extend .common-style
  	width:100px;
  	height:50px;
  	color:#fff;
  }
  .right-style{
  	@extend .common-style
  	width:200px;
  	height:100px;
  	color:blue;
  }
  ~~~

  

###### 添加mixin滚动条样式

* styles/scrollbar.scss 写入以下代码

~~~
@mixin scrollBarStyle() {
  &::-webkit-scrollbar-track-piece {
    -webkit-border-radius: 0;
  }
  &::-webkit-scrollbar {
    width: 5px;
    height: 5px;
  }
  &::-webkit-scrollbar-thumb {
    height: 50px;
    background-color: #e8e8e8;
    -webkit-border-radius: 6px;
    outline-offset: -2px;
    filter: alpha(opacity = 50);
    -moz-opacity: 0.5;
    -khtml-opacity: 0.5;
    opacity: 0.5;
  }
  &::-webkit-scrollbar-thumb:hover {
    height: 50px;
    background-color: #b8b8b8;
    -webkit-border-radius: 6px;
    cursor: pointer;
  }
}

@mixin scrollBarStyle2() {
  &::-webkit-scrollbar-track-piece {
    -webkit-border-radius: 0;
  }
  &::-webkit-scrollbar {
    width: 8px;
    height: 5px;
  }
  &::-webkit-scrollbar-thumb {
    height: 50px;
    background-color: #ccc5c5;
    -webkit-border-radius: 6px;
    outline-offset: -2px;
    filter: alpha(opacity = 50);
    -moz-opacity: 0.5;
    -khtml-opacity: 0.5;
    opacity: 0.5;
  }
  &::-webkit-scrollbar-thumb:hover {
    height: 50px;
    background-color: #b8b8b8;
    -webkit-border-radius: 6px;
    cursor: pointer;
  }
}

// 隐藏滚动条
@mixin scrollBarStyle4() {
  &::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(41, 51, 72);
    border-radius: 0px;
  }

  &::-webkit-scrollbar {
    width: 0px;
    border-radius: 0;
  }

  &::-webkit-scrollbar-thumb {
    background: #735c2685;
    border-radius: 0px;
  }
}

@mixin scrollBarStyle3() {
  &::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(41, 51, 72);
    border-radius: 10px;
  }

  &::-webkit-scrollbar {
    width: 6px;
    border-radius: 10px;
  }

  &::-webkit-scrollbar-thumb {
    background: #735c2685;
    border-radius: 10px;
  }
}
~~~

* vue 文件中引用 

~~~
@import "@/styles/scrollbar.scss";
~~~

* vue 文件中使用

~~~
.modal-total-params {
  background: #222c40;
  padding: 10px;
  height: 350px;
  overflow-y: auto;
  @include scrollBarStyle4;
}
~~~

