# 前端面试知识点整理
##HTML
1.viewport meta
```javascript
    <meta name ="viewport" content ="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no"> 
    width  　　　　 viewport 宽度(数值/device-width)   
    height         viewport 高度(数值/device-height)   
    initial-scale  初始缩放比例   
    maximum-scale  最大缩放比例   
    minimum-scale  最小缩放比例   
    user-scalable  是否允许用户缩放(yes/no)  
```
2.语义

>web语义化是指通过HTML标记表示页面包含的信息，包含了HTML标签的语义化和css命名的语义化。 
HTML标签的语义化是指：通过使用包含语义的标签（如h1-h6）恰当地表示文档结构 
css命名的语义化是指：为html标签添加有意义的class，id补充未表达的语义，如Microformat通过添加符合规则的class描述信息 为什么需要语义化：

- 去掉样式后页面呈现清晰的结构
- 盲人使用读屏器更好地阅读
- 搜索引擎更好地理解页面，有利于收录
- 便团队项目的可持续运作及维护

HTML5新增语义化标签：header、footer、nav、article、aside、section等。

##CSS

1.排版
 
- position
 
```
    static 默认
    relative 相对定位
    absolute 绝对定位 飘出文档流
    如果一个元素绝对定位后，其参照物是以离自身最近元素是否设置了相对定位，如果有设置将以离自己最近元素定位，如果没有将往其祖先元素寻找相对定位元素，     一直找到html为止。
    fixed 固定 属于绝对定位
    inherit 规定应该从父元素继承 position 属性的值
```

- display

```
    inline 默认。此元素会被显示为内联元素，元素前后没有换行符。
    block 此元素将显示为块级元素，此元素前后会带有换行符。
    inline-block 行内块元素。
    flex（早期版本叫box） 将对象作为弹性伸缩盒显示。（http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html）
```

- float、clear
 
 ```
    HTML页面的标准文档流(默认布局)是：从上到下，从左到右，遇块(块级元素)换行。
    浮动层：给元素的float属性赋值后，就是脱离文档流，进行左右浮动，紧贴着父元素(默认为body文本区域)的左右边框。
    而此浮动元素在文档流空出的位置，由后续的(非浮动)元素填充上去：块级元素直接填充上去，若跟浮动元素的范围发生重叠，浮动元素覆盖块级元素。
    内联元素：有空隙就插入。
    
    <div style="clear:both"></div>
    .clearfix:after {
        content: ".";
        display: block;
        height: 0;
        clear: both;
        visibility: hidden;
    }
 ```
 
- 盒子模型
 
 
```
    内容(content)、填充(padding)、边框(border)、边界(margin)
    内容（content（with/height））、内边距（padding）、边框（border）、外边距（margin）
    box-sizing
        box-sizing属性可以为三个值之一：content-box（default），border-box，padding-box。
        content-box，border和padding不计算入width之内
        padding-box，padding计算入width内
        border-box，border和padding计算入width之内，其实就是怪异模式了~
```
 
- 行
 
```
    line-height（http://www.studyofnet.com/news/273.html）:
        “行高“指一行文字的高度，具体来说是指两行文字间基线间的距离。在CSS，line-height被用来控制行与行之间的垂直距离。line-height 属性会影响行框	  的布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。
        从上到下四条线分别是顶线、中线、基线、底线，很像才学英语字母时的四线三格，我们知道vertical-align属性中有top、middle、baseline、bottom，	      就是和这四条线相关。
        行高是指上下文本行的基线间的垂直距离，即图中两条红线间垂直距离。
        行距是指一行底线到下一行顶线的垂直距离，即第一行粉线和第二行绿线间的垂直距离。
        半行距是行距的一半，即区域3垂直距离/2，区域1，2，3，4的距离之和为行高，而区域1，2，4距离之和为字体size，所以半行距也可以这么算：（行高-字	    体size）/2
    vertical-align（http://www.zhangxinxu.com/wordpress/2010/05/%E6%88%91%E5%AF%B9css-vertical-align%E7%9A%84%E4%B8%80%E4%BA%9B%E7%90%86%E8%A7%A3%E4%B8%8E%E8%AE%A4%E8%AF%86%EF%BC%88%E4%B8%80%EF%BC%89/）
        定义和用法
        vertical-align 属性设置元素的垂直对齐方式。
        说明
        该属性定义行内元素的基线相对于该元素所在行的基线的垂直对齐。允许指定负长度值和百分比值。这会使元素降低而不是升高。在表单元格中，这个属性会设         置单元格框中的单元格内容的对齐方式。
        值	描述
        长度	通过距离升高（正值）或降低（负值）元素。'0cm'等同于'baseline'
        百分值 – %	通过距离（相对于1line-height1值的百分大小）升高（正值）或降低（负值）元素。'0%'等同于'baseline'
        baseline	默认。元素的基线与父元素的基线对齐。
        sub	降低元素的基线到父元素合适的下标位置。
        super	升高元素的基线到父元素合适的上标位置。
        top	把对齐的子元素的顶端与line box顶端对齐。
        text-top	把元素的顶端与父元素内容区域的顶端对齐。
        middle	元素的中垂点与 父元素的基线加1/2父元素中字母x的高度 对齐。
        bottom	把对齐的子元素的底端与line box底端对齐。
        text-bottom	把元素的底端与父元素内容区域的底端对齐。
        inherit	采用父元素相关属性的相同的指定值。
```
 
- 文本
 
```
    whitespace
        定义和用法
        white-space 属性设置如何处理元素内的空白。
        值	描述
        normal	默认。空白会被浏览器忽略。
        pre	空白会被浏览器保留。其行为方式类似 HTML 中的 <pre> 标签。
        nowrap	文本不会换行，文本会在在同一行上继续，直到遇到 <br> 标签为止。
        pre-wrap	保留空白符序列，但是正常地进行换行。
        pre-line	合并空白符序列，但是保留换行符。
        inherit	规定应该从父元素继承 white-space 属性的值。
    wordbreak
        定义和用法
        word-break 属性规定自动换行的处理方法。
        值	描述
        normal	使用浏览器默认的换行规则。
        break-all	允许在单词内换行。
        keep-all	只能在半角空格或连字符处换行。
    word-wrap    
        定义和用法
        word-wrap 属性允许长单词或 URL 地址换行到下一行。
        值	描述
        normal	只在允许的断字点换行（浏览器保持默认处理）。
        break-word	在长单词或 URL 地址内部进行换行。
    区别
        word-wrap:break-word与word-break:break-all共同点是都能把长单词强行断句，不同点是word-wrap:break-word会首先起一个新行来放置长单词，新的         行还是放不下这个长单词则会对长单词进行强制断句；而word-break:break-all则不会把长单词放在一个新行里，当这一行放不下的时候就直接强制断句了。
```
 
2.绘制

- background
 
```
    值	描述	
    background-color	规定要使用的背景颜色。	
    background-position	规定背景图像的位置。	
    background-size	规定背景图片的尺寸。	
    background-repeat	规定如何重复背景图像。	
    background-origin	规定背景图片的定位区域。	
    background-clip	规定背景的绘制区域。	
    background-attachment	规定背景图像是否固定或者随着页面的其余部分滚动。	
    background-image	规定要使用的背景图像。	
    inherit	规定应该从父元素继承 background 属性的设置。
    如何定位背景图像：
    body
    { 
        background-image:url('bgimage.gif');
        background-repeat:no-repeat;
        background-attachment:fixed;
        background-position:center;
    }
    CSS3 新属性（http://www.daqianduan.com/3302.html）
        Background Size属性用来重设你的背景图片。有几个属性值：
            (1)background-size: contain;
            缩小背景图片使其适应标签元素（主要是像素方面的比率）
            (2)background-size: cover;
            让背景图片放大延伸到整个标签元素大小（主要是像素方面的比率）
            (3)background-size: 100px 100px;
            标明背景图片缩放的尺寸大小
            (4)background-size: 50% 100%;
            百分比是根据内容标签元素大小，来缩放图片的尺寸大小
```

