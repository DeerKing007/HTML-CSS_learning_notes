# HTML(超文本标记语言)

#1 什么是HTML？

**HTML** ，即HyperText Markup Language（超文本标记语言）。我们平时所说的网页，即为使用HTML语言来书写的文件，也叫做**超文本文档**。

##1.1 HTML

HTML是超文本标记语言，可以用标记来实现一些普通文本实现不了的操作（超文本操作），这里所说的标记，就是指标签。  

HTML标签一般由开始标签、标签体、结束标签和标签属性组成。

按照规范要求，HTML标签采用小写字母书写。HTML的属性部分可以使用双引号，也可以使用单引号。

 

##1.2 最基本的HTML结构

```html
<!doctype html>
<html>
	<head>
    <title>网页标题</title>
    </head>
    <body>
    网页主体（网页正文）
    </body>
</html>
```

### **1.3 HTML注释**

在HTML文件中，使用`<!-- -->`来添加注释。 
```html
<!-- 单行注释 -->
<!-- 多行
注释 -->
(多行注释在markdown里会有显示问题，但在html中是可以被正常认可的)
```

#2 网页的基本组成

标签的定义：标记，是一些符号，用来区分文档中的不同部分。
单标签：比如`<img/>`
双标签：开始标签+闭合标签
标签组成：标签 标签属性 （属性：用来描述标签的特征）

##2.1 **网页头部**

####  2.1.1 `<meta>`标签
```
一般需要写在<head></head>中，是网页的元信息。
指定网页为UTF-8编码（HTML5专属）：<meta charset="utf-8">
```

#### 2.1.2 `<title></title>`标签

当前网页的标题，会出现在浏览器的标题栏/标签栏。也会作为将当前网页添加到收藏夹/书签时使用的默认名称。

```
按照HTML规范，<title></title>是唯一需要包含到<head></head>中的标签。
```

### 2.2 **网页主体**

```
网页主体指的是<body></body>中的部分，一般用于书写一些需要给用户展示的内容。一般由标签符号构成。 常用标签：h1-h6,p,br,img,span,div,a,三种列表标签，table，form以及特殊字符
```

#### 2.2.1 字符实体

```
<body>
    这 是一些内     容。
</body>
```

使用浏览器打开这个文件，可以发现：“这”和“是”中间的单个空格是正常显示的，而“内”和“容”之间的多个空格会显示成只有一个空格。这是由于浏览器会自动截短大于一个的空格，目的是为了让程序员更精确的控制文本格式。

如果想在HTML中使用不会被截短的空格，要使用**字符实体**`&nbsp;`表示。 

| 字符实体 | 显示描述 | 描述              |
| -------- | -------- | ----------------- |
| `&nbsp;` |          | 空格              |
| `&lt;`   | <        | 小于号            |
| `&gt;`   | >        | 大于号            |
| `&amp;`  | &        | 和号              |
| `yen;`   | ￥       | 元                |
| `copy;`  | ©        | 版权（copyright） |

#### 2.2.2 简单的标签

#####换行标签：`<br>`和`<hr>`

像多个空格一样，直接出现在HTML中的回车换行也会被截短成一个空格。如果想在HTML中使用不会被截短的换行，要使用标签`<br>`代替。如果添加一个占据一行的水平线，可以使用`<hr>`。

`<br>`：另起一行

`<hr/>`：定义一条水平分隔线，不是成对出现，只有一个。

##### 标题标签：`<h1></h1>`

定义标题，可以定义相同的标题标识，且相同的标题字体一样大。（我不理解）

```html
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
<!-- 字体依次减小 -->
```

##### 段落标签：`<p></p>`

定义一个段落，会自动在自己上下产生一些空白。另起一个段落，单独成行。
```html
<p>第一段文字。</p>
<p>第二段文字。</p>
<p>第三段文字。</p>
```

##### 小标签

定义斜体：`<i></i>`，快捷方式ctrl i
定义粗字体：`<b></b>`，快捷方式ctrl b
加下划线：`<u></u>`，快捷方式ctrl u
文字上标：`<sup></sup>`
文字下标：`<sub></sub>`





## 3 HTML中常用的标签运用

### 3.1 表格（重点）

表格在网页刚刚出现不久时主要作为一种布局方式存在,目前主要用来显示数据 。
表格不再是单一标签，而是由多个标签组成的组合效果。

