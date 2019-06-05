#    CSS

## 1 CSS介绍

**CSS** ，即Cascading Style Sheets（层叠样式表）。可以用来为HTML或者XML添加样式（主要是HTML）。 
**元素是能够指定样式的最小单位，狭义上元素指标签，广义上元素还包括伪元素。** 

CSS注释方法：`/*注释内容*/ `

### 1.1 HTML语言与CSS的联系：

**HTML和CSS之间的关系**:

- HTML：构建页面（人）；CSS：构建HTML元素的样式（化妆师）
- HTML是页面的内容组成，CSS是页面的表现。

仅仅通过HTML语言来改变标签显示样式的话，只能通过HTML属性进行，这有着很多限制和困难：
1. HTML标签提供的有关样式的属性较少。
2. 相似的样式在不同的标签里可能通过不同的属性进行定义，较难记忆。
3. 属性的取值不够严谨规范，浏览器表现差异明显。
4. 需要为每个标签都进行属性指定，标签较多时实现繁琐。

使用CSS就可以解决以上的问题，更加自由和方便的定义标签样式。
1. CSS作用：用于控制网页的外观，修饰和美化html标签的,实现了结构和形式的分离。
2. 使用CSS+DIV的优点 采用CSS+DIV进行网页重构相对与传统的TABLE网页布局而具有以下3个显著优点：**1：表现和内容相分离 2：提高页面浏览速度 3：易于维护和改版**

## 2 CSS的样式表

使用CSS之前，必须先书写一些HTML标签，因为CSS是给HTML标签来赋予样式。
CSS样式表分类：**行内样式表，内嵌样式表，外部样式表**。

### 2.1 行内（内联）样式表：style属性

每个标签都可以添加**style**属性，可以通过这个属性为当前标签添加样式。 `<p style="color:#f00;"></p>`

**书写方便，权重高，但没有实现样式和结构的分离，使用情况较少，只能控制一个标签（少）。**

### 2.2 内嵌样式表：style标签

将CSS代码集中写在HTML文档的head头部标签中，并用style标签定义；语法中，style标签一般位于head标签中title标签之后，也可以把他放在HTML文档的任何地方。

```html
<head>
    <style>
        选择器{
            font-size:24px;
            color:red;
            font-family:"楷体","KaiTi";
        }
    </style>
</head>
```

**部分结构和样式相分离，但没有彻底分离，使用情况较多，可以控制一个页面（中）。**

### 2.3 外部样式表（.css文件与`<link>`）

语法中，link标签需要放在head头部标签中，并且必须指定link标签的三个属性，具体如下：

- href：定义所链接外部样式表文件的url，相对路径或者绝对路径。
- type：定义所链接文档的类型，在这里需要指定为"text/CSS"，表示被链接的外部文件为CSS样式表。
- rel：定义当前文档与被链接文档之间的关系，在这里需要指定为"stylesheet"，表示被链接的文档是一个样式表文件。

**完全实现结构和样式相分离，不过需要引入，使用最多，可以控制整个站点（多）。**

建立一个以css为扩展名的文本文件，在里面键入以下内容： 

```css
选择器{
    font-size:24px;
    color:red;
    font-family:"楷体","KaiTi";
}
```

然后就可以使用`<link>`标签引入到HTML的head标签内 。

```html
<head>
    <link rel="stylesheet" href="css文件路径">
</head>
```



###2.4 导入样式表（不建议直接在HTML中使用） 

导入样式和链接样式比较相似，采用@import样式导入CSS样式表，在HTML初始化时，会被导入导HTML或者CSS文件中，成为文件的一部分，类似内嵌样式。不过在加载文HTML档后再加载样式，所以有时会出现没有样式的情况（很短暂），然后就有样式了。

```html
在HTML中使用：
<style type="text/css">
@import url(style.css);
</style>
在CSS中使用：
@import url(style.css);
```

> 如果需要引入多个CSS文件链接式则需要多写几句，也可以写成一个总的CSS，在里面用导入式导入其他的CSS，然后再用链接式在HTML中链接总的CSS。

### 2.5 样式表的优先级

```html
<!--css样式引入方式：
			-1.行内样式
			-2.内联样式，内嵌样式。style标签 可使用
			-3.外链样式。link 推荐使用  
			-4.外部导入 。。。@import 
			开发：html css js  解耦合
			
			几种引入方式优先级？ 就近原则
			行内样式 优先级最高的 -->
<style>
			div {
				color: red;
				/*字体大小*/
				font-size: 30px;
			}
			
		</style>
		<link rel="stylesheet" type="text/css" href="css/style.css"/>
	</head>
	<body>
		<div class="my-div" id="my_div">
引入方式：1.行内样式 2，内联样式 3.外链样式
		</div>
<!--当前两类样式表中操作的元素，是同一个元素时同一个样式，看权重-->
			
<!--1.同一选择器，样式表引入有无影响？就近 覆盖
	2.同一选择器，样式表引入出现覆盖 就近原则，必须操作的为同一个样式；如果样式不一样，那各自都起效果。
	3.选择器不同的时候，同一样式按权重走，如果不同样式，同上。-->
	4.在标签内定义的优先级最高，其次是<head>中<style>定义的，其次是外部的；<head>标签中如果外部引入在<style>在标签之前引入，那么<style>标签将会覆盖外部引入相同的部分，反之亦然。	
```

### 2.6 CSS的样式设置和规则

**样式设置**：width 宽度 ， height 高度，单位为 px；em，rem，%等；
 background-color 背景颜色 颜色表示三种方式（单词表示法，16进制，rgb(0,0,0)）。

*详细介绍看后面的文本属性*

**样式规则**：

1、选择器用于指定CSS样式作用的HTML对象，花括号内是对该对象设置的具体样式。
2、属性和属性值以"键值对"的形式出现。（声明=属性+属性值，一个选择器中可以有多个声明）
3、属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等。
4、属性和属性值之间用英文“:”连接。
5、多个“键值对”之间用英文";"进行区分。

## 3 选择器（重点）

选择种类包含：
基本选择器（标签选择器，类选择器，ID选择器），
关系选择器（后代选择器，子代选择器，并集选择器，交集选择器），
伪类选择器，伪元素选择器，属性选择器等 。

**通用选择器**：匹配页面中所有元素
语法：*｛属性：值｝
使用场合：定义当前页面中最基本的显示样式，如：字体，大小……

**属性与值**

- 允许出现多个***属性：值***对，每对之间用***;***隔开
- 特点：只作用于在所定义的标签内，其它标签不受影响。

### 3.1 标签选择器

**语法：标签名** 
按照标签的标签名进行选择，可一次选择多个，把某一类表情哦爱你全部选择出来。
**能快速为页面中同类型的标签统一样式，同时这也是它的缺点，不能设置差异化样式。**

```html
<style>
    div{
        color:red;
    }
</style>

<div>第1个div</div><!-- 红色的 -->
<div>第2个div</div><!-- 红色的 -->
<span>第1个div</span>
<span>第2个span</span>
<div>第3个div</div><!-- 红色的 -->
```

### 3.2 id选择器

**语法：#id** 
按照标签的id属性进行选择，该语法中，id名即为HTML元素的id属性值，大多数的HTML元素都可以定义id属性，元素的id值是唯一的，只能对应文档中某一个具体的元素，用法基本和类选择器相同。 

