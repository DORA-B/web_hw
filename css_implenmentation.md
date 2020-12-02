# 盒模型

## 盒模型介绍

box：盒子，每个元素在页面中都会生成一个矩形区域（盒子）

盒子类型：
(css属性)

1. 行盒，display等于inline的元素(不换行)
2. 块盒，display等于block的元素(会换行)
display默认值为inline(行盒)

> 浏览器默认样式表设置的块盒：容器元素、h1~h6、p

常见的行盒：span、a、img、video、audio

### 盒子的组成部分

无论是行盒、还是块盒，都由下面几个部分组成，从内到外分别是：

1. 内容  content

```content
width、height，设置的是盒子内容的宽高
内容部分通常叫做整个盒子的**内容盒 content-box**
```

2.填充(内边距)  padding
盒子边框到盒子内容的距离

padding-top、padding-right、padding-bottom、padding-left、

padding: 简写属性

> padding: 上 右 下 左

```exp
padding:50px 50px 50px 50px
最终会转化成：
padding-top
padding-right
padding-bottom
padding-left
```

**填充盒 padding-box**=填充区+内容区

3.边框  border
边框 = 边框样式 + 边框宽度 + 边框颜色

边框样式：border-style(默认non)
边框宽度：border-width(默认0)
边框颜色：border-color
> **边框盒 border-box**=边框+填充区+内容区

```attention
采用简写方式(可连同样式定义)
边框也可以从四个方向定义(顺时针上右下左)
border-top-style
border-right-style
border-bottom-style
border-left-style
```

4.外边距  margin

边框到其他盒子的距离
速写属性同上/上上

```margin

margin-top、margin-right、
margin-bottom、margin-left
```

## 盒模型应用

### 改变宽高范围

默认情况下，width 和 height 设置的是内容盒宽高。衡量设计稿尺寸的时候，往往使用的是边框盒，但设置width和height，则设置的是内容盒。

1. 精确计算
2. CSS3：box-sizing

### 改变背景覆盖范围

默认情况下，背景覆盖边框盒

可以通过background-clip进行修改

### 溢出处理

overflow，控制内容溢出边框盒后的处理方式

```of
overflow:visible(默认情况)
overflow:hidden(溢出隐藏)
overflow：scroll(可滚动查看)
overflow-y:auto(需要滚动条时出现，否则不出现)
text-pverflow:ellipsis(只对于文字溢出的效果，以三个圆点代替溢出部分)
```

### 断词规则

word-break，会影响文字在什么位置被截断换行

normal：普通。CJK字符（文字位置截断），非CJK字符（单词位置截断）

break-all：截断所有。所有字符都在文字处截断(英文在单字处截断)

keep-all：保持所有。所有文字都在单词之间截断(中文则会在一行中一直显示)

### 空白处理

white-space: nowrap(不换行)

```ws
normal不会空白折叠
pre保留空白字
```

## 行盒模型

常见的行盒：包含具体内容的元素

> span、strong、em、i、img、video、audio

1. 盒子沿着内容延伸
(行盒相接时头尾相接)
2. 行盒不能设置宽高
3. 内边距（填充区）
水平方向有效，垂直方向不会实际占据空间。
4. 边框
水平方向有效，垂直方向不会实际占据空间。
5. 外边距
水平方向有效，垂直方向不会实际占据空间。

## 行块盒

display：inline-block 的盒子

1. 不独占一行
2. 盒模型中所有尺寸都有效(垂直和水平)

### 空白折叠

空白折叠，发生在行盒（行块盒）内部 或 行盒（行块盒）之间

### 可替换元素 和 非可替换元素

大部分元素，页面上显示的结果，取决于元素内容，称为**非可替换元素**

少部分元素，页面上显示的结果，取决于元素属性，称为**可替换元素**

可替换元素：img、video、audio

绝大部分可替换元素均为行盒。
> object-fit:fill(默认)图片的适应方式
可替换元素类似于行块盒，盒模型中所有尺寸都有效。

## 常规流

盒模型：规定单个盒子的规则

视觉格式化模型（布局规则）：页面中的多个盒子排列规则

视觉格式化模型，大体上将页面中盒子的排列分为三种方式：

1. 常规流
2. 浮动
3. 定位

## 常规流布局

常规流、文档流、普通文档流、常规文档流

所有元素，默认情况下，都属于常规流布局

总体规则：块盒独占一行，行盒水平依次排列

包含块（containing block）：每个盒子都有它的包含块，包含块决定了盒子的排列区域。

绝大部分情况下：盒子的包含块，为其父元素的内容盒

```p_c
<!-- 盒子的包含块，为其父元素的内容盒 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .parent{
            background: lightblue;
            border: 2px solid;
            padding: 30px;
            margin: 30px;
            width: 600px;
            height: 1000px;
        }
        .child{
            border: 2px solid;
            background: red;
            width: 100px;
            margin: 0 auto;
            height: 50%;
        }
    </style>
</head>
<body>
    <div class="parent">
        <div class="child">
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Similique totam quod quam repellat provident repudiandae, a reprehenderit voluptates fugiat laboriosam eveniet esse voluptas laudantium non porro hic ut neque tempora.
        </div>
    </div>
</body>
</html>
```

> **块盒**

1. 每个块盒的总宽度，必须刚好等于包含块的宽度

宽度的默认值是auto

margin的取值也可以是auto，默认值0

auto：将剩余空间吸收掉

width吸收能力强于margin

若宽度、边框、内边距、外边距计算后，仍然有剩余空间，该剩余空间被margin-right全部吸收

在常规流中，块盒在其包含块中居中，可以定宽、然后左右margin设置为auto。

2.每个块盒垂直方向上的auto值

height:auto， 适应内容的高度

margin:auto， 表示0
3.百分比取值

padding、宽、margin可以取值为百分比

以上的所有百分比相对于包含块的宽度。

高度的百分比：
1）. 包含块的高度是否取决于子元素的高度，设置百分比无效
2）. 包含块的高度不取决于子元素的高度，百分比相对于父元素高度
4.上下外边距的合并

两个常规流块盒，上下外边距相邻，会进行合并。

两个外边距取最大值。
