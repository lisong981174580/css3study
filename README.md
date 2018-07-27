## css3
### 一、选择器
#### 常用的（IE8以上）
1.* 通配符选择器

2.,,,群组选择器

3.> 子选择器

4.+ 选择元素后紧跟的第一个兄弟元素

5.~ 选择元素后所有紧跟的所有兄弟元素

6.属性选择器、属性包含选择器
```
    //选择类型为text的input
    input[type=text]:{
    }
    //选择herf属性值包含#的
    a[href~="#"]{
    }

   //选择herf属性值以#开头的
    a[href^="#"]{
    }

   //选择herf属性值以#结尾的
    a[href$="123#"]{
    }

   //选择herf属性值为value或者value-开头的
    a[href|="#"]{
    }
```
#### 动态伪类（IE8以上）
```
a:link{};
a:hover{};
a:active{};
a:visited{};
input:focus{}
```
1.link 锚点伪类（a)

2.hover 鼠标移入后的颜色（a)

3.active 按下后的颜色（a)

4.visited 访问后的颜色（a);

5.focus 获取焦点后(input)

#### UI元素状态伪类(IE9以上）
> 我们把":enabled",":disabled",":checked"伪类称为UI元素状态的伪类

1.disabled 主要用在input
```
<style>
  input:disable{} //选择不可编辑的
  input:enabled{} //选择可编辑的
</style>
<input type="text" disable="disable">
<input type="text" >
```
#### nth选择器
##### 基本类
1.:first-child 选择属于其父元素的首个子元素的每个Elenent元素

2.:last-child 选择属于其父元素的最后子元素的每个Elenent元素

3.:nth-child(n) 选择器匹配属于其父元素的第n个子元素，不论元素的类型

4.:nth-last-child(n)  //从后往前匹配

5.nth-of-child //匹配特定类型的

6.nth-last-of-type //从后往前匹配

7.only-child //匹配作为子元素唯一的子元素
#####  关于参数n
> 可以巧妙的利用n
```
//选择某元素下第n个Element
:nth-child(n){}
//选择某元素下奇数个Element
:nth-child(odd){} 或者 :nth-child(2n-1){}
//选择某元素下偶数个Element  或者 :nth-child(2n){}
:nth-child(even){}

```

#### 特殊的
1.:empty 选择器匹配没有子元素（包括文本节点）的每个元素
```
//匹配没有子元素的div
div:empty{}
```
2.(:not) 否定选择器
```
nav > a:not(:last-of-type){}
```
#### 伪元素
1.::first-line 选择文本的第一行（用于块级元素）
```
p::first-line{}
```
2.::first-letter 选择文本的第一个（用于块级元素）
```
p::first-letter{}
```
3.::before在元素内容前插入新内容
> 第一个子元素、行级元素、内容通过content插入
```
div::before{content:'插入的内容'}
```
4.::after在元素内容后插入新内容
> 多用于清除浮动
```
// clear:left 清除左浮动
// clear:right 清除右浮动
// clear:both 清除两边浮动
div::after{
 clear:both;
 content:'';//如果没有这个，浏览器会认为没有内容插入
 disolay:block;//必须是块级的
}
```
5.::selection
> 用于设置在浏览器中选中文本后的前景色如背景色
```
div::selection{
}
```
### 二、属性
#### 边框与圆角
* border 边框
* border-radius边框圆角
```
//单位:px、%、rem、em、vm
//如果是%则相对于元素本身
//椭圆
  border-radius:50%
```
* border-image 边框图片

#### 阴影属性
* box-shadoow属性
> 可以设置一个或多个下拉阴影的框
```
box-shadow:50px 30px 0 0 yellow inset;//水平偏移 垂直偏移 模糊程度 扩展距离  颜色 内阴影
```

