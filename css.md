# Css网页添加样式

***注释时采用"/**/"***

## 选择器

选择器：选中元素
方式
1.ID选择器(特定ID值的元素(#+ID))
2.元素选择器(选择同一元素名称的所有元素/使用的作用对象太广，全局匹配，所以使用较少)
3.类选择器(class\样式\(.+类名))

```元素选择器\ID选择\class

<!-- 元素选择器 -->
#h1{
    color=green;
    text-align:center;
}
<h1> 标题一</h1>

<!-- ID选择 -->
#ted_tset {
        color: red;
        font-size: 3em;
        text-align: center;
     }
<p id="ted_tset"> Lorem2 </p>

<!-- class 选择 -->
.red-big-center {
            color: red;
            font-size: 3em;
            text-align: center;
     }
<p class="red-big-center">Lorem ipsum dolor sit amet.</p>
```

## 书写位置

```style
<style>
<!-- ... -->
</style>
***最好能够放于head***
```

## CSS代码书写位置

1.内部样式表

书写在style元素中

```内部
<style>
.red{
  font-size:3em;
}

</style>
```

2.内联样式表，元素样式表

直接书写在元素的style属性中

```内联

 <h1 style="color:red; background-color:lightblue;">内联样式示意 </h>

```

3.外部样式表[推荐]
***将样式书写到独立的css文件中。***
> 需要在html文件中写入href="./example.css"对css文件进行引用

```link
<link rel="stylesheet" href="./css/index">
***注意，link没有</link>***
```

1). 外部样式可以解决多页面样式重复的问题
2). 有利于浏览器缓存，从而提高页面响应速度
3). 有利于代码分离（HTML和CSS），更容易阅读和维护

## 常见样式声明

1. color
2. background-color

**预设值**：定义好的单词

**三原色，色值**：光学三原色（红、绿、蓝），每个颜色可以使用0-255之间的数字来表达，色值。

```rgb
rgb表示法：
rgb(0, 255, 0)
hex（16进制）表示法：
 #红绿蓝
```

常见颜色值颜色

```常见颜色值颜色
马尔斯绿： #008c8c
淘宝红：#ff4400, #f40
黑色：#000000，#000
白色：#ffffff, #fff
红：#ff0000, #f00
绿：#00ff00, #0f0
蓝：#0000ff, #00f
紫：#f0f
青：#0ff
黄：#ff0
灰色：#ccc
```

3.font-size
元素内部文字的尺寸大小

1）px：像素，绝对单位，简单的理解为文字的高度占多少个像素
2）em：相对单位，相对于父元素的字体大小(em及父元素字体大小)
每个元素必须有字体大小，如果没有声明，则直接使用父元素的字体大小，如果没有父元素（html），则使用基准字号(浏览器中的规定的型号)
> user agent，UA，用户代理（浏览器）

4.font-weight
>font-weight=normal(400)(默认)
>font-weight=bold(加粗)
>strong，默认加粗
文字粗细程度，可以取值数字，可以取值为预设值

5.font-family
文字类型
必须用户计算机中存在的字体才会有效。
使用多个字体，以匹配不同环境
>sans-serif，非衬线字体，前边的都不能用，则选择一个非衬线字体

```exp
div{
            font-family: consolas,翩翩体-简,微软雅黑,Arial,sans-serif
        }
<!-- 如果有则用没有则下一个 -->
<!-- 前边的都不能用，则选择一个非衬线字体 -->
```

7.font-style
字体样式，通常用它设置斜体
> i元素(倾斜)，默认样式，是倾斜字体; 实际使用中，通常用它表示一个图标（icon）
> 加粗strong(重要的、不能忽略的内容)、em元素(强调)
7.text-decoration

文本修饰，给文本加线。

```t_d
text-decoration:line-through(穿过文字)
text-decoration:underline(下划线)
text-decoration:none(无样式)
```

> a元素
> del元素：错误的内容
> s元素：过期的内容

```<del>exp
<a href>百度</a>(去掉超链接下的线，使其不显示)
成语：<del>章</del>张口就来
活动价格：1.8，原价：<s>998</s>
```

8.text-indent
首行文本缩进
9.line-height
(1) 每行文本的高度，该值越大，每行文本的距离越大。
(2) 设置行高为容器的高度，可以让单行文本垂直居中
(3) 行高可以设置为纯数字，表示相对于当前元素的字体大小
***防止由于字体大小和行高发生冲突导致重叠现象***
10.width 宽度
11.height 高度

```exp
        p{
            background:#008c8c;
            color:#fff;
            height: 50px;
            line-height: 50px;
        }
```

12.letter-space 文字间隙
13.text-align 元素内部文字的水平排列方式
>左置、居中、右置

## 选择器2

选择器：帮助你精准的选中想要的元素

### 简单选择器

1. ID选择器
2. 元素选择器
3. 类选择器
4. 通配符选择器