- transform（转换）
 
```
    定义和用法
    transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。
    语法
    transform: none|transform-functions;
    值	描述	
    none	定义不进行转换。	
    matrix(n,n,n,n,n,n)	定义 2D 转换，使用六个值的矩阵。	
    matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)	定义 3D 转换，使用 16 个值的 4x4 矩阵。	
    translate(x,y)	定义 2D 转换。	
    translate3d(x,y,z)	定义 3D 转换。	
    translateX(x)	定义转换，只是用 X 轴的值。	
    translateY(y)	定义转换，只是用 Y 轴的值。	
    translateZ(z)	定义 3D 转换，只是用 Z 轴的值。	
    scale(x,y)	定义 2D 缩放转换。	
    scale3d(x,y,z)	定义 3D 缩放转换。	
    scaleX(x)	通过设置 X 轴的值来定义缩放转换。	
    scaleY(y)	通过设置 Y 轴的值来定义缩放转换。	
    scaleZ(z)	通过设置 Z 轴的值来定义 3D 缩放转换。	
    rotate(angle)	定义 2D 旋转，在参数中规定角度。	
    rotate3d(x,y,z,angle)	定义 3D 旋转。	
    rotateX(angle)	定义沿着 X 轴的 3D 旋转。	
    rotateY(angle)	定义沿着 Y 轴的 3D 旋转。	
    rotateZ(angle)	定义沿着 Z 轴的 3D 旋转。	
    skew(x-angle,y-angle)	定义沿着 X 和 Y 轴的 2D 倾斜转换。	
    skewX(angle)	定义沿着 X 轴的 2D 倾斜转换。	
    skewY(angle)	定义沿着 Y 轴的 2D 倾斜转换。	
    perspective(n)	为 3D 转换元素定义透视视图。
    例子
        div
        {
        transform:rotate(7deg);
        -ms-transform:rotate(7deg); 	/* IE 9 */
        -moz-transform:rotate(7deg); 	/* Firefox */
        -webkit-transform:rotate(7deg); /* Safari 和 Chrome */
        -o-transform:rotate(7deg); 	/* Opera */
        }
```

3.动画
 
- transition（过渡）
 
```
    语法
    transition: property duration timing-function delay;
    值	描述
    transition-property	规定设置过渡效果的 CSS 属性的名称。
    transition-duration	规定完成过渡效果需要多少秒或毫秒。
    transition-timing-function	规定速度效果的速度曲线。
        语法
        transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|cubic-
        bezier(n,n,n,n);
        值	描述
        linear	规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。
        ease	规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。
        ease-in	规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。
        ease-out	规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。
        ease-in-out	规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。
        cubic-bezier(n,n,n,n)	在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。
    transition-delay	定义过渡效果何时开始。
    例子
        <style> 
        div
        {
        width:100px;
        height:100px;
        background:blue;
        transition:width 2s;
        -moz-transition:width 2s; /* Firefox 4 */
        -webkit-transition:width 2s; /* Safari and Chrome */
        -o-transition:width 2s; /* Opera */
        }

        div:hover
        {
        width:300px;
        }
        </style>
```
 
 - animation(动画)
 
 ```
    语法
    animation: name duration timing-function delay iteration-count direction;
    值	描述
    animation-name	规定需要绑定到选择器的 keyframe 名称。。
    animation-duration	规定完成动画所花费的时间，以秒或毫秒计。
    animation-timing-function	规定动画的速度曲线。
    animation-delay	规定在动画开始之前的延迟。
    animation-iteration-count	规定动画应该播放的次数。
    animation-direction	规定是否应该轮流反向播放动画。
    例子
        <style> 
        div
        {
        width:100px;
        height:100px;
        background:red;
        position:relative;
        animation:mymove 5s infinite;
        -webkit-animation:mymove 5s infinite; /*Safari and Chrome*/
        }

        @keyframes mymove
        {
        from {left:0px;}
        to {left:200px;}
        }

        @-webkit-keyframes mymove /*Safari and Chrome*/
        {
        from {left:0px;}
        to {left:200px;}
        }
        </style>
 ```
4.理解和还原设计图意

- 垂直居中（http://blog.csdn.net/freshlover/article/details/11579669）

```
	(1)绝对居中
		.Center-Container {  
		  position: relative;  
		}  
		.Absolute-Center {  
		  width: 50%;  
		  height: 50%;  
		  overflow: auto;  
		  margin: auto;  
		  position: absolute;  
		  top: 0; left: 0; bottom: 0; right: 0;  
		}  
	(2)负外边距(Negative Margins)
		.is-Negative {  
			width: 300px;  
			height: 200px;  
			padding: 20px;  
			position: absolute;  
			top: 50%; left: 50%;  
			margin-left: -170px; /* (width + padding)/2 */  
			margin-top: -120px; /* (height + padding)/2 */  
		}  
	(3)变形（Transforms）
		.is-Transformed {   
		  width: 50%;  
		  margin: auto;  
		  position: absolute;  
		  top: 50%; left: 50%;  
		  -webkit-transform: translate(-50%,-50%);  
			  -ms-transform: translate(-50%,-50%);  
				  transform: translate(-50%,-50%);  
		}  
	(4)表格单元格（Table-Cell）
		<div class="Center-Container is-Table">  
		  <div class="Table-Cell">  
			<div class="Center-Block">  
			<!-- CONTENT -->  
			</div>  
		  </div>  
		</div>  
		.Center-Container.is-Table { display: table; }  
		.is-Table .Table-Cell {  
		  display: table-cell;  
		  vertical-align: middle;  
		}  
		.is-Table .Center-Block {  
		  width: 50%;  
		  margin: 0 auto;  
		} 
	(5)flex
		body {
		   /* Remember to use the other versions for IE 10 and older browsers! */
		   display: flex;
		   justify-content: center;
		   align-items: center;
		}
```

- 水平居中


```
	(1)如果需要居中的元素为常规流中inline元素，为父元素设置text-align: center;即可实现
	(2)如果需要居中的元素为常规流中block元素，
		1）为元素设置宽度，
		2）设置左右margin为auto,
		3）IE6下需在父元素上设置text-align: center;
		4) 再给子元素	恢复需要的值
	(3)如果需要居中的元素为浮动元素，
		1）为元素设置宽度，
		2）position: relative，
		3）浮动方向偏移量（left或者right）设置为50%，
		4）浮动方向上的margin设置为元素宽度一半乘以-1
	(4)如果需要居中的元素为绝对定位元素，
		1）为元素设置宽度，
		2）偏移量设置为50%，
		3）偏移方向外边距设置为元素宽度一半乘以-1
	(5)如果需要居中的元素为绝对定位元素，
		1）为元素设置宽度，
		2）设置左右偏移量都为0,
		3）设置左右外边距都为auto
```

- 多列等高

```
	(1)大的margin-bottom。这种技术的关键是给每个框设置大的底内边距，然后用数值相似的负外边距消除这个高度。这会导致每个列溢出容器元素。如果把容器的overflow属性设置	 为hidden,列就在最高点被裁切。		
	(2)背景图片、背景色实现假等高
	(3)css3 column-count
```

- 自适应宽

```
	(1)百分比
   （2）@media screen 
   （3）flex
   （4）<meta name=”viewport” content=”width=device-width, initial-scale=1″ />
   （5）相对大小的字体em
```

5.其它

- 继承性,特殊性,层叠性和重要性