`<table></table>`标签为表格域，表格的其他部分必须在table标签以内。
该标签属性有border(表格外边框的厚度)/cellspacing(单元格之间空白)/cellpadding（单元边沿与其内容之间的空白）/width与height（分为<=0与>0两种）
`<tr></tr>`标签为表格的行row。 
`<td></td>`标签为标签的列colum，必须写在tr标签以内。该标签属性有：align valign height属性。
`<th></th>`标签为标签的表头head（不常用），必须写在tr标签以内，会自动对里面的文字加粗居中显示。 

一个两行三列的表格（table的border属性用于显示表格边框）。 

```html
 <table border="1" cellpadding="" cellspacing="" width="" height="" align="center"将整个表格在页面居中>
     <tr valign="top"垂直>
         <th rowsapn="" colspan="" align="" valign="" width="" height="" >
             表头
         </th>
     </tr>
     <tr>
        <td>第二行的第一列</td>
        <td>第二行的第二列</td>
        <td>第二行的第三列</td>
    </tr>
    <tr>
        <td>第三行的第一列</td>
        <td>第三行的第二列</td>
        <td>第三行的第三列</td>
    </tr>
</table>
```

表格里面显示的数据或其他元素必须写在td或者th以内。该标签属性有：rowspan（跨行）,colspan（colum span跨列）,aglin（水平对齐）,valign（垂直对齐）,width/height。

#### 3.1.1 列合并与行合并

列合并：使用td标签的**colspan**属性来合并一行中的多列。例如：colspan=2 就是跨2列 。`<td colspan="2" align="center">`包括己身的两列`</td>`
行合并：使用td标签的**rowspan**属性来合并一列中的多行。例如：rowspan=3表示跨3行。`<td rowspan="3" valign="middle">`包括己身的前两行`</td>  `
align属性指定文字水平居中显示left center right ；
valign属性指定文字垂直方向显示效果：top center bottom。

####3.1.2 width和height

以px为单位指定行的高或列的宽 。例如：

```html
<tr height="100">
    <td width="100">hh</td>
</tr>
```



### 3.2列表

列表用来展示一些成系列的内容，在默认样式下，有序列表和无序列表的差别较大。但目前很少采用其默认样式显示。 

有序列表（order-list）：`<ol></ol>`

无序列表（unorder-list，用的最多）：`<ul></ul>`

书写列表里每行的内容：`<li></li>`

自定义列表：`<dl><dt><dd></dd></dt></dl>`

| list-style-position | 列表标记位置                                                 |
| ------------------- | ------------------------------------------------------------ |
| inside              | 列表项目标记放置在文本中，且环绕文本以标记为中心对齐。       |
| outside             | 默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不以标记为中心对齐。 |
| inherit             | 规定应该从父元素继承list-style-position属性的值。            |

| list-style-type      | 无序列表标记类型   | 有序列表标记类型                          |
| -------------------- | ------------------ | ----------------------------------------- |
| none                 | 无标记             | /                                         |
| disc                 | 默认。标记是实心圆 | /                                         |
| circle               | 标记是空心圆       | /                                         |
| square               | 标记是实心方块     | /                                         |
| decimal              | /                  | 有序数字，ol默认，标记是数字（1，2，3……） |
| decimal-leading-zero |                    | 以0开头的数字标记（01，02，03……）         |
| lower-roman          | /                  | 小写罗马数字（）                          |
| upper-roman          | /                  | 大写罗马数字：Ⅰ，Ⅱ，Ⅲ，Ⅳ，Ⅴ，Ⅵ，Ⅶ，Ⅷ，Ⅸ   |
| lower-alpha          | /                  | 有序小写英文字母                          |
| upper-alpha          | /                  | 有序大写英文字母                          |

| 有序列表的其他属性（type） | 作用                                                         |
| -------------------------- | ------------------------------------------------------------ |
| start                      | 定义开始的序号（<ol type="3">，即从3开始标记3，4，5……）      |
| value                      | 在某一列重新开始定义列序号（<li value="4"></li>,不管前面的序号，从这一列开始以4开头定义） |

标记类型的设置--list-style-type:none disc

标记位置的设置--list-style-position:outside inside

标记设置为图片--list-style-image:url()

综上：list-style:type position image