```exp
*，选中所有元素
*{
  color:red;
}
```

5.属性选择器
根据属性名和属性值选中元素

```exp
/* 存在title属性的<a> 元素 */
a[title] {
  color: purple;
}

/* 存在href属性并且属性值匹配"https://example.org"的<a> 元素 */
a[href="https://example.org"] {
  color: green;
}

/* 存在href属性并且属性值包含"example"的<a> 元素 */
a[href*="example"] {
  font-size: 2em;
}

/* 存在href属性并且属性值结尾是".org"的<a> 元素 */
a[href$=".org"] {
  font-style: italic;
}
<!-- italic倾斜 -->
/* 存在class属性并且属性值包含以空格分隔的"logo"的<a>元素 */
a[class~="logo"] {
  padding: 2px;
}
```

```grammer
语法
[attr]
表示带有以 attr 命名的属性的元素。
[attr=value]
表示带有以 attr 命名的属性，且属性值为 value 的元素。
[attr~=value]
表示带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少有一个值为 value。
[attr|=value]
表示带有以 attr 命名的属性的元素，属性值为“value”或是以“value-”为前缀（"-"为连字符，Unicode 编码为 U+002D）开头。典型的应用场景是用来匹配语言简写代码（如 zh-CN，zh-TW 可以用 zh 作为 value）。
[attr^=value]
表示带有以 attr 命名的属性，且属性值是以 value 开头的元素。
[attr$=value]
表示带有以 attr 命名的属性，且属性值是以 value 结尾的元素。
[attr*=value]
表示带有以 attr 命名的属性，且属性值至少包含一个 value 值的元素。
[attr operator value i]
在属性选择器的右方括号前添加一个用空格隔开的字母 i（或 I），可以在匹配属性值时忽略大小写（支持 ASCII 字符范围之内的字母）。
[attr operator value s]
在属性选择器的右方括号前添加一个用空格隔开的字母 s（或 S），可以在匹配属性值时区分大小写（支持 ASCII 字符范围之内的字母）。
```

6.伪选择器

选中某些元素的某种状态
***(顺序如下)***
1）link: 超链接未访问时的状态

2）visited: 超链接访问过后的状态

3）hover: 鼠标悬停状态

4）active：激活状态，鼠标按下状态

>记忆爱恨法则：love hate(lvha)

```exp
/* 鼠标按下时的a元素 */
/* a:active{
    color:#008c8c;
} */
```

7.伪元素选择器
< before after

```exp
<!-- 书名号的显示 -->
span::before{
content:"《";
color:red;
}

span::after{
content:"》";
color:red;
}

<p>
<span>傲慢与偏见</span>这本书的作者是列夫托尔斯泰
</p>

```

### 选择器的组合

1. 并且

```and
p {
    text-indent: 2em;
    line-height: 2;
}

 p.red {
    color: red;
}

```

2.后代元素 —— 空格

```hou
.red li {
    color: #008c8c;}
<!--表示选择了某一类 带有red特性的后代元素li  -->
```

3.子元素 —— >

```子
.abc>.bcd{
    color:red;
}
```

4.相邻兄弟元素 —— +
>下一个兄弟元素
5.后面出现的所有兄弟元素 —— ~

### 选择器的并列

多个选择器, 用逗号分隔

## 层叠

声明冲突：同一个样式，多次应用到同一个元素

层叠：解决声明冲突的过程，浏览器自动处理（权重计算）
1.比较重要性

重要性从高到底：

> 作者样式表：开发者书写的样式

1） 作者样式表中的!important样式
2)  作者样式表中的普通样式
3)  浏览器默认样式表中的样式

2.比较特殊性

看选择器

总体规则：选择器选中的范围越窄，越特殊

具体规则：通过选择器，计算出一个4位数
<（x x x x）

1. 千位：如果是内联样式，记1，否则记0
2. 百位：等于选择器中所有id选择器的数量
3. 十位：等于选择器中所有类选择器、属性选择器、伪类选择器的数量
4. 个位：等于选择器中所有元素选择器、伪元素选择器的数量

```number
a {/* 0001 */ color: red; }
body a {/* 0002 */color: #fff;}
div ul a {/* 0003 */color: green; }
#mydiv #myul a {/* 0201 */color: gray; }
#mydiv #myul .mylink {/* 0210 */color: #008c8c;}
#mydiv #myul :link{/* 0210 */color:chocolate;}
```

3.比较源次序
代码书写靠后的胜出

## 应用

1. 重置样式表
书写一些作者样式，覆盖浏览器的默认样式

重置样式表 -> 浏览器的默认样式

常见的重置样式表：normalize.css、reset.css、meyer.css

2.爱恨法则(lvha)
link > visited > hover > active

```ai
先用reset再用自己的特殊样式
    <link rel="stylesheet" href="css/reset.css">
    <link rel="stylesheet" href="css/mystyle.css">
```