```
    (1)继承性
        继承是一种规则，它允许样式不仅应用于某个特定 html 标签元素，而且应用于其后代。
        具有继承属性的标签：
            关于文字排版的属性如：
                font
                word-break
                letter-spacing
                text-align
                text-rendering
                word-spacing
                white-space
                text-indent
                text-transform
                text-shadow
                line-height
            color
            visibility
            cursor
    (2)特殊性
        选择器的优先权：
            1.  内联样式表的权值最高 1000；
            2.  ID 选择器的权值为 100
            3.  Class 类选择器的权值为 10
            4.  HTML 标签选择器的权值为 1
    (3)层叠性
        层叠就是在html文件中对于同一个元素可以有多个css样式存在，当有相同权重的样式存在时，会根据这些css样式的前后顺序来决定，处于最后面的css样式会         被应用。
    (4)重要性
        CSS 优先级法则：
            A  选择器都有一个权值，权值越大越优先；
            B  当权值相等时，后出现的样式表设置要优于先出现的样式表设置；
            C  创作者的规则高于浏览者：即网页编写者设置的CSS样式的优先权高于浏览器所设置的样式；
            D  继承的CSS 样式不如后来指定的CSS 样式；
            E  在同一组属性设置中标有“!important”规则的优先级最大； 
```

- BFC

```
    BFC 定义
　　    BFC布局规则：BFC(Block formatting context)直译为"块级格式化上下文"。
		它是一个独立的渲染区域，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。
    BFC布局规则：
        内部的Box会在垂直方向，一个接一个地放置。
        Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠
        每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
        BFC的区域不会与float box重叠。
        BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。
        计算BFC的高度时，浮动元素也参与计算
    哪些元素会生成BFC?
        根元素
        float属性不为none
        position为absolute或fixed
        display为inline-block, table-cell, table-caption, flex, inline-flex
        overflow不为visible
    作用
        可以包含浮动元素
        不被浮动元素覆盖
        阻止父子元素的margin折叠
```

##JS

1.基本概念

- 标识符：首字母字母、下划线、美元符号，其它多一个数字

- 基本数据类型：Undefined、Null、String、Number、Boolean

- typeof操作符（检测基本类型）

```
	"undefined" - 这个值未定义
	"boolean" - 这个值是布尔值
	"string" - 这个值是字符串	
	"number" - 这个值是数值
	"object" - 这个值是对象或null
	"function" - 这个值是函数	
```

- hasOwnProperty（给定的属性在当前对象实例中是否存在）

```
	for (i in parent){
		if(parent.hasOwnProperty(i)){
			child[i] = parent[i];
		}
	}
```

- instanceof(检测是不是某种类型对象)

```
	person instanceof Object //person是Object的吗？
```

2.函数

- 闭包

```
	我的理解：无论通过何种手段将内部函数传递到所在的词法作用域以外，它都会持有对原始定义作用域的引
	用，无论在何处执行这个函数都会使用闭包。
	一、什么是闭包
	简而言之，就是能够读取其他函数内部变量的函数。
	由于JS变量作用域的特性，外部不能访问内部变量，内部可以外部变量。
	二、使用场景
	1. 实现私有成员。
	2. 保护命名空间，避免污染全局变量。
	3. 缓存变量。
	三、注意事项
	1. 内存泄漏
	由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题。
	2. 变量命名
	如果内部函数的变量和外部函数的变量名相同时，那么内部函数再也无法指向外部函数那个同名的变量。
	
	下面我们来看一段代码，清晰地展示了闭包：
	function foo() {
	var a = 2;
	function bar() {
	console.log( a );
	}
	return bar;
	}
	var baz = foo();
	baz(); // 2 ———— 朋友，这就是闭包的效果。
	函数bar()的词法作用域能够访问foo()的内部作用域。然后我们将bar()函数本身当作一个值类型
	进行传递。在这个例子中，我们将bar所引用的函数对象本身当作返回值。
	在foo()执行后，其返回值（也就是内部的bar()函数）赋值给变量baz并调用baz()，实际上只是通过
	不同的标识符引用调用了内部的函数bar()。
	bar()显然可以被正常执行。但是在这个例子中，它在自己定义的词法作用域以外的地方执行。
	在foo()执行后，通常会期待foo()的整个内部作用域都被销毁，因为我们知道引擎有垃圾回收器用
	来释放不再使用的内存空间。由于看上去foo()的内容不会再被使用，所以很自然地会考虑对其进
	行回收。
	而闭包的“神奇”之处正是可以阻止这件事情的发生。事实上内部作用域依然存在，因此没有被回
	收。谁在使用这个内部作用域？原来是bar()本身在使用。
	拜bar()所声明的位置所赐，它拥有涵盖foo()内部作用域的闭包，使得该作用域能够一直存活，以
	供bar()在之后任何时间进行引用。
	bar()依然持有对该作用域的引用，而这个引用就叫作闭包。
	因此，在几微秒之后变量baz被实际调用（调用内部函数bar），不出意料它可以访问定义时的词法
	作用域，因此它也可以如预期般访问变量a。
	这个函数在定义时的词法作用域以外的地方被调用。闭包使得函数可以继续访问定义时的词法作
	用域。
	当然，无论使用何种方式对函数类型的值进行传递，当函数在别处被调用时都可以观察到闭包。

```

- 作用域（http://www.cnblogs.com/lhb25/archive/2011/09/06/javascript-scope-chain.html）

```
	1. 全局作用域（Global Scope）
		（1）最外层函数和在最外层函数外面定义的变量拥有全局作用域
		（2）所有末定义直接赋值的变量自动声明为拥有全局作用域
		（3）所有window对象的属性拥有全局作用域
	2. 局部作用域（Local Scope）
		(1)和全局作用域相反，局部作用域一般只在固定的代码片段内可访问到，最常见的例如函数内部，所有在一些地方也会看到有人把这种作用域称为函数作用域
	3. 作用域链（Scope Chain）
		(1)改变作用域链
			eval:避免使用			
			with:避免使用	
			catch:当try代码块中发生错误时，执行过程会跳转到catch语句，然后把异常对象推入一个可变对象并置于作用域的头部。在catch代码块内部，函数的			所有局部变量将会被放在第二个作用域链对象中。
	4. 查找、声明
		无所在哪声明，都等同于在函数顶部声明
		自下而上，沿作用链向上查找	

```

- this

```
	1.在一般函数方法中使用 this 指代全局对象
	2.作为对象方法调用，this 指代上级对象
	3.作为构造函数调用，this 指代new 出的对象
	4.apply 调用 ，apply方法作用是改变函数的调用对象，此方法的第一个参数为改变后调用这个函数的对象，this指代第一个参数
```

- call/apply

```
	call 和 apply 都是为了改变某个函数运行时的 context 即上下文而存在的，换句话说，就是为了改变函数体内部 this 的指向。因为 JavaScript 的函		     数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念。

	二者的作用完全一样，只是接受参数的方式不太一样。例如，有一个函数 func1 定义如下：
	var func1 = function(arg1, arg2) {};
	就可以通过 func1.call(this, arg1, arg2); 或者 func1.apply(this, [arg1, arg2]); 来调用。其中 this 是你想指定的上下文，他可以任何一个 	      JavaScript 对象(JavaScript 中一切皆对象)，call 需要把参数按顺序传递进去，而 apply 则是把参数放在数组里。

	JavaScript 中，某个函数的参数数量是不固定的，因此要说适用条件的话，当你的参数是明确知道数量时，用 call，而不确定的时候，用 apply，然后把参         数 push 进数组传递进去。当参数数量不确定时，函数内部也可以通过 arguments 这个数组来便利所有的参数。
	
	_____________________________________
	

	在javascript OOP中，我们经常会这样定义：
	function cat(){
	}
	cat.prototype={
	food:"fish",
	say: function(){
	alert("I love "+this.food);
	}
	}

	var blackCat = new cat;
	blackCat.say();
	但是如果我们有一个对象whiteDog = {food:"bone"},我们不想对它重新定义say方法，那么我们可以通过call或apply用blackCat的say方法：					blackCat.say.call(whiteDog);
	所以，可以看出call和apply是为了动态改变this而出现的，当一个object没有某个方法，但是其他的有，我们可以借助call或apply用其它对象的方法来操作。
	用的比较多的，通过document.getElementsByTagName选择的dom 节点是一种类似array的array。它不能应用Array下的push,pop等方法。我们可以通过：
	var domNodes = Array.prototype.slice.call(document.getElementsByTagName("*"));
	这样domNodes就可以应用Array下的所有方法了。
```