```html

<!-- 有序列表 -->
<ol>
    <li>浏览器发起请求</li>
    <li>服务器给出响应</li>
    <li>浏览器解析网页</li>
    <li>浏览器渲染网页</li>
</ol>
<!-- 无序列表 -->

<ul>
    <li>开始标签</li>
    <li>标签体</li>
    <li>结束标签</li>
    <li>属性</li>
</ul>
```



### 3.3 表单（特别重点）`<form></form>`

表单用来提供一些可以由用户选择或输入的元素，主要用于收集用户数据提交给服务器，比如登陆注册。 
表单由一个form标签（块级元素）和若干个其他表单元素标签（都是行内元素）组成（*其他表单元素可以不依赖form单独使用*）。用户在填写其他表单元素后，可以**提交**整个表单中**name属性不为空**的表单元素中的数据到服务器。 

#### 3.3.1 `<form></form>`标签

**action**属性规定表单提交的地址。  
**method**属性规定表单提交的方式（取值可以为get或post，之后详细说明）。
**enctype**属性指定数据的编码处理方式（当method=”post”时适用） 

#### 3.3.2 `<input>`元素（重要）

最常见的表单元素，根据其**type**属性的不同取值，可以显示为不同的输入组件。 text文本框，password密码框，radio单选框，checkbox复选框，file文件域，textarea文本域，submit提交按钮，reset重置按钮，button普通按钮。特别注意：当这个按钮处在一个表单内部时，如果不手动指定button的type属性，浏览器可能会将其当做普通按钮或者提交按钮。因此，这时必须为这个标签指定type属性。 表格的**value**属性是最终提交到服务器时数据的获取位置，可以提前给予默认值。 **H5新增一些：placeholder，color，range，number,email,autofocus，tel等**属性用于在用户输入前提示用户。  

```html
<form>
    <!--普通文本输入框-->
    <label for="txt"></label><!--更友好-->
    <input name="uname" type="text" id="txt" placeholder="用户名"><br>
    <!--密码输入框-->
    <input name="upass" type="password" placeholder="密码"><br>

    性别：
    <!--单选框，name属性相同的为同组单选框，checked属性指定默认选中-->
    <input name="gender" type="radio" value="m" checked="checked">男
    <input name="gender" type="radio" value="f">女<br>

    爱好：
    <!--多选框，name属性相同的为同组多选框，checked属性指定默认选中-->
    <input name="hobby" type="checkbox" value="fb">足球
    <input name="hobby" type="checkbox" value="bb">篮球
    <input name="hobby" type="checkbox" value="pp" checked="checked">乒乓球<br>

    出生日期：
    <!--日期选择器，有部分浏览器不支持-->
    <input name="birth" type="date"><br>

    喜欢的颜色：
    <!--颜色选择器，有部分浏览器不支持-->
    <input name="color" type="color"><br>

    头像：
    <!--文件上传组件，有部分浏览器不支持-->
    <input name="head" type="file"><br>

    <!--提交按钮，不要写name属性，可以不写value属性-->
    <input type="submit" value="注册">
    
    <!--重置按钮，不要写name属性，可以不写value属性-->
    <input type="reset"><!--重置，恢复到初始情况-->
    
    <!--普通按钮，不要写name属性，使用value属性表示按钮上的文字-->
    <input type="button" value="按钮">
    
    <!--自定义的滑动条,表示范围-->
    <input type="range" name="" id="" value="" min="" max="" step="" list="" />
    //min：范围的最小值，缺省值是0。
    //max：范围的最大值，缺省值是100。
    //value：可以是整数，也可以是浮点数，缺省值是最大值和最小值之间。
    //step：步长，滑块组件滑动时value变动的最小单位。缺省值是1.如果最小值min是浮点数，step也可以是浮点数。
    //list：就是DataList，目前没有浏览器能实现这个功能。
</form>
```

#### 3.3.3 下拉列表框

下拉列表框可以为用户提供一个包含若干候选项的选择组件。向其添加multiple属性可以称为多选列表框（通过Shift连续多选，通过Ctrl非连续多选）。**注意：提交的内容是用户选中的option对应的value属性。**

单选（使用selected属性指定默认选中）：   

```html
<select name="country">
    <option value="cn" selected="selected">中国</option>
    <option value="usa">美国</option>
    <option value="en">英国</option>
    <option value="au">澳大利亚</option>
</select>
```

多选（使用selected属性指定默认选中）： 

```html
<select name="users" multiple="multiple">
    <option value="zhang3">张三</option>
    <option value="li4" selected="selected">李四</option>
    <option value="wang5" selected="selected">王五</option>
    <option value="zhao6">赵六</option>
</select>
```