id选择器与类选择器的区别在于使用次数。类选择器（class）好比人的名字，可以多个人重复使用；id选择器好比人的身份证号码，是唯一的，不能重复使用。

```html
<style>
    #div1{
        color:red;
    }
</style>

<div id="div1">id为div1的div</div><!-- 红色的 -->
<div id="div2">id为div2的div</div>
<div id="div3">id为div3的div</div>
```

### 3.3 类选择器

**语法：.class** 
按照标签的class属性进行选择，可一次选择多个。 
- 标签的class属性可以写多个，用空格分隔。
- 一个页面中可以有多个相同的类名, 一个标签也可以设置多个类名,空格隔开即可。

**类选择器最大的优势是可以为元素对象定义单独或相同的样式，可以选择一个或多个标签。**

> 1、长名称或词组可以使用中横线来为选择器命名。
> 2、不建议使用"_"下划线来命名选择器。（输入的时候少按一个shift键；浏览器兼容问题；JS变量命名是用"_"，能良好区分JavaScript变量命名）
>
> 3、不要以纯数字、中文等命名，尽量使用英文字母来表示。

```html
<style>
    .t1{
        color:red;
    }
</style>

<div class="t1">class为t1的div</div><!-- 红色的 -->
<div class="t2">class为t2的div</div>
<span class="t1">class为t1的span</div><!-- 红色的 -->
```

### 3.4 多类名选择器

给标签指定多个类名，达到更多的选择目的。

多类名选择器在后期布局比较复杂的情况下使用较多。

**注意**：

> 1、样式显示效果跟HTML元素中的类名先后顺序没有关系与CSS样式书写的上下顺序有关。
>
> 2、各个类名中间用空格隔开。

### 3.5 通配符选择器（全选择器）

通配符选择器用"*"号表示，它是所有选择器中作用范围最广的，能匹配页面所有的元素。

基本语法：*｛属性1：属性值1；属性2：属性值2；｝

```html
<!--使用通配符选择器定义CSS样式，清除所有HTML标记的默认边距-->
*{
margin:0;
padding:0;
}
```

### 3.6 子元素选择器（javaScript中详细说明）

:nth-child(index) 匹配其父元素下的第n个子（从1开始）

:eq(index) 匹配一个子元素（从0开始）

## 4 复合选择器（关系选择器）

两个或多个基本选择器，通过不同方式连接而成的选择器。

### 4.1 后代选择器

找到指定的标签的所有后代，然后设置属性。
**语法：选择器1 选择器2…… **（父 子 孙）
先找到选择器1，然后在选择器1下找到所有选择器2，最后设置属性。

注意点：

- **后代选择器必须用空格隔开。**
- 后代不一定是儿子，也可以是孙子

### 4.2 子代选择器

子代选择器是两个及以上的选择器同时作用的结果，符合前一个选择器的直接子标签中所有符合后一个选择器的标签被选中，可以一次选择多个。（选中指定父元素的指定子元素）

**语法：选择器1>选择器2** （父>子）

注意点：
1、**子选择器用大于号隔开**

2、子元素选择器在IE6浏览器中不支持

 ### 4.3 并集选择器

并集选择器是两个及以上的基本选择器同时作用的结果，任何形式的选择器都可以，并集选择器是多个选择器通过逗号连接而成的。

**通常用于集体声明。**

 **语法：选择器1,选择器2** ……

```html
h1,h2,h3{color:red;font-size:23px;}
```

### 4.4 交集选择器

交集选择器是由两个选择器直接连接构成，其结果是选中二者各自元素范围的交集，**其中第一必须是标签选择器，第二个必须是类选择器或者id选择器，两个选择器之间不能有空格，必须连续书写。**

**语法：选择器1选择器2 （中间没有空格）** 

```html
h3.class(color:red;font-size:13px;)
```

##5 伪类选择器

###5.1 伪类选择器

伪类选择器是指当一些标签符合某些条件时会被选中的选择器，相当于这些标签有了这些class，但是程序员不必在标签上 手动添加这个（些）class，伪类选择器必须配合其他选择器使用。 **伪类主要有以下几种：**

1. :focus 选中焦点所在的标签（主要是表单元素）。

2. :hover 选中鼠标悬浮上去的标签。

3. :visited 选中被浏览过的超链接。

4. :nth-child(n) 匹配当前元素的父元素中的第n个子元素（从1开始）。

   ```html
   <style>
       li:nth-child(1){
           color:red;
       }
   </style>
   
   <ul>
       <li></li> <!-- 变红 -->
       <li></li>
       <li></li>
   </ul>
   ```

   

5. :last-child 匹配父元素中的最后一个子元素。

6. :first-child 匹配父元素中的第一个子元素。

> 注意写的时候，他们的顺序尽量不要颠倒 按照 lvha 的顺序。 

**提示：chrome的开发者工具可以强行给元素加上伪类，方便调试**

```css
a {   /* a是标签选择器  所有的链接 */
            font-weight: 700;
            font-size: 16px;
            color: gray;
        }
a:hover {   /* :hover 是链接伪类选择器 鼠标经过 */
            color: red; /*  鼠标经过的时候，由原来的 灰色 变成了红色 */
}
```

### 5.2 伪元素选择器（了解）

**和伪类选择器的区别： **
1.伪类选择器依赖现有的元素，伪元素选择器会创建元素。
2.伪类选择器与其他选择器只能使用:分隔，伪元素选择器可以使用::分隔。

**伪元素主要有以下几种（不再重复写出::分隔符）：**

1. :first-letter 将其选择器选出的元素内的第一个文字创建为伪元素，进而可以添加样式。
2. :first-line 将其他选择器选出的元素内的第一行文字创建为伪元素，进而可以添加样式。
3. :before 在其他选择器选出的元素前面创建一个伪元素，内容由content属性指定，进而可以添加样式。
4. :after 在其他选择器选出的元素后面创建一个伪元素，内容由content属性指定，进而可以添加样式。常见最多的是就是清除浮动。

## >sublime快捷方式

sublime可以快速提高我们代码的书写方式

1. 生成标签 直接输入标签名 按tab键即可 比如 div 然后tab 键， 就可以生成；
2. 如果想要生成多个相同标签 加上 * 就可以了 比如 div*3 就可以快速生成3个div；
3. 如果有父子级关系的标签，可以用 > 比如 ul > li就可以了；
4. 如果有兄弟关系的标签，用 + 就可以了 比如 div+p；
5. 如果生成带有类名或者id名字的， 直接写 .demo 或者 #two tab 键就可以了。

##>CSS书写规范

开始就形成良好的书写规范，是专业化的开始。 

###空格规范

