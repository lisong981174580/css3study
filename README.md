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
* border-radius边框圆角
```
//单位:px、%、rem、em、vm
//如果是%则相对于元素本身
//椭圆
border-radius:50%
```
* border 边框

### 三、单位
* vm
> 相对于视口的宽度。视口被均分为100单位的vw
* rem
> 相对长度单位。相对于根元素(即html元素)font-size计算值的倍数
* em
>相对长度单位。相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。