#### 3.3.4 `<textarea></textarea>`文本域标签

textarea标签会显示为一个**多行文本输入框**。textarea标签没有value属性，提交的内容是这个标签的标签体。提供默认文本时，也直接写到这个标签体里就可以，**但要注意，这个和其他html标签很大的不同就是其内容中的空格和换行是有效的（也叫预格式化文本）。属性：rows="5" cols="30" 设置大小。row是行（高），column是列（宽）。**

```html
<textarea name="intro">这是一些带  有空     格
和换行

的文字</textarea>
```

#### 3.3.5 `<button></button>`标签

在网页上显示为一个按钮。和input标签中的几个按钮不一样的是，按钮上显示的内容由这个标签的标签体决定，因此可以组合任意行内元素使用，也可以较为自由的指定样式 。

###3.4 图片标签：`<img/>`（重点）

在网页中，可以使用`<img>`标签来显示一个图像。<u>不换行</u>  
对于一个图像，常见的属性有三个： src，ait，title。

####3.4.1 src

图像的来源，可以是一个地址，也可以是一段base64码。标签的src属性是必需的。src属性的值是图像文件的URL，也就是引用该图像的文件的绝对路径或相对路径。

```html
<!--可以是一个网络地址-->
<img src="https://www.baidu.com/img/bd_logo1.png?qua=high">

<!--可以是一个本地地址（一般采用相对路径）-->
<img src="../image/logo.png">

<!--可以是一段base64码（base64码过于庞大，这里仅为示例，无法正常显示）-->
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAhwAAAEC...">
```

####3.4.2 alt

图像的代替文字，当图像无法正确加载时，用于提示用户图片内容的文字。 

```html
<img src="../image/logo1.png" alt="百度一下，你就知道！">
```

####3.4.3 title

不只是图像，所有的标签都可以添加这个属性用于增加一个悬浮提示。 

```html
<img src="../image/logo.png" title="百度一下，你就知道！">
<!-- 图片的大小，即宽度与高度 -->
<img src="../image/flower.jpg" width="200px" height="200px">
```

###3.5 视频标签：`<video></video>`

```html
<video width="200" height="200" src="视频链接" controls></video>
```

**src**属性是必需的，controls属性用于设置视频底部的控制条。

### 3.6 超级链接（重点）`<a></a>`

超级链接用来定义一个访问其他超文本文档（某一部分）的快捷方式，用户可以单击以跳转。 

**target属性**:指定页面在何处打开（不要漏写下划线）

- **_blank**：在新窗口打开。 
- **_self**：在当前窗口打开。（默认）

####3.6.1 跳转到其他网页

```html
<a href="网络地址或本地地址">链接描述</a>

<a herf="http://www.baidu.com/">打开百度</a>

<a herf="http://www.baidu.com/"><img src="../image/logo.png"></a>
```

#### 3.6.2 跳转到网页某一部分

可以使用链接直接跳转到网页某一部分，这叫做锚点跳转。 

声明锚点位置的方式：

1. 任何一个标签的id属性（注意：id属性标签唯一）。
2. 页面顶部（无需声明，固定为#top）。HTML5新增内容模块

跳转到锚点：

```html
<!--跳转到id为bt1的标签-->
<a href="#bt1">跳转到标题1</a> 

<!--跳转到其他页面的锚点-->
<a href="test.html#bt2">跳转到test.html页面的标题2位置</a>

<!--跳转到页面顶部，无需声明锚点-->
<a href="#top">回到顶部</a> 
```

## 4 标签元素分类（块级元素和行内元素是重点）

```html
<!--语义化 标签 p
			p标签 段落
			a标签 超链接
			img标签 图片
			h标签 标题
			table标签 表格标签
			form标签 input 
			div 标签  盒子
			span标签  小标签 文本
			H5新增：header头部，footer尾部，nav标签-导 航
			分类：
			块级元素：独占一行   div p h标签 table标签 form标签 
				-块级元素 可嵌套 行内元素，也可嵌套块级元素
			行内元素：不换行  a img span input
				-不能嵌套块级元素 ，可以嵌套行内元素
			行内块 内联块元素
		-->
```

###  `<div></div>标签`与`<span></span>标签`

> 在html开发中，div与span标签是常用的标签。
> div的语义是division"分割"；span的语义是span"范围、跨度"。