- 垃圾收集

```
	(1) 标记清除：进入环境、离开环境标记，然后统一销毁带标记的	
	(2) 引用计数：当声明一个变量并将引用类型值复制该值，引用次数为1，同个值又被赋给另一个变量，加1，相反，这个值引用的变量又得了另一个值，减1，为0			则回收	
```

3.对象

- 创建对象

```
	1.工厂模式
		function createPerson(name, age, job){
			var o = new Object();
			o.name = name;
			o.age = age;
			o.job = job;
			o.sayName = function(){
				alert(this.name);
			}
			return o;
		}
		var person1 = createPerson("Jimmy", 29, "Front-end Engineer");
		var person2 = createPerson("David", 27, "Front-end Engineer");
	2.构造函数模式
		function Person(name, age, job){
			this.name = name;
			this.age = age;
			this.job = job;
			this.sayName = function(){
				alert(this.name);
			}
		}
		var person1 = new Person("Jimmy", 29, "Front-end Engineer");
		var person2 = new Person("David", 27, "Front-end Engineer");
	3.原型模式
		function Person(){

		}
		Person.prototype.name="Jimmy";
		Person.prototype.age=29;
		Person.prototype.name="Front-end Engineer";
		Person.prototype.sayName=function(){
			alert(this.name)
		}
		var person1 = new Person();
		person1.sayName();//"Jimmy"
				
		var person2 = new Person();
		person2.sayName();//"Jimmy"
		
	4.组合使用构造函数模式和原型模式

		function Person(name, age, job){
			this.name = name;
			this.age = age;
			this.job = job;
			this.friends = ["cate","lucy"];
		}

		Person.prototype = {
			constructor : Person,
			sayName : function(){
				alert(this.name)
			}
		}
		var person1 = new Person("Jimmy", 29, "Front-end Engineer");
		var person2 = new Person("David", 27, "Front-end Engineer");

		person1.friends.push("lily");
		alert(person1.friends);//"cate,lucy,lily"
		alert(person2.friends)//"cate,lucy"
		alert(person1.friends === person2.friends)//false
		alert(person1.sayName === person2.sayName)//false
	
	5.动态原型模式(best)

		把原型的创建放在构造函数中完成。

		function Person(name, age, job){
			//属性
			this.name = name;
			this.age = age;
			this.job = job;
			//方法
			if(typeof this.sayName != "function"){

				Person.prototype.sayName = function(){
					alert(this.name)
				}

			}
		}

		var friend = new Person("Jimmy", 29, "Front-end Engineer");

		friend.sayName();
```