#### background属性
> background:clor position  size repeat origin  clip attachment image;
* background-clip:border-box|padding-box|content-box;//背景图片显示区域
* background-origin:border-box|padding-box|content-box;//指定background-position属性应该是相对位置;
* background-size:length|precentage|contain|cover;//图像尺寸
> cover:把背景图片缩放到最大一个不留白的程度  完整填充
> contain:把背景图片完整显示出来，但是可能留白
* background-image:url(),url();//多图片显示
* background-attachment:fiexd;//是否滚屏

#### 渐变
##### 线性渐变
* background:liner-gradient(direction|angle,color-stop1 10%,color-stop2 50%,...) //线性渐变
* background:repeating-liner-gradient(direction|angle,color-stop1 10%,color-stop2 20%,...) //重复线性渐变

##### 径向渐变
> 从中间向外拉伸
* background:radial-gradient(center,shape size,color-stop1 10%,color-stop2 50%,...) //径向渐变
* background:repeating-radial-gradient(center,shape size,color-stop1 10%,color-stop2 50%,...) //重复径向渐变

#### 文本属性
* text-shadow:h-shadow v-shadow  blur  color; //文本阴影
* text-outline:thickness blur color ; //规定文本轮廓(没有浏览器支持)
* word-break:normal|break-all|keep-all;//规定文本自动换换行的处理方法
* word-wrap:normal|break-word; //允许长单词或url地址换行到下一行
* text-align-last:auto|left|right|center|justify|start|end|initial|inherit;//文本最后一行的对齐方式

#### 字体属性
> 字体库网址：https://www.fontsquirrel.com/tools/webfont-generator
* @font-face
```
@font-face{
  font-family:字体名称;
  src:字体存放路径;
  font-weight:;
  font-style:;
}
```
#### css3转换（tansform属性）
* 2d转换
```
 /*旋转*/
    transform: rotate(20deg);
    /*移动*/
    transform: translateX(20px);
    transform: translateY(20px);
    transform: translate(20px,20px);
    /*缩放*/
    transform: scaleX(1);
    transform: scaleY(1);
    transform: scale(1,1);
    /*扭曲*/
    transform: skewX(15deg);
    transform: skewY(15deg);
    transform: skew(15deg,15deg);
```
* 3d转换
```
   /*旋转*/
    transform: rotateX(20deg);
    transform: rotateY(20deg);
    transform: rotateZ(20deg);
    transform: rotate3d(1,1,1,20deg);
    /*移动*/
    transform: translateX(20px);
    transform: translateY(20px);
    transform: translateZ(20px);
    transform: translate3d(20px,20px,20px);

    /*缩放*/
    transform: scaleX(1);
    transform: scaleY(1);
    transform: scaleZ(1);
    transform: scale3d(1,1,1);
```
* transform-origin属性
> transform-origin属性允许您更改转换元素的位置
```
//基本点在左上角
 transform-origin: left top;
```
* 矩阵
```
transform: matrix(a,b,c,d,tx,ty);

```
* transform-style
> 指定嵌套元素怎样在三维空间中呈现
```
 transform-style:preserve-3d|flat;
```
* perspective
> 指定观察者与[z=0]平面的距离，使具有三维位置变换的元素产生透视效果
```
 perspective: 100000|none;

```
* backface-visibility:visibity|hidden;
> 指定元素背面向用户是否可见