- DIV是**层叠样式表（CSS）**中的定位技术，全称DIVision,ision,即为划分，有时可以称为图层。DIV元素是用来为HTML文档内大块（block-level）的内容提供结构和背景的元素。用于组合块级元素，以便通过样式来对这些元素进行格式化。div在浏览器中默认是不会增加任何的效果改变，但语义变了，div中的所有元素是一个小区域。div标签是一个容器级标签，里面什么都能放，也可以放div标签。
- span是表达“小区域、小跨度”的标签，但是是一个“文本级”的标签。
- `<div>`元素是块级元素，用于组合其他元素的容器，默认的display属性是block；`<span>`元素是内联元素，用作文本的容器，默认的display的属性是inline。
- 块级元素之间会自动换行，内联元素不会。
- 块级元素和行内元素不是一成不变的，只要给块元素定义display:inline，块元素就成了内嵌元素；同理，给内嵌元素定义了display:block就成了块元素。

## 5 标签显示模式（display）

### 5.1 块级元素（block-level）  display属性：block

常见的块元素有`<h1>~<h6>、<p>、<div>、<ul>、<ol>、<li>`等。其中`<div>`标签是最典型的块元素，非常符合布局，所以都喜欢叫CSS+DIV布局。

块级元素的特点：  
1、总是从新行开始 ，独占一行，默认情况下，其宽度自动填满其父元素宽度，宽度默认是容器的100% 。
2、高度、行高（可以设置宽和高，设置了宽度还是独占一行），外边距margin以及内边距padding都可以设置。  
3、可以嵌套块级元素及行内元素。 
4、可以互相转换display:inline变成行内元素。
浏览器默认行为下常见的块级元素：**div**、**h1~h6**、**hr**、**p**、**table**、**form**。 

### 5.2 行内元素（inline-level） display属性：inline

行内元素（内联元素）不占有独立的区域，仅仅靠自身的字体大小和图像尺寸来支撑结构，一般不可以设置宽度、高度、对齐等属性，常用于控制页面中文本的样式。 

常见的行内元素有`<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<ins>、<u>、<span>`等，其中`<span>`标签最典型的行内元素。 

行内元素的特点：  
1、和相邻行内元素在一行上，直到一行排不下，才会换行，其宽度随元素的内容而变化。  
2、设置高、宽无效，但水平方向的padding和margin可以设置，垂直方向的无效。 
3、默认宽度就是它本身内容的宽度。 
4、行内元素只能容纳文本或其他行内元素（a特殊），不可以嵌套块级元素。同理还有这些标签h1,h2,h3,h4,h5,h6,dt，他们都是文字类块级标签，里面不能放其他块级元素。
5、可以互相转换display:block变成块级元素

  注意： 

1. 只有文字才能组成段落，因此 p 里面不能放块级元素。 
2. 链接里面不能再放链接。 

浏览器默认行为下常见的行内元素：**span**、**img**、**font**、**a**、**b**、**i**、**sub**、**sup**、**input**、**button**。 

### 5.3 行内块元素（inline-block） display属性:inline-block

浏览器默认行为下常见的内联块元素：**img**、**input**、**select** 。

在行内元素中有几个特殊的标签——`<img />、<input />、<td>，`可以对它们设置宽高和对齐属性，有些资料可能会称它们为行内块元素。 

行内块元素的特点： 
（1）和相邻行内元素（行内块）在一行上,但是之间会有空白缝隙。
（2）默认宽度就是它本身内容的宽度。
（3）高度，行高、外边距以及内边距都可以控制。 

### 5.4 块级元素与行内元素的区别

块级元素的特点：总是从新行开始 ；高度，行高、外边距以及内边距都可以控制；宽度默认是容器的100%；可以容纳内联元素和其他块元素。 

行内元素的特点：和相邻行内元素在一行上；高、宽无效，但水平方向的padding和margin可以设置，垂直方向的无效；默认宽度就是它本身内容的宽度；行内元素只能容纳文本或则其他行内元素。 

 ### 5.5 标签嵌套规则：

1. 不能交叉嵌套
2. 块级元素嵌套行内元素或者块级元素
3. 行内元素不能嵌套块级元素
4. **块级元素不能放在`<p></p>`里面**
5. 有几个特殊的块级元素只能包含行内元素，不能再包含块级元素，这几个特殊的标签是： h1、h2、h3、h4、h5、h6、p、dt