【强制】 选择器 与 { 之间必须包含空格。 

示例： .selector { } 

【强制】 属性名与之后的 : 之间不允许包含空格， :与属性值之间必须包含空格。

示例：font-size: 12px;

### 选择器规范

【强制】 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行。 

示例：

```css
/* good */
.post,
.page,
.comment {
    line-height: 1.5;
}

/* bad */
.post, .page, .comment {
    line-height: 1.5;
}
```

【建议】 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。

示例：

```css
/* good */
#username input {}
.comment .avatar {}

/* bad */
.page .header .login #username input {}
.comment div * {}
```

### 属性规范

【强制】 属性定义必须另起一行。

示例：

```css
/* good */
.selector {
    margin: 0;
    padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```

【强制】 属性定义后必须以分号结尾。

示例：

```css
/* good */
.selector {
    margin: 0;
}

/* bad */
.selector {
    margin: 0
}
```

## >CSS三大特性

层叠、继承、优先级是学习CSS必须掌握的三大特性。

### CSS层叠性
所谓层叠性是指多种CSS样式的叠加。 是浏览器处理冲突的一个能力,如果一个属性通过两个相同选择器设置到同一个元素上，那么这个时候一个属性就会将另一个属性层叠掉 。
一般情况下，如果出现样式冲突，则会按照CSS书写的顺序，以最后的样式为准。
1. 样式冲突，遵循的原则是就近原则。 那个样式离着结构近，就执行那个样式。
2. 样式不冲突，不会层叠。

### CSS继承性（重点） 
所谓继承性是指书写CSS样式表时，子标签会继承父标签的某些样式，如文本颜色和字号。想要设置一个可继承的属性，只需将它应用于父元素即可。 
恰当地使用继承可以简化代码，降低CSS样式的复杂性。子元素可以继承父元素的样式（text-，font-，line-这些元素开头的都可以继承，以及color属性） 

### CSS优先性
定义CSS样式时，经常出现两个或更多规则应用在同一元素上，这时就会出现优先级的问题。 
考虑权重时：
```
1、继承样式的权重为0。即在嵌套结构中，不管父元素样式的权重多大，被子元素继承时，他的权重都为0，也就是说子元素定义的样式会覆盖继承来的样式。
2、行内样式优先。应用style属性的元素，其行内样式的权重非常高，可以理解为远大于100。总之，他拥有比上面提高的选择器都大的优先级。
3、权重相同时，CSS遵循就近原则。也就是说靠近元素的样式具有最大的优先级，或者说排在最后的样式优先级最大。
4、CSS定义了一个!important命令，该命令被赋予最大的优先级。也就是说不管权重如何以及样式位置的远近，!important都具有最大优先级。
```

###CSS特殊性（Specificity）

关于CSS权重，我们需要一套计算公式来去计算，这个就是 CSS Specificity，我们称为CSS 特性或称非凡性，它是一个衡量CSS值优先级的一个标准 具体规范入如下：

specificity用一个四位的数 字串(CSS2是三位)来表示，更像四个级别，值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越。

| 继承或者* 的贡献值       | 0,0,0,0  |
| ------------------------ | -------- |
| 每个元素（标签）贡献值为 | 0,0,0,1  |
| 每个类，伪类贡献值为     | 0,0,1,0  |
| 每个ID贡献值为           | 0,1,0,0  |
| 每个行内样式贡献值       | 1,0,0,0  |
| 每个!important贡献值     | ∞ 无穷大 |

 **权重是可以叠加的** 

```
div ul  li   ------>      0,0,0,3

.nav ul li   ------>      0,0,1,2

a:hover      -----—>      0,0,1,1

.nav a       ------>      0,0,1,1   

#nav p       ----->       0,1,0,1
```

 **注意**：
	1、数位之间没有进制 比如说： 0,0,0,5 + 0,0,0,5 =0,0,0,10 而不是 0,0, 1, 0， 所以不会存在10个div能赶上一个类选择器的情况。
	2、继承的权重是 0。

总结优先级：
1. 使用了 !important声明的规则。
2. 内嵌在 HTML 元素的 style属性里面的声明。
3. 使用了 ID 选择器的规则。
4. 使用了类选择器、属性选择器、伪元素和伪类选择器的规则。
5. 使用了元素选择器的规则。
6. 只包含一个通用选择器的规则。
7. 同一类选择器则遵循就近原则。

**总结**：权重是优先级的算法，层叠是优先级的表现 

####！important 的使用

!important写法：(实际应用很少) 

```html
<style>
    div{
        font-size:20px;
        color:red !important;
    }
</style>
<div style="color:blue;">第一个div中的测试文字</div><!-- 变红 -->
<div style="font-size:28px;color:blue;">第二个div中的测试文字</div><!-- 变红，字体变大 -->
```

#### 权值

1.id选择器>类选择器>标签选择器
2.选择器权值：行内1000，id选择器100，类选择器10，标签选择器1，*0,继承样式最低
3.多个选择器选中同一个元素时，看权值；权值相同时，就近原则。
4.使用在属性值后面加一个 !important,增加选择器的权重 可以强制优先级最高，都带有!important时继续按照上述规则 
5.任何由程序员指定的样式优先级都大于浏览器默认样式

**多个选择器选中同一个元素时，看权值**

简单记法：  **!important > style属性 > id > class > 标签 > \* > 浏览器** 

## 6 文本的基本属性

文字颜色：color; font-size 字号；font-family 字体；  font-weight 字体加粗 bold;/正常normal;font-style字体样式 normal/italic 。

**基本语法格式**（综合样式设置）：

选择器{font:font-style font-weight font-size/line-height font-family;}

<!--文字：样式（倾斜） 加粗 字体大小/行高 字体-->

- 使用font属性时，必须按上面语法格式中的顺序来写，不能更换顺序，各个属性以空格隔开。
- 注意：其中不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

###6.1 文字颜色color

使用属性**color**来指定文字颜色，其属性取值是CSS颜色。 

**CSS颜色表（RGB分别代表红绿蓝，a代表alpha不透明度）** 

| 表示形式 | 说明                                                         | 举例                                                         |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 颜色名称 | 通过英文单词指定颜色                                         | red、green、blue                                             |
| HEX      | 通过#RRGGBB或者#RGB的形式用十六进制（#0-9a-f）表示颜色       | f0000（同#f00）、#00ff00（同#0f0）、#0000ff（同#00f）        |
| RGB      | 通过rgb(r,g,b)的形式用三个0-255的数字表示颜色                | rgb(255,0,0),rgb(0,255,0),rgb(0,0,255);或者rgb(100%,0%,0%),百分号不能省，0也不能省百分号 |
| RGBA     | RGB形式的扩展，第四个字母alpha（不透明度）取值范围0~1,不可为负数，表示透明度，0表示完全透明 | rgba(0,0,0,0.6)表示半透明黑色                                |

### 6.2 文字大小font-size

使用属性**font-size**来指定文字大小，其属性取值是数字加CSS单位。 

**CSS单位表** 

| 单位 | 描述（作为文字大小单位）                            | 备注（作为长度单位）                       |
| ---- | --------------------------------------------------- | ------------------------------------------ |
| px   | 像素（最常用的绝对单位，中文偶数，英文奇数）        | 最常用的绝对单位                           |
| in   | 英寸                                                | 不常用                                     |
| cm   | 厘米                                                | 不常用                                     |
| em   | 最常用的相对单位，取父标签font-size的倍数           | 以当前标签的font-size为基准值取倍数        |
| rem  | 最近比较流行的相对单位，取html标签的font-size的倍数 | 移动端布局，不常用                         |
| %    | 以百分比形式取父标签font-size的倍数（不常用）       | 最常用的相对单位，取父元素对应长度的百分比 |

如果使用rem作为文字单位，就可以在用户改变当前浏览器字体时，更加智能的对字体大小进行控制，并且在桌面端和手机端表现良好。 

### 6.3 文字字体font-family

使用属性**font-family**来指定文字字体，属性取值一般是多个引号引起来的字体名称用逗号进行分隔，浏览器会从第一个字体开始尝试，如果不支持第一个字体则会自动向后查找。 

- 可以通过escape()来测试属于什么字体。
- 为了照顾不同电脑的字体安装问题，尽量只是用宋体和微软雅黑中文字体。

~~~html
font-family:"楷体","KaiTi","仿宋","FangSong";
~~~

**常见字体中英文名称对照表（了解即可，不用记）** 

| 中文名称   | 英文名称（推荐使用） | 文字示例                |
| ---------- | -------------------- | ----------------------- |
| 宋体       | SimSun               | 中文 English 123 ，。； |
| 黑体       | SimHei               | 中文 English 123 ，。； |
| 微软雅黑   | Microsoft YaHei      | 中文 English 123 ，。； |
| 微软正黑体 | Microsoft JhengHei   | 中文 English 123 ，。； |
| 楷体       | KaiTi                | 中文 English 123 ，。； |
| 仿宋       | FangSong             | 中文 English 123        |

### 6.4 文字粗细font-weight

| 属性值                         | 说明                                |
| ------------------------------ | ----------------------------------- |
| normal（常用）                 | 常规，默认值                        |
| bold（常用）                   | 加粗，常用                          |
| bolder                         | IE5+， 特粗体                       |
| lighter                        | IE5+，细体                          |
| number（100~900）(100的整数倍) | IE5+ ，数字400=normal;数字700=bold; |

> 1、在HTML中将对象直接加粗,可以用<b>或<strong>对其加粗。
>
> 2、使用CSS加粗对象可以使用font-weight:bold即可实现加粗。

###6.5 文字样式font-style

| 属性值  | 说明         |
| ------- | ------------ |
| normal  | 常规，默认值 |
| italic  | 斜体，常用   |
| oblique | 倾斜         |

## 7 段落属性

### 7.1 行间距(文本行高)line-height

line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。

line-height常用的属性单位有三种，分别是像素px、相对值em（字符倍数）、百分比%，实际工作中使用最多的是像素px。

一般情况下，行距比字号大7.8像素左右。

### 7.2 水平对齐方式text-align

用于设置文本内容的水平对齐方式，相当于html中的align对齐属性。**只有对块级元素（block）设定才会生效，并且可继承。**

text-align:排列值

属性值：left左对齐（默认）；   right右对齐 ；  center居中对齐（是让盒子里的内容水平居中，而不是让盒子居中对齐）；justify两端对齐，可以让大段的文本看起来比较整齐，不过两端对齐的表现可能会因浏览器的不同而有所不同。

> 块级元素水平居中：margin:0 auto;

### 7.3 垂直对齐方式vertical-align

设置文字的垂直对齐方式。语法：vertical-align:排列取值

| 排列取值    | 说明                           |
| ----------- | ------------------------------ |
| baseline    | 浏览器默认的垂直对齐方式       |
| sub         | 文字的下标                     |
| super       | 文字的上标                     |
| top         | 垂直靠上对齐                   |
| text-top    | 使元素和上级元素的字体向上对齐 |
| middle      | 垂直居中对齐                   |
| text-bottom | 使元素和上级元素的字体向下对齐 |

> line-height（行高）：子元素的行高与父元素的行高相等，垂直居中。

### 7.4 首行缩进text-indent

text-indent属性用于设置首行文本的缩进，浏览器默认不缩进，其属性值可为字符宽度的倍数em，也可为相对于浏览器窗口的百分比%，允许使用负值。建议使用em作为设置单位。

1em就是一个字的宽度，若是汉字的段落，1em就是一个汉字的宽度。

### 7.5 文本的修饰text-decoration

text-decoration通常用于给链接修改装饰效果。

| 值           | 描述                                                   |
| ------------ | ------------------------------------------------------ |
| none         | 默认。定义标准的文本                                   |
| underline    | 下划线，定义文本下的一条线，下划线也是我们链接自带的。 |
| overline     | 上划线，定义文本上的一条线                             |
| line-through | 中划线（删除线），定义穿过文本下的一条线               |
| blink        | 文字闪烁效果                                           |

### 7.6 文字阴影text-shaow（CSS3）

**text-shadow** 决定文字的阴影，部分浏览器不支持
**text-transform**:文字大小写转换。 none默认，capitalize单词以大写字母开头， uppercase全大写，lowercase全小写。
**white-space**:规定段落中的文本是否换行。normal默认处理方式（换行）；nowrap 强制在同一行内显示所有文本（不换行）

比较简单的文字阴影由四个属性值组成： 

~~~html
text-shadow:水平偏移（必写） 垂直偏移（必写） 模糊距离 阴影颜色
~~~

###7.7 单词间隔word-spacing 

指的是单词间的最小，最大和最佳间隙 或者说单词之间空格的大小。

语法：word-spacing:normal（正常的间隔）/in/长度值（可以是负值）+单位

### 7.8 字符间隔letter-spacing

指的是字符间的最小，最大和最佳间隙。

语法：letter-spacing:normal/inherit/initial

### 7.9 文本转换text-transform

文字大小写转换。语法：text-transform:转换值

 none默认原始值，capitalize单词以大写字母开头， uppercase全大写，lowercase全小写。

###7.10 



## 8 背景属性

###8.1 background-color（背景颜色）

指定背景颜色；属性值是CSS颜色

###8.2 background-size（背景大小）

更改背景图片大小；例如：background-size: 200px 210px; 

###8.3 background-image（背景图片）

指定背景图片；属性值是none（默认的无背景图片）/url （背景图片地址） 。提倡背景图片后面的地址，url不要加引号。 

> 若图片不重复的话，图片覆盖不到的地方会被背景颜色填充；若图片平铺，则会覆盖背景颜色。
>
> 属性允许指定一个图片展示在背景中（只有CSS3才可以多背景）可以和 background-color 连用。 

例如：url(/i/eg_bg_04.gif)        （url不要加引号）

###8.4 background-repeat（背景重复）

指定背景图片是否重复，以及哪个方向重复或者是否平铺

**属性值**：
repeat：背景图像在纵向和横向上平铺（默认的）
repeat-x：背景图片在横向上平铺
repeat-y：背景图片在纵向上平铺
no-repeat ：背景图像不平铺

> 设置背景图片是，默认把图片在水平和垂直方向平铺以铺满整个元素。

例如：background-image: url(/i/eg_bg_03.gif); background-repeat: repeat-y; 

###8.5 background-position（背景位置）

指定背景图片在背景中的位置 

**属性值**：

- position：center（背景图片居中对齐，用的最多）,left,right,top,bottom等方位值，通常对成对出现。
- length：百分比数值（%），由浮点数字和单位标识符组成的长度值（浮点数字px）。

> 1、设置或检索对象的背景图像位置，必须现指定background-image属性，默认值为：（0% 0%）。
>
> 2、若指定了一个值，则该值用于横坐标，纵坐标默认为50%；若有两个值，则第一个值用于横坐标，第二个值用于纵坐标。
>
> 3、position后面是横坐标和纵坐标，可以使用方位名词或者精确单位。
>
> 4、若精确单位和方位名词混合使用，则必须横坐标在前，纵坐标在后。（background-position:15px top;其中15px是横坐标，top是纵坐标。）

例如：background-image:url('/i/eg_bg_03.gif'); background-repeat:no-repeat; background-position:center; 

###8.6 background-attachment（背景附着） 

设置或检索背景图像是随对象内容滚动还是固定的

语法：background-attachment : scroll | fixed  

**属性值**：

- scroll：背景图像是随着对象内容滚动。
- fixed：背景图像固定

###8.7 背景透明（CSS3）

background：rgba(0,0,0,0.3);

最后一个参数是alpha透明度，取值范围0~1之间。

> 背景半透明是指盒子背景半透明，盒子里面的内容不受影响。

###8.8 背景简写

background属性的值的书写顺序官方没有强制标准。不过为了增加可读性，可以写成如下格式：

background:背景颜色 背景图片地址 背景平铺 背景滚动 背景位置

例如：background:transparent url(image.jpg) repeat-y scroll 50% 0; 

## 9 列表中的符号设置（重要）

list-style分解版：list-style-type项目符号类型；list-style-image项目符号图像；list-style-position项目符号位置。

可以指定列表中每一项的标志样式，既可以通过ul或者ol指定其中所有项的样式，又可以通过li单独制定每一项的样式。 

简写综合方式：list-style:square url()  inside 

**注意：list-style-type在使用时不考虑是ul还是ol** 

/*list-style-type: circle;*/
/*list-style-type: afar;*/
/*list-style-type: square;*/`

| list-style-position | 列表标记位置                                                 |
| ------------------- | ------------------------------------------------------------ |
| inside              | 列表项目标记放置在文本中，且环绕文本以标记为中心对齐。       |
| outside             | 默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不以标记为中心对齐。 |
| inherit             | 规定应该从父元素继承list-style-position属性的值。            |

| list-style-type      | 无序列表标记类型   | 有序列表标记类型                          |
| -------------------- | ------------------ | ----------------------------------------- |
| none                 | 无标记             |                                           |
| disc                 | 默认。标记是实心圆 |                                           |
| circle               | 标记是空心圆       |                                           |
| square               | 标记是实心方块     |                                           |
| decimal              |                    | 有序数字，ol默认，标记是数字（1，2，3……） |
| decimal-leading-zero |                    | 以0开头的数字标记（01，02，03……）         |
| lower-roman          |                    | 小写罗马数字（）                          |
| upper-roman          |                    | 大写罗马数字：Ⅰ，Ⅱ，Ⅲ，Ⅳ，Ⅴ，Ⅵ，Ⅶ，Ⅷ，Ⅸ   |
| lower-alpha          |                    | 有序小写英文字母                          |
| upper-alpha          |                    | 有序大写英文字母                          |

| 有序列表的其他属性（type） | 作用                                                         |
| -------------------------- | ------------------------------------------------------------ |
| start                      | 定义开始的序号（<ol type="3">，即从3开始标记3，4，5……）      |
| value                      | 在某一列重新开始定义列序号（<li value="4"></li>,不管前面的序号，从这一列开始以4开头定义） |

##10 导航栏案例

使用技巧：在一行内的盒子内，设定行高等于盒子的高度，就可以是文字垂直居中。

```html
<head>
        <meta charset="utf-8">
        <style> 
        body {
            background-color: #000;
        }
        a {
            width: 200px;
            height: 50px;
            /* background-color: orange; */
            display: inline-block;  /* 把a 行内元素转换为行内块元素 */
            text-align: center;  /* 文字水平居中 */
            line-height: 50px;  /* 我们设定行高等于盒子的高度，就可以使文字垂直居中 */
            color: #fff;
            font-size: 22px;
            text-decoration: none;  /* 取消下划线 文本装饰 */
        }
        a:hover {  /* 鼠标经过 给我们的链接添加背景图片*/
            background: url(images/h.png) no-repeat; 
        }
        </style>
    </head>
    <body>
    <a href="#">专区说明</a>
    <a href="#">申请资格</a>
    <a href="#">兑换奖励</a>
    <a href="#">下载游戏</a>
    </body>
```



##11 简易盒子类型

CSS就三个大模块： 盒子模型 、 浮动 、 定位，其余的都是细节。要求这三部分，无论如何也要学的非常精通。 

所谓盒子模型就是把HTML页面中的标签（元素）看作是一个矩形的盒子，也就是一个盛装内容的容器。每个矩形都由元素的内容、内边距（padding）、边框（border）和外边距（margin）组成。 

![Alt text](data:image/png;base64,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) 

### 11.1 盒子大小box-sizing

####手动指定宽度和高度的计算方式

| 属性值      | 说明                     |
| ----------- | ------------------------ |
| content-box | 宽高是内容区的宽高，默认 |
| border-box  | 宽高从边框开始计算，常用 |

指定最小宽度、最小高度、最大宽度、最大高度，常配合取相对值的宽度和高度使用。

#### content的width和height

用于指定宽度和高度，一般是操作内容区的宽度和高度，计算元素实际占用空间时需要考虑内边距和边框。width和height的属性值可以为不同单位的数值或相对于父元素的百分比%，实际工作中最常用的是像素值。 

大多数浏览器，如Firefox、IE6及以上版本都采用了W3C规范，符合CSS规范的盒子模型的总宽度和总高度的计算原则是： 

```html
 /*外盒尺寸计算（元素空间尺寸）*/
  Element空间高度 = content height + padding + border + margin
  Element空间宽度 = content width + padding + border + margin
  /*内盒尺寸计算（元素实际大小）*/
  Element Height = content height + padding + border （Height为内容高度）
  Element Width = content width + padding + border （Width为内容宽度）
```

**注意**：

*1、宽度属性width和高度属性height仅适用于块级元素，对行内元素无效（ img 标签和 input除外）。*

2、*计算盒子模型的总高度时，还应考虑上下两个盒子垂直外边距合并的情况*。*

3、*如果一个盒子没有给定宽度/高度或者继承父亲的宽度/高度，则padding 不会影响本盒子大*小

###11.2 边框border

border-width（宽度）:上边 [右边 下边 左边]; `
border-style（类型）:上边 [右边 下边 左边]; 
border-color（颜色）:上边 [右边 下边 左边]; 

综合写法：border: 宽度 类型 颜色`

border-top:（上边框）宽度 类型 颜色;` 
border-bottom:（下边框）宽度 类型 颜色;` 
border-left:（左边框）宽度 类型 颜色;` 
border-right:（右边框）宽度 类型 颜色;`

| 类型取值 | 说明                                     |
| -------- | ---------------------------------------- |
| none     | 没有边框，即忽略所有边框的宽度（默认值） |
| solid    | 单实线，最常用                           |
| dotted   | 点线，可能显示为实线                     |
| dashed   | 虚线，可能显示为实线                     |
| double   | 双实线，宽度表现不统一                   |

####表格的细线边框

以前学过的html表格边框很粗，这里只需要CSS一句话就可以美观起来。 让我们真的相信，CSS就是我们的白马王子（白雪公主）。

table{ border-collapse:collapse; } collapse 单词是合并的意思

border-collapse:collapse; 表示边框合并在一起。

####圆角边框(CSS3)

radius 半径（距离）

语法格式：                                

```
border-radius: 左上角  右上角  右下角  左下角;
```

border-radius（边框圆角）:指定四个角度圆角半径，取值超过短边的50%时相当于50%。

常见用法：

1. 制作圆角矩形，此时取值不要达到或超过短边的50%。
2. 制作圆形或椭圆形（用户头像常见），取值为短边的50%。

###11.3 内边距（内补白）padding

内容与边框之间的距离 

`padding-top:上边距`  `padding-bottom:下边距`  `padding-left:左边距`  `padding-right:右边距` 

简写方式如下：

`padding:四边边距` （一个值）
`padding:上下边距 左右边距`（两个值） 
`padding:上边距 左右边距 下边距` （三个值）
`padding:上边距 右边距 下边距 左边距`（四个值）（上右下左，从上边开始按顺时针旋转）

###11.4 外边距（外补白）margin

外边距：元素与元素之间的距离 。设置外边距会在元素之间创建“空白”， 这段空白通常不能放置其他内容。 

~~~html
margin-top:上边距 
margin-bottom:下边距 
margin-left:左边距 
margin-right:右边距

简写方式如下：
margin:四边边距 
margin:上下边距 左右边距 
margin:上边距 左右边距 下边距 
margin:上边距 右边距 下边距 左边距（上右下左，从上边开始按顺时针旋转）
~~~

注意：
1、盒子水平居中：margin: 0 auto 
	条件：必须是块级元素；盒子必须指定宽度（width）
	方法：给左右的外边距设置为auto

> margin：

2、父子关系中设置子元素margin时要慎重，可以使用padding。
给子元素设置margin-top,实际是给父元素设置了，解决方法：使用padding。
3、图片下方有空隙产生（父元素加边框出现的空隙）：img{vertical-align:middle;} vertical-align:top/bottom/middle 或img{display:block;}
4、各个浏览器下img有空隙 img{float:left;} 两个块元素，竖向的margin值不增加，会重叠，其间距为最大margin值 。
5、IE6横向margin加倍（产生因素：块属性、float、有横向margin ） 解决方法：display：inline；
6、制作网页时清除元素的默认内外边距，是为了更方便的控制网页中的元素：
*{
  padding:0;/*清除内边框*/
  margin:0;/*清除外边框*/
}

> 行内元素只有左右外边距，没有上下外边距。

> 上下内边距在ie6等低版本浏览器中会问题，尽量不用。

7、外边距合并：使用margin定义块元素的垂直外边距时，可能会出现外边距的合并。
8、嵌套块元素垂直外边距的合并：
	问题：对于两个嵌套关系的块元素，如果父元素没有上内边距及边框，则父元素的上外边距会与子元素的上外边距发生合并，合并后的外边距为两者中的较大者，即使父元素的上外边距为0，也会发生合并。![嵌套块元素垂直外边距的合并](E:图片\嵌套块元素垂直外边距的合并.png)
	
解决办法：为父元素定义1像素的上边框或上内边距；为父元素添加overflow:hidden。
9、相邻块元素垂直外边距的合并：
当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom，下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和，而是两者中的较大者。这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。

![相邻块元素垂直外边距的合并](E:图片\相邻块元素垂直外边距的合并.png)

解决办法：避免这种情况即可。

  ### 11.5 盒子模型布局稳定性

根据稳定性来分，建议优先使用宽度（width）其次使用内边距（padding） 再次外边距（margin）。 

理由：
1、margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。
2、padding 会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。
3、width 没有问题（嗨皮）我们经常使用宽度剩余法 、高度剩余法来做。

### 11.6 盒子阴影

语法：
	box-shadow:水平阴影 垂直阴影 模糊距离 阴影尺寸 阴影颜色  内/外阴影； 

| 值       | 描述                                     |
| -------- | ---------------------------------------- |
| h-shadow | 必写。水平阴影的位置，允许负值。         |
| v-shadow | 必写。垂直阴影的位置，允许负值           |
| blur     | 可选。模糊距离。                         |
| spread   | 可选。阴影的尺寸                         |
| color    | 可选。阴影的颜色。参阅CSS颜色值          |
| inset    | 可选。将外部阴影（outset）改为内部阴影。 |
1、前两个属性是必须写的。其余的可以省略。
2、外阴影 (outset) 但是不能写，默认；  想要内阴影 inset

```css
div {
            width: 200px;
            height: 200px;
            border: 10px solid red;
            /* box-shadow: 5px 5px 3px 4px rgba(0, 0, 0, .4);  */
            /* box-shadow:水平位置 垂直位置 模糊距离 阴影尺寸（影子大小） 阴影颜色  内/外阴影； */
            box-shadow: 0 15px 30px  rgba(0, 0, 0, .4);
}
```



### 11.7 文字与盒子居中时，图片和背景的区别
文字水平居中是 text-align: center
盒子水平居中是将左右margin改为auto
```css
text-align: center; /* 文字居中水平 */ 
margin: 10px auto; /* 盒子水平居中 左右margin 改为 auto 就阔以了 */ 
```
插入图片 我们用的最多 比如产品展示类
背景图片我们一般用于小图标背景 或者 超大背景图片
```css
section img {  
        width: 200px;/* 插入图片更改大小 width 和 height */
        height: 210px;
        margin-top: 30px;  /* 插入图片更改位置 可以用margin 或padding  盒模型 */
        margin-left: 50px; /* 插入当图片也是一个盒子 */
    }

aside {
        width: 400px;
        height: 400px;
        border: 1px solid purple;
        background: #fff url(images/sun.jpg) no-repeat;

        background-size: 200px 210px; /*  背景图片更改大小只能用 background-size */
        background-position: 30px 50px; /* 背景图片更该位置 我用 background-position */
    }
```

> 页面流（normal flow）

> 页面上的元素被解析后的一种渲染方式，类似于水流的方式。页面自上而下解析，遇到块级元素就让它占据一个新行，遇到行内元素就按照父元素的text-align属性按照一定的方向进行流动，如此循环进行页面渲染。
>
> 普通文档流：元素从上到下排列的顺序
>
> 脱离文档流：元素从正常的排列顺序被抽离（浮动，定位）
>
> CSS的3种定位机制：普通流（标准流）、浮动和定位。 

##12 浮动float

###12.1 浮动

将元素从正常排列顺序抽离出，排列在父元素的最左侧/最右侧（按照我们的意愿进行排列），若浮动元素超出当前行宽度，超出元素自动挤到下行。它允许周围其他文字和行内元素围绕自己进行布局。
浮动的目的就是为了让多个块级元素在同一行上显示。
在CSS中，通过float属性来定义浮动，其基本语法格式如下： 选择器{float:属性值;}

| 属性值 | 说明               |
| ------ | ------------------ |
| none   | 元素不浮动，默认值 |
| left   | 元素向左浮动       |
| right  | 元素向右浮动       |

- 当一个盒子浮动时（float不为none时），脱离页面流，漂浮在其他的标准流盒子上面，**将不再占据块级元素的空间**。

- 当一个**行内元素**浮动后，就**可以为其指定宽高**了。

- 浮动的盒子需要和标准流的父级搭配使用 ，元素添加浮动后，元素会具有行内块元素的特性。元素的大小完全取决于定义的大小或者默认的内容多少，浮动根据元素书写的位置来显示相应的浮动。 

- 浮动首先创建包含块的概念（包裹）。浮动的元素总是找离它最近的父级元素对齐。但是不会超出内边距（padding）的范围。

  ![浮动找最近的父类盒子对齐](E:图片\浮动找最近的父类盒子对齐.jpg)

- 浮动的元素排列位置，跟上一个元素（块级）有关系。如果上一个元素有浮动，则A元素顶部会和上一个元素的顶部对齐；如果上一个元素是标准流，则A元素的顶部会和上一个元素的底部对齐。   

![浮动的两个子盒子](E:图片\浮动的两个子盒子.jpg)



### 12.2 清除浮动

> 图文混排：给一个盒子里的图片作浮动，下方的图片会占领上方图片之前的位置，被覆盖
>
> 

清除浮动后造成的影响。本质上是为了解决父级元素因为子级元素浮动引起内部高度为0的问题。

浮动应用：页面布局中  多栏布局，两端对齐布局，导航栏。

![正常标准盒子](E:图片\正常标准盒子.jpg)

![子盒子浮动](E:图片\子盒子浮动.jpg)

方法一：父元素设置宽高（高是必须的）border padding  margin   #当高度不能固定的时候就不适用了
方法二：父元素触发BFC的方式，设置 overflow:hidden|auto|scroll

方法三：给需要清除浮动的元素设置clear:left/right/both，清除在该元素之上其他元素浮动造成的影响。

>代码简洁，但内容增多容易造成不会自动换行，导致内容被隐藏掉，无法显示需要溢出的元素。
方法三：属性clear——可以让一个元素主动向下移动来保持自己和其他浮动元素和自己不在同一行。
基本语法格式：选择器{clear:属性值;}
存在问题：给该元素设置margin时没有效果，使影响元素的margin失效 

| 属性值 | 说明                 |
| ------ | -------------------- |
| none   | 不清除浮动，默认值   |
| left   | 清除左边的浮动       |
| right  | 清除右边的浮动       |
| both   | 清除左右的浮动，常用 |
 方法四：使用after伪元素清除浮动-实际应用（综合最优的方法——万能法）

在需要清除自身里面的浮动对其他盒子影响的盒子里，设置:after；或者在需要清除上方盒子内的浮动对当前盒子的影响时，在当前盒子设置:before

:after 方式是空元素的升级版，好处是不用单独加标签

```css
.clearfix:after {  
    content: "."; 
    display: block; 
    height: 0; 
    clear: both; 
    visibility: hidden;  
}  

.clearfix {*zoom: 1;}   /* IE6、7 专有 */
```

> 注意： content:”.” 里面尽量跟一个小点，或者其他，尽量不要为空，否则再firefox 7.0前的版本会有生成空格。 
符合闭合浮动思想 结构语义化正确 ,但是由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。 
方法五：使用before和after双伪元素清除浮动

```css
.clearfix:before,.clearfix:after { 
  content:"";
  display:table;  /* 这句话可以触发BFC BFC可以清除浮动,BFC我们后面讲 */
}
.clearfix:after {
 clear:both;
}
.clearfix {
  *zoom:1;
}
```
代码更简洁 ,但是由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。 

## 13 定位position

指定元素的定位方式，默认为**static**，根据页面流进行定位。当一个元素定位不为**static**时，可以用（边偏移属性）**top**、**left**、**right**、**bottom**和**z-index**来操作元素的位置。 

语法格式：选择器{position:属性值;}

| 属性值   | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| static   | 静态定位：各个元素在HTML页面流中默认的位置。不可用边偏移     |
| relative | 相对定位-相对元素的原来位置进行偏移，结合方位进行位置确定，但元素在页面流中的位置依然保留 |
| absolute | 绝对定位-相对于具有定位的父元素位置进行偏移；元素模式（无论是块级元素还是行内元素）转换为行内块模式（若是行内元素）。 |
| fixed    | 固定定位-相对于浏览器窗口进行的固定位；元素模式（无论是块级元素还是行内元素）转换为行内块模式。 |

### 13.1 相对定位relative

position:relative——指定元素为相对定位，元素以在页面中原来占据的位置为原点，根据（top、left、right和bottom）的取值进行偏移，每次移动的位置，是以自己的左上角为基点移动（相对于自己来移动位置） 。但在偏移后，原位置任然占据空间。 相对定位的盒子仍在标准流中，它后面的盒子仍以标准流方式对待它。（相对定位不脱标） 。多用于子绝互相，单独应用很少。

### 13.2 绝对定位absolute

position:absolute——指定元素为绝对定位，元素不再占据任何页面空间（完全脱标）。此时会根据其最近的第一个**不是static定位**（绝对、相对、固定定位）的父元素结合（top、left、right和bottom）进行定位。**若找不到这种父元素，则根据整个页面进行定位**。 

**绝对定位的盒子水平/垂直居中：**
普通的盒子是左右margin 改为 auto就可， 但是对于绝对定位就无效了

定位的盒子也可以水平或者垂直居中，有一个算法。
	1、首先left50%父盒子的一半大小
	2、然后走自己外边距负的一半值就可以了 margin-left。

### 13.3 子绝父相（外相对，内绝对）

子绝父相：因为子级是绝对定位，不会占有位置， 可以放到父盒子里面的任何一个地方。父盒子布局时，需要占有位置，因此父亲只能是相对定位。
一种在处理某些定位问题时较为常见的书写方式。当我们想让一个子元素相对于其某个父元素位置确定，我们就可以设置这个父元素为相对定位，并把这个子元素设置后绝对定位后结合（top、left、right和bottom）进行处理。
定位位置，不受父元素padding的影响。
可配合使用z-index来设置元素的层叠顺序。
属性值为：整数。默认值是0。z-index值越大越靠上。

### 13.4 固定定位fixed（常用于打广告） 

position:fixed——指定元素为固定定位，元素将脱离页面流的控制，不再占据任何页面空间（完全脱标）。元素会相对于整个视口（用户可以看到的页面部分，即可视窗口）进行定位，当页面滚动时，该元素保持固定不动。

### 13.5 叠放次序（z-index）

当对多个元素同时设置定位时，定位元素之间有可能会发生重叠。 在CSS中，要想调整重叠定位元素的堆叠顺序，可以对定位元素应用z-index层叠等级属性，其取值可为正整数、负整数和0。 例如：z-index:2;

**注意**： 

1. z-index的默认属性值是0，取值越大，定位元素在层叠元素中越居上。
2. 如果取值相同，则根据书写顺序，后来居上。
3. 后面数字一定不能加单位。
4. 只有相对定位，绝对定位，固定定位有此属性，其余标准流，浮动，静态定位都无此属性，亦不可指定此属性。

###13.6 定位模式转换

跟浮动一样，元素添加了绝对定位和固定定位之后，元素模式也会发生转换，都转换为行内块模式， 比如**行内元素**如果添加了绝对定位或者固定定位后浮动后，可以不用转换模式，直接给高度和宽度。

### 13.7 四种定位总结

| 定位模式         | 是否脱标占有位置     | 是否可以使用边偏移 | 移动位置基准                     |
| ---------------- | -------------------- | ------------------ | -------------------------------- |
| 静态static       | 不脱标，正常模式     | 不可以             | 正常模式                         |
| 相对定位relative | 不脱标，占有位置     | 可以               | 相对自身位置移动（自恋型）       |
| 绝对定位absolute | 完全脱标，不占有位置 | 可以               | 相对于定位父级移动位置（拼爹型） |
| 固定定位fixed    | 完全脱标，不占有位置 | 可以               | 相对于浏览器移动位置（认死理型） |

## 14 元素的显示与隐藏

在CSS中有三个显示和隐藏的单词比较常见，我们要区分开，他们分别是 display ，visibility 和 overflow。 
他们的主要目的是让一个元素在页面中消失，但是不在文档源码中删除。 最常见的是网站广告，当我们点击类似关闭不见了，但是我们重新刷新页面，它们又会出现和你玩躲猫猫！！ 

###14.1 display 显示

作用：display属性用于设置或检索元素是否显示和显示方式。
特点：隐藏之后，不再保留位置。

| 属性值               | 说明                                   |
| -------------------- | -------------------------------------- |
| display:block        | 对象转换为块级元素，也有显示元素的意思 |
| display:inline       | 行内元素                               |
| display:none         | 隐藏显示                               |
| display:inline-block | 行内块元素，可以被指定宽高的类行内元素 |

### 14.2 visibility 可见性
作用：用于设置或检索是否显示对象
特点：隐藏之后，继续保留原有位置。

visibility:visible 对象可视

visibility:hidden 对象隐藏

**元素不显示的两种形式：visibility:hidden占空间；display:none不占空间。**

###14.3 overflow 溢出
作用：检索或设置当对象的内容超过其指定高度及宽度时如何管理内容。

visible : 不剪切内容也不添加滚动条。
auto :  超出自动显示滚动条，不超出不显示滚动条
hidden : 不显示超过对象尺寸的内容，超出的部分隐藏掉
scroll : 不管超出内容否，总是显示滚动条

- 行内元素与块级元素的比较

|          | 块级元素                                 | 行内元素                     |
| -------- | ---------------------------------------- | ---------------------------- |
| 占据空间 | 总是占据一个新行                         | 可以和其他行内元素占同一行   |
| 内部内容 | 可以有文字和其他任意元素                 | 只能有其他行内元素和文字     |
| 边距     | 可以自由指定外边距和内边距（行内块也是） | 竖直方向上的内外边距不起作用 |

 ### 14.4 元素可以被指定宽高的情况
当元素满足以下任一条件时，可以被手动指定宽高。 

1. 是块级元素。
2. 是img或input。
3. 是行内块元素。
4. 是float不为none的元素。
5. 是定位方式不为static或relative的元素。

###14.5 background详解与CSS精灵

- **background详解**

  1.仅仅指定背景色： 
  ​    background:CSS颜色; 相当于 background-color:CSS颜色; 
  2.仅仅指定背景图片： 
  ​    background:url(图片路径); 相当于 background-image:url(图片路径); 
  ​    background:url(图片路径) no-repeat; 相当于 background-image:url(图片路径) no-repeat; 
  ​    （no-repeat用于让背景图片不重复） 
  3.同时指定背景色和背景图片： 
  ​    background:CSS颜色 url(图片路径); 
  4.指定背景图片的位置： 
  ​    background:url(图片路径) no-repeat 水平偏移 垂直偏移

- **雪碧图和CSS精灵**

  像下面这样，由许多小图拼接成的一大张图像就可以叫做一个雪碧图。因为其需要配合CSS精灵使用，所以有时候也被叫做精灵图。 
  CSS精灵（CSS Sprite）是一种使用CSS属性background来从雪碧图上取图片的技术。

  - **使用CSS精灵的好处**

  我们知道，当我们访问一个网页时会向服务器发送一次请求。如果这个网页中，引入了其他文件（比如CSS、图片），那么同样需要向服务器发送请求。

  服务器接收到请求后，会根据请求的地址去寻找对应文件，并将它发送给客户端，这是一个比较耗时耗力的操作。

  如果使用CSS精灵，那我们从同一张雪碧图上取多次图片只需要向服务器发送一次请求。

  因此，合理使用CSS精灵技术，能够减少请求次数，从而

  > **1. 减轻服务器压力** 
  > **2. 减少用户的等待时间** **3. 图片不易丢失** **4.后期维护简单**

  ![Alt text](data:image/png;base64,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) 

## 15 CSS高级技巧

### 15.1 CSS用户界面样式

所谓的界面样式， 就是更改一些用户操作样式， 比如 更改用户的鼠标样式， 表单轮廓等。但是比如滚动条的样式改动受到了很多浏览器的抵制，因此我们就放弃了 ，防止表单域拖拽 。

####鼠标样式cursor

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。 

| 属性值(可使用鼠标指向测试) | 说明                                    |
| -------------------------- | --------------------------------------- |
| auto                       | 自动根据当前位置判断，默认值            |
| default                    | 系统默认光标，通常是箭头                |
| pointer                    | 系统指示光标，通常是手形                |
| text                       | 系统文本光标，通常类似于细高的大写字母I |
| wait                       | 系统等待光标，通常是转动的彩色圆圈      |
| help                       | 系统帮助光标，通常是箭头加一个问号      |

#### vertical-align 垂直对齐
让带有宽度的块级元素居中对齐，是margin: 0 auto;
让文字居中对齐，是 text-align: center;
vertical-align 垂直对齐， 这个看上去很美好的一个属性， 实际有着不可捉摸的脾气。
```
vertical-align:baseline(默认)||top||middle||bottom
```
vertical-align 不影响块级元素中的内容对齐，它只针对于行内元素或者行内块元素，特别是行内块元素， **通常用来控制图片、表单与文字的对齐。** 默认的图片会和文字基线对齐。 

#### 去除图片底侧空白缝隙
 图片或者表单等行内块元素，他的底线会和父级盒子的基线对齐。这样会造成一个问题，就是图片底侧会有一个空白缝隙。 
解决的方法就是：
1、给img 添加vertical-align:middle | top等。 让图片不要和基线对齐。
2、给img 添加display：block; 转换为块级元素就不会存在问题了。 

#### 轮廓 outline

是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。 

```css
outline:outline-color||outline-style||outline-width
```

但是我们都不关心可以设置多少，我们平时都是去掉的。

最直接的写法是 ： outline: 0; 或者 outline: none;

```html
<input type="text" style="outline:0;"/>
```

### 15.2 溢出的文字隐藏

#### word-break：自动换行

normal：使用浏览器默认的换行规则。
break-all：允许在单词内换行。
keep-all：只能在半角空格或连字符处换行。
主要处理英文单词

####white-space

white-space设置或检索对象内文本显示方式。通常我们使用于强制一行显示内容
normal：默认处理方式 
nowrap：强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行。
可以处理中文

#### text-overflow：文字溢出

ext-overflow : clip | ellipsis

设置或检索是否使用一个省略标记（…）标示对象内文本的溢出

clip：不显示省略标记（…），而是简单的裁切

ellipsis：当对象内文本溢出时显示省略标记（…）

注意一定要首先强制一行内显示，再次和overflow属性 搭配使用

### 15.3 核心技术

核心技术就是利用CSS精灵（主要是背景位置）和盒子padding撑开宽度, 以便能适应不同字数的导航栏。
一般的经典布局都是这样的：
```
<li>
  <a href="#">
    <span>导航栏内容</span>
  </a>
</li>
```
总结：
1. a 设置 背景左侧，padding撑开合适宽度。
2. span 设置背景右侧， padding撑开合适宽度 剩下由文字继续撑开宽度。
3. 之所以a包含span就是因为 整个导航都是可以点击的。

##16 其他补充

###16.1 BFC(块级格式化上下文)

BFC(Block formatting context)

直译为”块级格式化上下文”。

**那些元素会具有BFC的条件**

不是所有的元素模式都能产生BFC，w3c 规范：
display 属性为 block, list-item, table 的元素，会产生BFC.
大家有么有发现这个三个都是用来布局最为合理的元素，因为他们就是用来可视化布局。
注意其他的display属性，比如 line 等等，他们创建的是 IFC ，我们暂且不研究。

**什么情况下可以让元素产生BFC**

## 