#### css3过度（transition属性）
> transition:property duration timing-funcion  delay;
> 允许css的属性值在一定的时间内平滑地过度
* transition-property:none|all|property;// 参与过度的属性
* transition-duration: time;//过度时间
* transition-timing-function: ease|liner|ease-in(很多）;
* transition-delay: time;//延时

#### css3动画（animation)
> animation:name  duration  timing-function  delay iteration-count direction fill-mode play-state
> 视觉暂留原理 0.34s
*  animation-name:keyfreamename|none; //动画名称
*  animation-duration: time;//动画持续时间
*  animation-timing-function: ease|liner|ease-in(很多）;//动画方式
*  animation-delay: time;//延时
*  animation-iteration-count: infinite|数字;//循环次数，infinite无数次
* animation-direction: normal|reverse|alternate|;//检索或设置对象在循环中是否反向运动
* animation-fill-mode:none|forwards|backwards|both ;//规定当动画不播放时，要用应到的元素样式
* animation-play-state:paused|running ;//指定动画是否正在运行或者暂停
* @keyframes
> 关键帧，可以指定任何顺序排列来决定animation动画变化的关键位置
```
@keyframes mymove
{
    from {top:0px;}
    to {top:200px;}
}

@keyframes mymove2
{
    0%   {top:0px;}
    25%  {top:200px;}
    50%  {top:100px;}
    75%  {top:200px;}
    100% {top:0px;}
}

```
* will-change
> 提前通知浏览器元素将要做什么动画，让浏览器提前准备合适的优化设置
> 增强页面渲染性能，css的动画、变形、渐变并不会自动触发GPU加速，而是使用浏览器稍慢的软件渲染引擎（除非是3d转换),代价是占用RAM和GPU存储空间
```
  will-change: auto|scroll-position|contents|<custom-ident>|<animateable-feature>;
  auto:没有特定的意图，适用于他通常所做的任何启发式和优化；
  scroll-position:表示将要改变元素的位置；
  contents:表示将要改变元素的内容
  <custom-ident>:明确指定将要改变的属性与给定的名称
  <animateable-feature>:  可动画的一些特征值，比如left、top、margin等

```
#### css3多列属性（columns)
> 设置或检索对象的列数和每列的宽度，是一个复合属性
> columns:每列的宽度 列数;
* column-gap:<length>|normal;
> 设置检索对象的列与列之间的间距
* column-rule
> 设置检索列与列之间的边框
* colum-span
> 设置或检索对象元素是否横跨所有的列
* column-fill
> 设置或检索所有对象所有列的高度是否统一
* column-break-before
> 设置或检索对象之前是否断行

#### css3用户界面
* appearance:none|button|button-bevel....;
> 设置或检索外观按照本地默认样式
* text-overflow:clip|ellipsis
> 当块级<overflow>为非visible时，定义内联内容溢出其块容器是否截断
> clip:当内联内容溢出块容器时，将溢出部分裁剪掉
> ellipsis:当内联内容溢出块容器时，将溢出部分替换为（...)
```
.box{
    width: 100px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

```
*  white-space: nowrap
> 禁止文本换行
```
 .ant-table td ,.ant-table th{ 
    white-space: nowrap;
 }
```
* outline:宽度|样式|颜色
> 指定轮廓边框的宽度、样式和颜色
> 设置或检索对象外的线条轮廓，不占用布局空间
* outline-width:10px;
> 定义轮廓宽度
* outline-color:<color>|invert;invert(使用背景色的反色);
> 轮廓颜色
* outline-style:none|dotted|solid;
> 轮廓样式
* outline-offset:<length>;
> 轮廓偏移值

* nav-index:auto|<number>;
> 设置检索对象的导航顺序

* cursor
> 设置鼠标光标样式

* zoom：normal|<number>|percenttage
> 设置或检索对象的缩放比例

* box-sizing:boder-box|content-box;
> 设置或检索对象的盒模型组成模式

* resize：none|both|horizontal|vertical
> 设置或检索对象区域是否允许用户缩放，调节元素尺寸比大小

* ime-mode：auto|normal|active|inactive|disabled
> 设置或检索是否允许用户激活输入中文、韩文、日文等输入法状态

* user-select：none|text|all|element
> 内容是否允许复制

* pointer-events
> 设置或检索在何时成为属性事件的taraget


### 三、单位
* vm
> 相对于视口的宽度。视口被均分为100单位的vw
* rem
> 相对长度单位。相对于根元素(即html元素)font-size计算值的倍数
* em
>相对长度单位。相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。

### 四、css优化
* position-fixed代替background-attachment;
* 带图片的元素放在伪元素中
* 巧用will-change