- 原型(https://segmentfault.com/a/1190000005824449)

![图](https://sfault-image.b0.upaiyun.com/755/273/755273249-57a2e38acba17_articlex "title")
```
	万物初生时，一个null对象，凭空而生，接着Object、Function学着null的模样塑造了自己，并且它们彼此之间喜结连理，提供了prototype和constructor，一	   个给子孙提供了基因，一个则制造万千子子孙孙。
    在JavaScript中，null也是作为一个对象存在，基于它继承的子子孙孙，当属对象。乍一看，null像是上帝,而Object和Function犹如JavaScript世界中的亚当     与夏娃。

	原型指针 __proto__
		在JavaScript中，每个对象都拥有一个原型对象，而指向该原型对象的内部指针则是__proto__,通过它可以从中继承原型对象的属性，原型是JavaScript中			的基因链接，有了这个，才能知道这个对象的祖祖辈辈。从对象中的__proto__可以访问到他所继承的原型对象。

		var a = new Array();
		a.__proto__ === Array.prototype // true
		上面代码中，创建了一个Array的实例a，该实例的原型指向了Array.prototype。
		Array.prototype本身也是一个对象，也有继承的原型:

		a.__proto__.__proto__ === Object.prototype  // true
		// 等同于 Array.prototype.__proto__ === Object.prototype
		这就说了明了，Array本身也是继承自Object的，那么Object的原型指向的是谁呢？

		a.__proto__.__proto__.__proto__ === null  // true
		// 等同于 Object.prototype.__proto__ === null
		所以说，JavaScript中的对象，追根溯源都是来自一个null对象。
		除了使用.__proto__方式访问对象的原型，还可以通过Object.getPrototypeOf方法来获取对象的原型，以及通过Object.setPrototypeOf方法来重写对象		 的原型。
	原型对象 prototype
		函数作为JavaScript中的一等公民，它既是函数又是对象，函数的原型指向的是Function.prototype
		
		var Foo = function() {}
		Foo.__proto__ === Function.prototype // true
		函数实例除了拥有__proto__属性之外，还拥有prototype属性。通过该函数构造的新的实例对象，其原型指针__proto__会指向该函数的prototype属性。

		var a = new Foo();
		a.__proto__ === Foo.prototype; // true
		而函数的prototype属性，本身是一个由Object构造的实例对象。

		Foo.prototype.__proto__ === Object.prototype; // true
		prototype属性很特殊，它还有一个隐式的constructor，指向了构造函数本身。

		Foo.prototype.constructor === Foo; // true
		a.constructor === Foo; // true
		a.constructor === Foo.prototype.constructor; // true
		PS: a.constructor属性并不属于a（a.hasOwnProperty("constructor") === false），而是读取的a.__proto__.constructor，所以上图用虚线表示		  a.constructor，方便理解。
	原型链
		概念：

		原型链作为实现继承的主要方法，其基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法。
		每个构造函数都有一个原型对象(prototype)，原型对象都包含一个指向构造函数的指针(constructor)，而实例都包含一个指向原型对象的内部指针				(__proto__)。

		那么，假如我们让原型对象等于另一个类型的实例，此时的原型对象将包含一个指向另一个原型的指针，相应地，另一个原型中也包含着一个指向另一个构造函	      数的指针。假如另一个原型又是另一个类型的实例，那么上述关系依然成立。如此层层递进，就构造了实例与原型的链条，这就是原型链的基本概念。

		意义：“原型链”的作用在于，当读取对象的某个属性时，JavaScript引擎先寻找对象本身的属性，如果找不到，就到它的原型去找，如果还是找不到，就到原		   型的原型去找。以此类推，如果直到最顶层的Object.prototype还是找不到，则返回undefine。
	亲子鉴定
		在JavaScript中，也存在鉴定亲子之间DNA关系的方法：

		instanceof 运算符返回一个布尔值，表示一个对象是否由某个构造函数创建。
		Object.isPrototypeOf() 只要某个对象处在原型链上，isProtypeOf都返回true
		var Bar = function() {}
		var b = new Bar();
		b instanceof Bar // true
		Bar.prototype.isPrototypeOf(b) // true
		Object.prototype.isPrototypeOf(Bar) // true
		要注意，实例b的原型是Bar.prototype而不是Bar
```


- 继承

```
	1.原型链
		function SuperType(){
			this.property = true;
		}
		SuperType.prototype.getSuperValue = function(){
			return this.property;
		}
		function SubType(){
			this.subproperty = false;
		}
		//继承SuperType
		SubType.prototype = new SuperType();
		SubType.prototype.getSubValue = function(){
			return this.subproperty;
		}

		var instance = new SubType();
		alert(instance.getSuperValue());//true

		所有函数的默认原型都是Object的实例
	2.借用构造函数

		function SuperType(){
			this.colors = ["red","black","blue"];
		}
		function SubType(){
			//继承SuperType
			SuperType.call(this);
		}

		var instance1 = new SubType();
		instance1.colors.push("green");
		alert(instance1.colors)//"red,black,blue,green"

		var instance2 = new SubType();
		alert(instance1.colors)//"red,black,blue"

		传递参数

		function SuperType(name){
			this.name = name;
		}

		function SubType(){
			//继承SuperType,同时还传递了参数
			SuperType.call(this,"Jimmy");

			//实例属性
			this.age="27";
		}

		var instance = new Subtype();
		alert(instance.name);//"Jimmy"
		alert(instance.age);//27
	3.组合继承
		function SuperType(name){
			this.name = name;
			this.colors = ["red","black","blue"];
		}

		SuperType.prototype.sayName = function(){
			alert(this.name)
		}

		function SubType(name,age){
			//继承属性
			SuperType.call(this,name);

			this.age = age;
		}

		//继承方法
		SubType.prototype = new SuperType();
		SubType.prototype.constructor = SubType;
		SubType.prototype.sayAge = function(){
			alert(this.age)
		}

		var instance1 = new SubType("Jimmy"，29)；
		instance1.colors.push("green");
		alert(instance1.colors);//"red,black,blue,green"
		instance1.sayName();//"Jimmy"
		instance1.sayAge()//29

		var instance2 = new SubType("Jason"，29)；
		alert(instance2.colors);//"red,black,blue"
		instance2.sayName();//"Jason"
		instance2.sayAge()//29
	4.原型式继承

		function object(o){
			function F(){};
			F.prototype = o;
			return new F();
		}

		var person = {
			name : "Jimmy",
			friend : ["Shelby","Sam","Van"]
		}

		var anotherPerson = object(person);
		anotherPerson.name = "Gerg";
		anotherPerson.friends.push("Rob");

		var yetPerson = object(person);
		yetPerson.name = "Linda";
		yetPerson.friends.push("Barbie");

		alert(person.friends);//"Shelby,Sam,Van,Rob,Barbie"

		Object.create()
		var person = {
			name : "Jimmy",
			friend : ["Shelby","Sam","Van"]
		}

		var anotherPerson = Object.create(person,{
			name:{
				value:"Greg"
			}
		})

		alert(anotherPerson.name);//"Greg"
	6.寄生组合式继承(best)
		function inheritPrototype(subType,superType){
			var prototype = object(superType.prototype);//创建对象
			prototype.constructor = subType;//增强对象
			subType.prototype = prototype;//指定对象
		}

		function SuperType(name){
			this.name = name;
			this.colors = ["red","black","blue"];
		}

		SuperType.prototype.sayName = function(){
			alert(this.name)
		}

		function SubType(name,age){
			//继承属性
			SuperType.call(this,name);

			this.age = age;
		}

		inheritPrototype(SubType,SuperType);

		SubType.prototype.sayAge = function(){
			alert(this.age)
		}
```

- new过程

```
	对于 var o = new Foo();

	//JavaScript 实际上执行的是：
		var o = new Object();
		o.[[Prototype]] = Foo.prototype;
		Foo.call(o);
		在JS中,绝大多数的函数都是既可以调用也可以实例化的.我们既可以直接执行函数得到函数的返回值.也可以通过new操作符得到一个对象.
		在javascript中, 通过new可以产生原对象的一个实例对象，而这个实例对象继承了原对象的属性和方法。因此，new存在的意义在于它实现了javascript中		  的继承，而不仅仅是实例化了一个对象！
	new不new的区别：
		如果函数返回值为常规意义上的值类型（Number、String、Boolean）时，new函数将会返回一个该函数的实例对象，而如果函数返回一个引用类型					（Object、Array、Function），则new函数与直接调用函数产生的结果等同。
```

4.内置对象

- Array

```
	检查是否是数组
    	ES5+ ： Array.isArray()

    之前版本做兼容：
    	if(typeof Array.isArray === "undefined"){
    		Array.isArray = function (arg){
    			return Object.prototype.toString.call(arg) === "[object Array]";
    		}
    	}
	Array 对象方法
		是否改变现有数组	方法	描述
		否 	concat()	连接两个或更多的数组，并返回结果。  
		否  join()	把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。
		是  pop()	删除并返回数组的最后一个元素
		是	push()	向数组的末尾添加一个或更多元素，并返回新的长度。
		是	reverse()	颠倒数组中元素的顺序。
		是	shift()	删除并返回数组的第一个元素
		否	slice()	从某个已有的数组返回选定的元素
		是	sort()	对数组的元素进行排序
		是	splice()	删除元素，并向数组添加新元素。
			toSource()	返回该对象的源代码。
			toString()	把数组转换为字符串，并返回结果。
			toLocaleString()	把数组转换为本地数组，并返回结果。 
		是	unshift()	向数组的开头添加一个或更多元素，并返回新的长度。
			valueOf()	返回数组对象的原始值
```

- Function

```
	创建函数的三种方式
		1.函数声明
		  	function sum1(n1,n2){
				return n1+n2;
		  	};
		2.函数表达式，又叫函数字面量
			var sum2=function(n1,n2){
				return n1+n2;
			};
			几种自执行函数：
				//可用来传参
				(function(x,y){
				  console.log(x+y);
				})(2,3);

				//带返回值
				var sum=(function(x,y){
				  return x+y;
				})(2,3);
				console.log(sum);

				~function(){
				  var name='~'
				  console.log(name);
				}();

				!function(){
				  var name='!'
				  console.log(name);
				}();

				;(function(){
				  var name=';'
				  console.log(name);
				})();

				-function(){
				  var name='-'
				  console.log(name);
				}();

				//逗号运算符
				1,function(){
				  var name=',';
				  console.log(name);
				}();

				//异或
				1^function(){
				  var name='^';
				  console.log(name);
				}();

				//比较运算符
				1>function(){
				  var name='>';
				  console.log(name);
				}();

				~+-!(function(){
				  var name='~+-!';
				  console.log(name);
				})();

				~!(function(){
				  var name='~!';
				  console.log(name);
				})();

				(function(){
				  var name='call';
				  console.log(name);
				}).call();

				(function(){
				  var name='apply';
				  console.log(name);
				}).apply();
		3.函数构造法，参数必须加引号
			var sum3=new Function('n1','n2','return n1+n2');
			console.log(sum3(2,3));//5
```

##WEB API

1.DOM API

- querySelector

```
	querySelector() 方法返回文档中匹配指定 CSS 选择器的一个元素。
	document.querySelector(".example").style.backgroundColor = "red";
```

- insertBefore

```
    定义和用法
    insertBefore() 方法在您指定的已有子节点之前插入新的子节点。
    语法
    node.insertBefore(newnode,existingnode)
    参数	类型	描述
    newnode	Node 对象	必需。需要插入的节点对象。
    existingnode	Node object	可选。在其之前插入新节点的子节点。如果未规定，则 insertBefore 方法会在结尾插入 newnode。
    例子
        <script>
        function myFunction()
        {
        var newItem=document.createElement("LI")
        var textnode=document.createTextNode("Water")
        newItem.appendChild(textnode)

        var list=document.getElementById("myList")
        list.insertBefore(newItem,list.childNodes[0]);
        }
        </script>
```

- appendChild

```
    定义和用法
    appendChild() 方法向节点添加最后一个子节点。
```

- childNodes/parentNode

```
    定义和用法
    childNodes 属性返回节点的子节点集合，以 NodeList 对象。
    例子
        <p><b>注释：</b>元素中的空格被视为文本，而文本被视为节点。</p>
        var c=document.body.childNodes;
        for (i=0; i<c.length; i++)
        {
        txt=txt + c[i].nodeName + "<br>";
        };
        打印出：
            P
            #text
            BUTTON
            #text
            SCRIPT
            #text
            P
            #text
```

- document.createElement/document.createTextNode/doucument.createDocumentFragment

```
    例子：
        var list = doucument.getElementById("myList"),
            fragment = doucument.createDocumentFragment(),
            item,
            i;
        for(i = 0; i < 10; i++){
            item = document.createElement("li");
            fragment.appendChild(item);
            item.appendChild(document.createTextNode("Item"+i))
        }
        list.appendChild(fragment);
```

- 事件
   
```
    (1) 冒泡与捕获
        事件捕获 html->body->div
        事件冒泡 div->body->html
        var useCapture = true; //false为冒泡获取【目标元素先触发】    true为捕获获取【父级元素先触发】
        one.addEventListener('click', function() {
            console.log('one');
        }, useCapture);
        阻止冒泡：
        /*
        * stopImmediatePropagation
        * 除了阻止元素上其它的事件处理函数的执行，这个方法还会通过在内部调用 event.stopPropagation() 来停止事件冒泡。
        * 如果仅仅想要停止事件冒泡到祖辈元素上，而让这个元素上的其它事件处理函数继续执行，我们可以使用 event.stopPropagation() 来代替。
        * 相当于e.stopPropagation() and return fasle
        */
        e.stopImmediatePropagation();
    (2) addEventListener/removeEventListener/attachEvent/detachEvent
        var addMyEvent = function (el,ev,fn){
            if(el.addEventListener){
                el.addEventListener(ev,fn,false)
            }else if(el.attachEvent){
                el.attachEvent("on"+ev,fn)
            }else{
                el["on" + ev] = fn;
            }
        }
    (3) createEvent/dispatchEvent
        参数	事件接口	初始化方法
        HTMLEvents	HTMLEvent	iniEvent()
        MouseEvents	MouseEvent	iniMouseEvent()
        UIEvents	UIEvent	iniUIEvent()
        //例子
        // Create the event.
        var event = document.createEvent('Event');
        // Define that the event name is 'build'.
        event.initEvent('build', true, true);
        // Listen for the event.
        elem.addEventListener('build', function (e) {
          // e.target matches elem
        }, false);
        // target can be any Element or other EventTarget.
        elem.dispatchEvent(event);
        
```

2.CSSDOM

- doucment.getComputedStyle(http://www.zhangxinxu.com/wordpress/2012/05/getcomputedstyle-js-getpropertyvalue-currentstyle/)

```
    getComputedStyle是一个可以获取当前元素所有最终使用的CSS属性值。返回的是一个CSS样式声明对象([object CSSStyleDeclaration])，只读。
    要写还是需要element.style
    getPropertyValue来取值
    语法如下：
    var style = window.getComputedStyle("元素", "伪类");
    例如：
    var dom = document.getElementById("test"),
    style = window.getComputedStyle(dom , ":after");
    例子：
    <style>
     #elem-container{
       position: absolute;
       left:     100px;
       top:      200px;
       height:   100px;
     }
    </style>

    <div id="elem-container">dummy</div>
    <div id="output"></div>  

    <script>
      function getTheStyle(){
        var elem = document.getElementById("elem-container");
        var theCSSprop = window.getComputedStyle(elem,null).getPropertyValue("height");
        document.getElementById("output").innerHTML = theCSSprop;
       }
      getTheStyle();
    </script>
```

- getBoundingClientRect

```
    这个方法返回一个矩形对象，包含四个属性：left、top、right和bottom。分别表示元素各边与页面上边和左边的距离。
    var box=document.getElementById('box');         // 获取元素
    alert(box.getBoundingClientRect().top);         // 元素上边距离页面上边的距离
    alert(box.getBoundingClientRect().right);       // 元素右边距离页面左边的距离
    alert(box.getBoundingClientRect().bottom);      // 元素下边距离页面上边的距离
    alert(box.getBoundingClientRect().left);        // 元素左边距离页面左边的距离

    注意：IE、Firefox3+、Opera9.5、Chrome、Safari支持，在IE中，默认坐标从(2,2)开始计算，导致最终距离比其他浏览器多出两个像素，我们需要做个兼容。
    document.documentElement.clientTop;  // 非IE为0，IE为2
    document.documentElement.clientLeft; // 非IE为0，IE为2
    functiongGetRect (element) {
        var rect = element.getBoundingClientRect();
        var top = document.documentElement.clientTop;
        var left= document.documentElement.clientLeft;
        return{
            top    :   rect.top - top,
            bottom :   rect.bottom - top,
            left   :   rect.left - left,
            right  :   rect.right - left
        }
    }
    分别加上外边据、内边距、边框和滚动条，用于测试所有浏览器是否一致。
```

- getClientRects

```
    TextRectangle的组成为键值对，主要有包括：
    {
    top : (number)
    bottom : (number)
    left : (number)
    right : (number)
    width : (number)
    height : (number)
    }
    getClientRects和getBoundingClientRect差异
        getClientRects返回的其实是个数组，数组中有很多个类似getBoundingClientRect返回的对象。getBoundingClientRect返回的永远是最外框框的那个矩         形区域相关的坐标偏移对象；而getClientRects是多行文字区域的坐标偏移集合，在非IE浏览器下，只对inline的标签有反应。
        一般getBoundingClientRect方法用的多一点。我们可以很容易获取某个元素的偏移值。甚至高宽都能很轻松的计算出来。所以，下载你想用js获取元素的高        宽尺寸，就可以试试getBoundingClientRect方法了。
        对getClientRects和getBoundingClientRect可以得到一个更好的说明.
        getClientRects 返回一个TextRectangle集合，就是TextRectangleList对象。
        getBoundingClientRect 返回 一个TextRectangle对象。
        那么这个TextRectangle对象有什么用呢，用来开判断文本是否换行！或者说用来获取矩形区域相关的坐标偏移对象！
        TextRectangle数组的长度可知道文字是否换行，甚至是换了几行，
        TextRectangle的几个属性和鼠标位置比较可以知道鼠标在哪一行上
```

3.canvas

```
    例子:
        <canvas id="myCanvas">your browser does not support the canvas tag </canvas>
        <script type="text/javascript">
        var canvas=document.getElementById('myCanvas');
        var ctx=canvas.getContext('2d');
        ctx.fillStyle='#FF0000';
        ctx.fillRect(0,0,80,100);
        </script>
```
4.BOM

- window对象

```
	Window 对象属性
	属性	描述
	closed	返回窗口是否已被关闭。
	defaultStatus	设置或返回窗口状态栏中的默认文本。
	document	对 Document 对象的只读引用。请参阅 Document 对象。
	history	对 History 对象的只读引用。请参数 History 对象。
	innerheight	返回窗口的文档显示区的高度。
	innerwidth	返回窗口的文档显示区的宽度。
	length	设置或返回窗口中的框架数量。
	location	用于窗口或框架的 Location 对象。请参阅 Location 对象。
	name	设置或返回窗口的名称。
	Navigator	对 Navigator 对象的只读引用。请参数 Navigator 对象。
	opener	返回对创建此窗口的窗口的引用。
	outerheight	返回窗口的外部高度。
	outerwidth	返回窗口的外部宽度。
	pageXOffset	设置或返回当前页面相对于窗口显示区左上角的 X 位置。
	pageYOffset	设置或返回当前页面相对于窗口显示区左上角的 Y 位置。
	parent	返回父窗口。
	Screen	对 Screen 对象的只读引用。请参数 Screen 对象。
	self	返回对当前窗口的引用。等价于 Window 属性。
	status	设置窗口状态栏的文本。
	top	返回最顶层的先辈窗口。
	window	window 属性等价于 self 属性，它包含了对窗口自身的引用。
	screenLeft
	screenTop
	screenX
	screenY
	只读整数。声明了窗口的左上角在屏幕上的的 x 坐标和 y 坐标。IE、Safari 和 Opera 支持 screenLeft 和 screenTop，而 Firefox 和 Safari 支持 screenX 和 screenY。
	Window 对象方法
	方法	描述
	alert()	显示带有一段消息和一个确认按钮的警告框。
	blur()	把键盘焦点从顶层窗口移开。
	clearInterval()	取消由 setInterval() 设置的 timeout。
	clearTimeout()	取消由 setTimeout() 方法设置的 timeout。
	close()	关闭浏览器窗口。
	confirm()	显示带有一段消息以及确认按钮和取消按钮的对话框。
	createPopup()	创建一个 pop-up 窗口。
	focus()	把键盘焦点给予一个窗口。
	moveBy()	可相对窗口的当前坐标把它移动指定的像素。
	moveTo()	把窗口的左上角移动到一个指定的坐标。
	open()	打开一个新的浏览器窗口或查找一个已命名的窗口。
	print()	打印当前窗口的内容。
	prompt()	显示可提示用户输入的对话框。
	resizeBy()	按照指定的像素调整窗口的大小。
	resizeTo()	把窗口的大小调整到指定的宽度和高度。
	scrollBy()	按照指定的像素值来滚动内容。
	scrollTo()	把内容滚动到指定的坐标。
	setInterval()	按照指定的周期（以毫秒计）来调用函数或计算表达式。
	setTimeout()	在指定的毫秒数后调用函数或计算表达式。
```

- location对象

```
	Location 对象属性
	属性	描述
	hash	设置或返回从井号 (#) 开始的 URL（锚）。
	host	设置或返回主机名和当前 URL 的端口号。
	hostname	设置或返回当前 URL 的主机名。
	href	设置或返回完整的 URL。
	pathname	设置或返回当前 URL 的路径部分。
	port	设置或返回当前 URL 的端口号。
	protocol	设置或返回当前 URL 的协议。
	search	设置或返回从问号 (?) 开始的 URL（查询部分）。
	Location 对象方法
	assign()	加载新的文档。
	reload()	重新加载当前文档。
	replace()	用新的文档替换当前文档。
```

- navigator对象

```
	Navigator 对象属性
	属性	描述
	appCodeName	返回浏览器的代码名。
	appMinorVersion	返回浏览器的次级版本。
	appName	返回浏览器的名称。
	appVersion	返回浏览器的平台和版本信息。
	browserLanguage	返回当前浏览器的语言。
	cookieEnabled	返回指明浏览器中是否启用 cookie 的布尔值。
	cpuClass	返回浏览器系统的 CPU 等级。
	onLine	返回指明系统是否处于脱机模式的布尔值。
	platform	返回运行浏览器的操作系统平台。
	systemLanguage	返回 OS 使用的默认语言。
	userAgent	返回由客户机发送服务器的 user-agent 头部的值。
	userLanguage	返回 OS 的自然语言设置。
```

- screen对象

```
	Screen 对象属性
	属性	描述
	availHeight	返回显示屏幕的高度 (除 Windows 任务栏之外)。
	availWidth	返回显示屏幕的宽度 (除 Windows 任务栏之外)。
	bufferDepth	设置或返回调色板的比特深度。
	colorDepth	返回目标设备或缓冲器上的调色板的比特深度。
	deviceXDPI	返回显示屏幕的每英寸水平点数。
	deviceYDPI	返回显示屏幕的每英寸垂直点数。
	fontSmoothingEnabled	返回用户是否在显示控制面板中启用了字体平滑。
	height	返回显示屏幕的高度。
	logicalXDPI	返回显示屏幕每英寸的水平方向的常规点数。
	logicalYDPI	返回显示屏幕每英寸的垂直方向的常规点数。
	pixelDepth	返回显示屏幕的颜色分辨率（比特每像素）。
	updateInterval	设置或返回屏幕的刷新率。
	width	返回显示器屏幕的宽度。
```

- history对象
```
	History 对象属性
	属性	描述
	length	返回浏览器历史列表中的 URL 数量。
	History 对象方法
	方法	描述
	back()	加载 history 列表中的前一个 URL。
	forward()	加载 history 列表中的下一个 URL。
	go()	加载 history 列表中的某个具体页面。
```

##HTTP
1.状态码

```
    1XX：信息状态码
        100 Continue：客户端应当继续发送请求。这个临时相应是用来通知客户端它的部分请求已经被服务器接收，且仍未被拒绝。客户端应当继续发送请求的剩余部         分，或者如果请求已经完成，忽略这个响应。服务器必须在请求万仇向客户端发送一个最终响应
        101 Switching Protocols：服务器已经理解力客户端的请求，并将通过Upgrade消息头通知客户端采用不同的协议来完成这个请求。在发送完这个响应最后的         空行后，服务器将会切换到Upgrade消息头中定义的那些协议。
    2XX：成功状态码
        200 OK：请求成功，请求所希望的响应头或数据体将随此响应返回
        201 Created：
        202 Accepted：
        203 Non-Authoritative Information：
        204 No Content：
        205 Reset Content：
        206 Partial Content：
    3XX：重定向
        300 Multiple Choices：
        301 Moved Permanently：
        302 Found：
        303 See Other：
        304 Not Modified：
        305 Use Proxy：
        306 （unused）：
        307 Temporary Redirect：
     4XX：客户端错误
        400 Bad Request:
        401 Unauthorized:
        402 Payment Required:
        403 Forbidden:
        404 Not Found:
        405 Method Not Allowed:
        406 Not Acceptable:
        407 Proxy Authentication Required:
        408 Request Timeout:
        409 Conflict:
        410 Gone:
        411 Length Required:
        412 Precondition Failed:
        413 Request Entity Too Large:
        414 Request-URI Too Long:
        415 Unsupported Media Type:
        416 Requested Range Not Satisfiable:
        417 Expectation Failed:
     5XX: 服务器错误
        500 Internal Server Error:
        501 Not Implemented:
        502 Bad Gateway:
        503 Service Unavailable:
        504 Gateway Timeout:
        505 HTTP Version Not Supported:
```
2.头

```
    Access-Control-Allow-Origin:* 支持跨域
    常见的request
        GET /Protocols/rfc2616/rfc2616-sec5.html HTTP/1.1
        Host: www.w3.org
        Connection: keep-alive
        Cache-Control: max-age=0
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
        User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.153 Safari/537.36
        Referer: https://www.google.com.hk/
        Accept-Encoding: gzip,deflate,sdch
        Accept-Language: zh-CN,zh;q=0.8,en;q=0.6
        Cookie: authorstyle=yes
        If-None-Match: "2cc8-3e3073913b100"
        If-Modified-Since: Wed, 01 Sep 2004 13:24:52 GMT

        name=qiu&age=25
    常见的response
        HTTP/1.1 200 OK
        Date: Tue, 08 Jul 2014 05:28:43 GMT
        Server: Apache/2
        Last-Modified: Wed, 01 Sep 2004 13:24:52 GMT
        ETag: "40d7-3e3073913b100"
        Accept-Ranges: bytes
        Content-Length: 16599
        Cache-Control: max-age=21600
        Expires: Tue, 08 Jul 2014 11:28:43 GMT
        P3P: policyref="http://www.w3.org/2001/05/P3P/p3p.xml"
        Content-Type: text/html; charset=iso-8859-1

        {"name": "qiu", "age": 25}
    HTTP头部详解
        1、 Accept：告诉WEB服务器自己接受什么介质类型，*/* 表示任何类型，type/* 表示该类型下的所有子类型，type/sub-type。
        2、 Accept-Charset： 浏览器申明自己接收的字符集
        Accept-Encoding： 浏览器申明自己接收的编码方法，通常指定压缩方法，是否支持压缩，支持什么压缩方法（gzip，deflate）
        Accept-Language：：浏览器申明自己接收的语言
        语言跟字符集的区别：中文是语言，中文有多种字符集，比如big5，gb2312，gbk等等。
        3、 Accept-Ranges：WEB服务器表明自己是否接受获取其某个实体的一部分（比如文件的一部分）的请求。bytes：表示接受，none：表示不接受。
        4、 Age：当代理服务器用自己缓存的实体去响应请求时，用该头部表明该实体从产生到现在经过多长时间了。
        5、 Authorization：当客户端接收到来自WEB服务器的 WWW-Authenticate 响应时，用该头部来回应自己的身份验证信息给WEB服务器。
        6、 Cache-Control：请求：no-cache（不要缓存的实体，要求现在从WEB服务器去取）
        max-age：（只接受 Age 值小于 max-age 值，并且没有过期的对象）
        max-stale：（可以接受过去的对象，但是过期时间必须小于 max-stale 值）
        min-fresh：（接受其新鲜生命期大于其当前 Age 跟 min-fresh 值之和的缓存对象）
        响应：public(可以用 Cached 内容回应任何用户)
        private（只能用缓存内容回应先前请求该内容的那个用户）
        no-cache（可以缓存，但是只有在跟WEB服务器验证了其有效后，才能返回给客户端）
        max-age：（本响应包含的对象的过期时间）
        ALL: no-store（不允许缓存）
        7、 Connection：请求：close（告诉WEB服务器或者代理服务器，在完成本次请求的响应后，断开连接，不要等待本次连接的后续请求了）。
        keepalive（告诉WEB服务器或者代理服务器，在完成本次请求的响应后，保持连接，等待本次连接的后续请求）。
        响应：close（连接已经关闭）。
        keepalive（连接保持着，在等待本次连接的后续请求）。
        Keep-Alive：如果浏览器请求保持连接，则该头部表明希望 WEB 服务器保持连接多长时间（秒）。例如：Keep-Alive：300
        8、 Content-Encoding：WEB服务器表明自己使用了什么压缩方法（gzip，deflate）压缩响应中的对象。例如：Content-Encoding：gzip
        9、Content-Language：WEB 服务器告诉浏览器自己响应的对象的语言。
        10、Content-Length： WEB 服务器告诉浏览器自己响应的对象的长度。例如：Content-Length: 26012
        11、Content-Range： WEB 服务器表明该响应包含的部分对象为整个对象的哪个部分。例如：Content-Range: bytes 21010-47021/47022
        12、Content-Type： WEB 服务器告诉浏览器自己响应的对象的类型。例如：Content-Type：application/xml
        13、 ETag：就是一个对象（比如URL）的标志值，就一个对象而言，比如一个 html 文件，如果被修改了，其 Etag 也会别修改，所以ETag 的作用跟 Last-         Modified 的作用差不多，主要供 WEB 服务器判断一个对象是否改变了。比如前一次请求某个 html 文件时，获得了其 ETag，当这次又请求这个文件时，           浏览器就会把先前获得的 ETag 值发送给WEB 服务器，然后 WEB 服务器会把这个 ETag 跟该文件的当前 ETag 进行对比，然后就知道这个文件有没有改变           了。
        14、 Expired：WEB服务器表明该实体将在什么时候过期，对于过期了的对象，只有在跟WEB服务器验证了其有效性后，才能用来响应客户请求。是 HTTP/1.0         的头部。例如：Expires：Sat, 23 May 2009 10:02:12 GMT
        15、 Host：客户端指定自己想访问的WEB服务器的域名/IP 地址和端口号。例如：Host：rss.sina.com.cn
        16、 If-Match：如果对象的 ETag 没有改变，其实也就意味著对象没有改变，才执行请求的动作。
        17、If-None-Match：如果对象的 ETag 改变了，其实也就意味著对象也改变了，才执行请求的动作。
        18、 If-Modified-Since：如果请求的对象在该头部指定的时间之后修改了，才执行请求的动作（比如返回对象），否则返回代码304，告诉浏览器该对象没         有修改。例如：If-Modified-Since：Thu, 10 Apr 2008 09:14:42 GMT
        19、If-Unmodified-Since：如果请求的对象在该头部指定的时间之后没修改过，才执行请求的动作（比如返回对象）。
        20、 If-Range：浏览器告诉 WEB 服务器，如果我请求的对象没有改变，就把我缺少的部分给我，如果对象改变了，就把整个对象给我。浏览器通过发送请求         对象的 ETag 或者 自己所知道的最后修改时间给 WEB 服务器，让其判断对象是否改变了。总是跟 Range 头部一起使用。
        21、 Last-Modified：WEB 服务器认为对象的最后修改时间，比如文件的最后修改时间，动态页面的最后产生时间等等。例如：Last-Modified：Tue, 06           May 2008 02:42:43 GMT
        22、 Location：WEB 服务器告诉浏览器，试图访问的对象已经被移到别的位置了，到该头部指定的位置去取。例如：Location：                               http://i0.sinaimg.cn/dy/deco/2008/0528/sinahome_0803_ws_005_text_0.gif
        23、 Pramga：主要使用 Pramga: no-cache，相当于 Cache-Control： no-cache。例如：Pragma：no-cache
        24、 Proxy-Authenticate： 代理服务器响应浏览器，要求其提供代理身份验证信息。Proxy-Authorization：浏览器响应代理服务器的身份验证请求，提供         自己的身份信息。
        25、 Range：浏览器（比如 Flashget 多线程下载时）告诉 WEB 服务器自己想取对象的哪部分。例如：Range: bytes=1173546-
        26、 Referer：浏览器向 WEB 服务器表明自己是从哪个 网页/URL 获得/点击 当前请求中的网址/URL。例如：Referer：http://www.sina.com/
        27、 Server: WEB 服务器表明自己是什么软件及版本等信息。例如：Server：Apache/2.0.61 (Unix)
        28、 User-Agent: 浏览器表明自己的身份（是哪种浏览器）。例如：User-Agent：Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN;                     rv:1.8.1.14) Gecko/20080404 Firefox/2、0、0、14
        29、 Transfer-Encoding: WEB 服务器表明自己对本响应消息体（不是消息体里面的对象）作了怎样的编码，比如是否分块（chunked）。例如：Transfer-         Encoding: chunked
        30、 Vary: WEB服务器用该头部的内容告诉 Cache 服务器，在什么条件下才能用本响应所返回的对象响应后续的请求。假如源WEB服务器在接到第一个请求消         息时，其响应消息的头部为：Content-Encoding: gzip; Vary: Content-Encoding那么 Cache 服务器会分析后续请求消息的头部，检查其 Accept-             Encoding，是否跟先前响应的 Vary 头部值一致，即是否使用相同的内容编码方法，这样就可以防止 Cache 服务器用自己 Cache 里面压缩后的实体响应给不         具备解压能力的浏览器。例如：Vary：Accept-Encoding
        31、 Via： 列出从客户端到 OCS 或者相反方向的响应经过了哪些代理服务器，他们用什么协议（和版本）发送的请求。当客户端请求到达第一个代理服务器         时，该服务器会在自己发出的请求里面添加 Via 头部，并填上自己的相关信息，当下一个代理服务器收到第一个代理服务器的请求时，会在自己发出的请求里         面复制前一个代理服务器的请求的Via 头部，并把自己的相关信息加到后面，以此类推，当 OCS 收到最后一个代理服务器的请求时，检查 Via 头部，就知道         该请求所经过的路由。例如：Via：1.0 236.D0707195.sina.com.cn:80 (squid/2.6.STABLE13)
```

3.方法

```
    一台服务器要与HTTP1.1兼容，只要为资源实现GET和HEAD方法即可
    GET是最常用的方法，通常用于请求服务器发送某个资源。
    HEAD与GET类似，但服务器在响应中值返回首部，不返回实体的主体部分
    PUT让服务器用请求的主体部分来创建一个由所请求的URL命名的新文档，或者，如果那个URL已经存在的话，就用干这个主体替代它
    POST起初是用来向服务器输入数据的。实际上，通常会用它来支持HTML的表单。表单中填好的数据通常会被送给服务器，然后由服务器将其发送到要去的地方。
    TRACE会在目的服务器端发起一个环回诊断，最后一站的服务器会弹回一个TRACE响应并在响应主体中携带它收到的原始请求报文。TRACE方法主要用于诊断，用于验     证请求是否如愿穿过了请求/响应链。
    OPTIONS方法请求web服务器告知其支持的各种功能。可以查询服务器支持哪些方法或者对某些特殊资源支持哪些方法。
    DELETE请求服务器删除请求URL指定的资源
```
##常见框架
##模块化开发
##构建工具
##版本控制
##优化
##算法

1.堆排序
//排序、搜索、动态规划    
##数据结构
1.二叉树（AVL树、红黑树）
2.二叉堆
##常见面试题
1.从浏览器地址栏输入url到显示页面的步骤(以HTTP为例)？
##坑
