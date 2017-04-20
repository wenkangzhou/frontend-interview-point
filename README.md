# 前端面试知识点整理

## 目录

- [HTML](#HTML)
	- viewport meta
	- 语义
- [CSS](#CSS)
	- 排版
	- 绘制
	- 动画
	- 理解和还原设计图意
	- 其它
- [JS](#JS)
	- 基本概念
	- 函数
	- 对象
	- 内置对象
	- 正则
	- ES6
- [WEB API](#WEB API)
	- DOM API
	- CSSDOM
	- canvas
	- BOM
- [HTTP](#HTTP)
	- 状态码
	- 头
	- 方法
- [常见框架](#常见框架)
	- vue
	- react
	- angular
- [模块化开发](#模块化开发)
	- AMD
	- CMD
	- CommonJS
	- UMD
- [构建工具](#构建工具)
	- Grunt
	- Gulp
	- Webpack
- [版本控制](#版本控制)
	- Git
	- Svn
- [优化](#优化)
	- 雅虎24法则
	- More
	- 稳定性
	- 响应式
	- 搜索SEO
- [算法](#算法)
	- 排序
	- 搜索
	- 动态规划
	- 二叉树
- [数据结构](#数据结构)
	- 二叉树
	- 二叉堆
- [常见面试题](#常见面试题)
	- 从浏览器地址栏输入url到显示页面的步骤(以HTTP为例)
	- 原生AJAX
	- 深浅复制
	- 跨域方式
	- 移动端1px细线解决方案总结
	- 请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象
	- 说说get和post请求的区别
	- 什么是 “use strict”? 使用它的好处和坏处分别是什么？
	- 有一个长度为100的数组，请以优雅的方式求出该数组的前10个元素之和
	- 不使用loop循环，创建一个长度为100的数组，并且每个元素的值等于它的下标
	- 实现对数组进行乱序
	- xss和csrf分别是什么？
	- 说说前端如何解决异步回调地狱？
	- 淘宝那里的商品项，如图片，滚动到了才加载，你知道怎么实现么(图片可视区域加载)
	- 到底该不该用 CSS reset？
	- 前端link和import的区别
	- 理解HTTP/304响应(HTTP原理中的缓存机制)
	- css实现超出字体内容出现 …
	- JavaScript函数节流和函数防抖之间的区别
	- 实现一个LazyMan
	- 在textarea光标处插入内容
	- 如何快速把一个多维数组转换成一个简单一维数组
	- nodeType
	- 正则表达式贪婪与非贪婪模式
	- 正则捕获
	- 重排与重绘
	- Underscore _.template 方法使用详解
- [一些常见问题记录](#一些常见问题记录)

## HTML

### 1.viewport meta

```javascript
    <meta name ="viewport" content ="width=device-width,initial-scale=1,maximum-scale=1, minimum-scale=1, user-scalable=no"> 
    width  　　　　 viewport 宽度(数值/device-width)   
    height         viewport 高度(数值/device-height)   
    initial-scale  初始缩放比例   
    maximum-scale  最大缩放比例   
    minimum-scale  最小缩放比例   
    user-scalable  是否允许用户缩放(yes/no)  
```

### 2.语义

>web语义化是指通过HTML标记表示页面包含的信息，包含了HTML标签的语义化和css命名的语义化。 
HTML标签的语义化是指：通过使用包含语义的标签（如h1-h6）恰当地表示文档结构 
css命名的语义化是指：为html标签添加有意义的class，id补充未表达的语义，如Microformat通过添加符合规则的class描述信息 

为什么需要语义化：

- 去掉样式后页面呈现清晰的结构
- 盲人使用读屏器更好地阅读
- 搜索引擎更好地理解页面，有利于收录
- 便团队项目的可持续运作及维护

HTML5新增语义化标签：header、footer、nav、article、aside、section等。

## CSS

### 1.排版
 
- position
 
```
    static 默认
    relative 相对定位
    absolute 绝对定位 飘出文档流
    	如果一个元素绝对定位后，其参照物是以离自身最近元素是否设置了相对定位，如果有设置将以离自己最近元素定位，
		如果没有将往其祖先元素寻找相对定位元素，一直找到html为止。
    fixed 固定 属于绝对定位
    inherit 规定应该从父元素继承 position 属性的值
	fixed 固定定位，参照位置是浏览器窗口的左上角，即坐标点为(0px, 0px)
	absolute 绝对定位，参展位置是离当前元素最近的定位方式为fixed,absolute,relative的祖先原则的左上角
```

- display

```
    inline 默认。此元素会被显示为内联元素，元素前后没有换行符。
    block 此元素将显示为块级元素，此元素前后会带有换行符。
    inline-block 行内块元素。
    flex（早期版本叫box） 将对象作为弹性伸缩盒显示。（http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html）
	table 此元素会作为块级表格来显示（类似 <table>），表格前后带有换行符。
	总体概念
		block和inline这两个概念是简略的说法，完整确切的说应该是 block-level elements (块级元素) 和 inline elements (内联元素)。
		block元素通常被现实为独立的一块，会单独换一行；inline元素则前后不会产生换行，一系列inline元素都在一行内显示，直到该行排满。
		大体来说HTML元素各有其自身的布局级别（block元素还是inline元素）：
		常见的块级元素有 DIV, FORM, TABLE, P, PRE, H1~H6, DL, OL, UL 等。
		常见的内联元素有 SPAN, A, STRONG, EM, LABEL, INPUT, SELECT, TEXTAREA, IMG, BR 等。
		block元素可以包含block元素和inline元素；但inline元素只能包含inline元素。
		要注意的是这个是个大概的说法，每个特定的元素能包含的元素也是特定的，所以具体到个别元素上，这条规律是不适用的。
		比如 P 元素，只能包含inline元素，而不能包含block元素。
		一般来说，可以通过display:inline和display:block的设置，改变元素的布局级别。
	block，inline和inlinke-block细节对比
		display:block
			block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。
			block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。
			block元素可以设置margin和padding属性。
		display:inline
			inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。
			inline元素设置width,height属性无效。
			inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；
			但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。
		display:inline-block
			简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。之后的内联对象会被排列在同一行内。
			比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性。
	Flex
		flex-direction 属性决定主轴的方向（即项目的排列	方向）
			.box {
			  flex-direction: row | row-reverse | column | column-reverse;
			}
		flex-wrap 属性定义，如果一条轴线排不下，如何换行
			.box{
			  flex-wrap: nowrap | wrap | wrap-reverse(换行，第一行在下方);
			}
		flex-flow 是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap
			.box {
			  flex-flow: <flex-direction> || <flex-wrap>;
			}
		justify-content 属性定义了项目在主轴上的对齐方式
			.box {
			  justify-content: flex-start | flex-end | center | space-between | space-around;
			}
			flex-start（默认值）：左对齐
			flex-end：右对齐
			center： 居中
			space-between：两端对齐，项目之间的间隔都相等。
			space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍
		align-items 属性定义项目在交叉轴上如何对齐
			.box {
			  align-items: flex-start | flex-end | center | baseline | stretch;
			}
			flex-start：交叉轴的起点对齐。
			flex-end：交叉轴的终点对齐。
			center：交叉轴的中点对齐。
			baseline: 项目的第一行文字的基线对齐。
			stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
		align-content 属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用
			box {
			  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
			}
			flex-start：与交叉轴的起点对齐。
			flex-end：与交叉轴的终点对齐。
			center：与交叉轴的中点对齐。
			space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
			space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
			stretch（默认值）：轴线占满整个交叉轴。
		order 属性定义项目的排列顺序。数值越小，排列越靠前，默认为0
			.item {
			  order: <integer>;
			}
		flex-grow 属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大
			.item {
			  flex-grow: <number>; /* default 0 */
			}
		flex-shrink 属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
			.item {
			  flex-shrink: <number>; /* default 1 */
			}
		flex-basis 属性定义了在分配多余空间之前，项目占据的主轴空间（main size）
			.item {
			  flex-basis: <length> | auto; /* default auto */
			}
		flex 属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto
			.item {
			  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
			}
		align-self 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性
			.item {
			  align-self: auto | flex-start | flex-end | center | baseline | stretch;
			}
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
        visibility: hidden;//display:none不占用位置 visibility占用
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
        “行高“指一行文字的高度，具体来说是指两行文字间基线间的距离。
		在CSS，line-height被用来控制行与行之间的垂直距离。
		line-height 属性会影响行框的布局。
		在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。
        从上到下四条线分别是顶线、中线、基线、底线，很像才学英语字母时的四线三格，
		我们知道vertical-align属性中有top、middle、baseline、bottom，就是和这四条线相关。
        行高是指上下文本行的基线间的垂直距离，即图中两条红线间垂直距离。
        行距是指一行底线到下一行顶线的垂直距离，即第一行粉线和第二行绿线间的垂直距离。
        半行距是行距的一半，即区域3垂直距离/2，区域1，2，3，4的距离之和为行高，而区域1，2，4距离之和为字体size，所以半行距也可以这么算：（行高-字体size）/2
    vertical-align（http://www.zhangxinxu.com/wordpress/2010/05/%E6%88%91%E5%AF%B9css-vertical-align%E7%9A%84%E4%B8%80%E4%BA%9B%E7%90%86%E8%A7%A3%E4%B8%8E%E8%AE%A4%E8%AF%86%EF%BC%88%E4%B8%80%EF%BC%89/）
        定义和用法
        	vertical-align 属性设置元素的垂直对齐方式。
        说明
        	该属性定义行内元素的基线相对于该元素所在行的基线的垂直对齐。
			允许指定负长度值和百分比值。这会使元素降低而不是升高。
			在表单元格中，这个属性会设置单元格框中的单元格内容的对齐方式。
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
    word-break
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
        word-wrap:break-word与word-break:break-all共同点是都能把长单词强行断句，
		不同点是word-wrap:break-word会首先起一个新行来放置长单词，新的行还是放不下这个长单词则会对长单词进行强制断句；
		而word-break:break-all则不会把长单词放在一个新行里，当这一行放不下的时候就直接强制断句了。
```
 
### 2.绘制

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
    t	ransform: none|transform-functions;
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

### 3.动画
 
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
	常用的也就是：宽度、高度、字体大小、颜色、显示隐藏、2D、3D、定位之后的top/left/right/bottom、内外边距。
	不支持：display属性。
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
 
### 4.理解和还原设计图意


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
		  height: 50%;
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
	(6)单行内容的居中
		只要给容器设置 line-height 和 height，并使两值相等，再加上 over-flow: hidden 就可以了
		.middle-demo-1{
			height: 4em;
			line-height: 4em;
			overflow: hidden;
		}
	(7)常规		
		<style>
			html,body {
				width: 100%;
				height: 100%;
				margin: 0;
				padding: 0;
			}
			.content {
				width: 300px;
				height: 300px;
				background: orange;
				margin: 0 auto; /*水平居中*/
				position: relative; 
				top: 50%; /*偏移*/
				margin-top: -150px; 
			}
		</style>
```

- 水平居中


```
	(1)如果需要居中的元素为常规流中inline元素，为父元素设置text-align: center;即可实现
	(2)如果需要居中的元素为常规流中block元素（margin: 0 auto）
		1）为元素设置宽度，
		2）设置左右margin为auto,
		3）IE6下需在父元素上设置text-align: center;
		4) 再给子元素恢复需要的值
	(3)如果需要居中的元素为浮动元素
		1）为元素设置宽度，
		2）position: relative，
		3）浮动方向偏移量（left或者right）设置为50%，
		4）浮动方向上的margin设置为元素宽度一半乘以-1
	(4)如果需要居中的元素为绝对定位元素(with:200px left:50% position:releate margin-left:-100px)
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
	(1)大的margin-bottom。
		这种技术的关键是给每个框设置大的底内边距，然后用数值相似的负外边距消除这个高度。
		这会导致每个列溢出容器元素。如果把容器的overflow属性设为hidden,列就在最高点被裁切。	
		<div id="wrap">
			<div id="left">
				<p>left</p>
			</div>
			<div id="center">
				<p>center</p>
			</div>
			<div id="right">
				<p>right</p>
			</div>
		</div>
		{
            margin: 0;
            padding: 0;
        }
        #wrap
        {
            overflow: hidden;
            width: 1000px;
            margin: 0 auto;
        }
        #left, #center, #right
        {
            margin-bottom: -10000px;
            padding-bottom: 10000px;
        }
        #left
        {
            float: left;
            width: 250px;
            background: #00FFFF;
        }
        #center
        {
            float: left;
            width: 500px;
            background: #FF0000;
        }
        #right
        {
            float: right;
            width: 250px;
            background: #00FF00;
        }
	(2)背景图片、背景色实现假等高
	(3)css3 column-count
		.newspaper
		{
		-moz-column-count:3; /* Firefox */
		-webkit-column-count:3; /* Safari and Chrome */
		column-count:3;
		}
```

- 自适应宽

```
   （1）百分比
   （2）@media screen 
   		@media (max-width: 600px) {
		  .facet_sidebar {
			display: none;
		}
   （3）flex
   （4）<meta name=”viewport” content=”width=device-width, initial-scale=1″ />
   （5）相对大小的字体em、rem、vw、vh
```
- 左侧固定 右侧自适应

```
	#left {   
		float: left;   
		width: 220px;   
		background-color: green;   
	}   
	#content {   
		background-color: orange;   
		margin-left: 220px;/*==等于左边栏宽度==*/  
	} 
	
	flex
		flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。
		浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
		.item {
		  flex-basis: <length> | auto; /* default auto */
		}
```



### 5.其它

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
        层叠就是在html文件中对于同一个元素可以有多个css样式存在，当有相同权重的样式存在时，
		会根据这些css样式的前后顺序来决定，处于最后面的css样式会被应用。
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

## JS

### 1.基本概念

- 标识符：首字母可以是字母、下划线、美元符号，其它多一个数字

- 基本数据类型：Undefined、Null、String、Number、Boolean

- typeof操作符（检测基本类型）

```
	"undefined" - 这个值未定义
	"boolean" - 这个值是布尔值
	"string" - 这个值是字符串	
	"number" - 这个值是数值
	"object" - 这个值是对象、数组或null
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

- isPrototypeOf(用来判断要检查其原型链的对象是否存在于指定对象实例中)

```
	var myFunc=function(){
		this.foo='value';	 
	};
	myFunc.prototype.ok='ok';
	thefunc=new myFunc();
	console.log(
		thefunc instanceof myFunc,//true
		myFunc instanceof Function,//true
		myFunc.prototype.isPrototypeOf(thefunc),//true
		Function.prototype.isPrototypeOf(myFunc),//true	 
		typeof thefunc,//object
	);
```


### 2.函数

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
		和全局作用域相反，局部作用域一般只在固定的代码片段内可访问到，最常见的例如函数内部，所有在一些地方也会看到有人把这种作用域称为函数作用域
	3. 作用域链（Scope Chain）
		(1)改变作用域链
			eval:避免使用			
			with:避免使用	
			catch:当try代码块中发生错误时，执行过程会跳转到catch语句，然后把异常对象推入一个可变对象并置于作用域的头部。
				  在catch代码块内部，函数的所有局部变量将会被放在第二个作用域链对象中。
	4. 查找、声明
		自下而上，沿作用链向上查找
		无所在哪声明，都等同于在函数顶部声明

```

- this

```
	1.在一般函数方法中使用 this 指代全局对象
	2.作为对象方法调用，this 指代上级对象
	3.作为构造函数调用，this 指代new出的对象
	4.apply 调用 ，apply方法作用是改变函数的调用对象，此方法的第一个参数为改变后调用这个函数的对象，this指代第一个参数
```

- call/apply

```
	call 和 apply 都是为了改变某个函数运行时的 context 即上下文而存在的，换句话说，就是为了改变函数体内部 this 的指向。
	因为 JavaScript 的函数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念。

	二者的作用完全一样，只是接受参数的方式不太一样。例如，有一个函数 func1 定义如下：
	var func1 = function(arg1, arg2) {};
	就可以通过 func1.call(this, arg1, arg2); 或者 func1.apply(this, [arg1, arg2]); 来调用。
	其中 this 是你想指定的上下文，他可以任何一个JavaScript 对象(JavaScript 中一切皆对象)，
	call 需要把参数按顺序传递进去，而 apply 则是把参数放在数组里。
	JavaScript 中，某个函数的参数数量是不固定的，因此要说适用条件的话，
	当你的参数是明确知道数量时，用 call，而不确定的时候，用 apply，然后把参数 push 进数组传递进去。
	当参数数量不确定时，函数内部也可以通过 arguments 这个数组来便利所有的参数。
	
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
	但是如果我们有一个对象whiteDog = {food:"bone"},我们不想对它重新定义say方法，那么我们可以通过call或apply用blackCat的say方法：blackCat.say.call(whiteDog);
	所以，可以看出call和apply是为了动态改变this而出现的，当一个object没有某个方法，但是其他的有，我们可以借助call或apply用其它对象的方法来操作。
	用的比较多的，通过document.getElementsByTagName选择的dom 节点是一种类似array的array。它不能应用Array下的push,pop等方法。我们可以通过：
	var domNodes = Array.prototype.slice.call(document.getElementsByTagName("*"));
	这样domNodes就可以应用Array下的所有方法了。
	
	_____________________________________
	
	和bind的区别：bind返回的是函数，aplly、call直接执行	
	
```

- 垃圾收集

```
	(1) 标记清除：进入环境、离开环境标记，然后统一销毁带标记的	
	(2) 引用计数：当声明一个变量并将引用类型值复制该值，引用次数为1，同个值又被赋给另一个变量，加1，
	            相反，这个值引用的变量又得了另一个值，减1，为0则回收	
```

### 3.对象

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
	万物初生时，一个null对象，凭空而生，接着Object、Function学着null的模样塑造了自己，并且它们彼此之间喜结连理，
	提供了prototype和constructor，一个给子孙提供了基因，一个则制造万千子子孙孙。
    在JavaScript中，null也是作为一个对象存在，基于它继承的子子孙孙，当属对象。
	乍一看，null像是上帝,而Object和Function犹如JavaScript世界中的亚当与夏娃。

	原型指针 __proto__
		在JavaScript中，每个对象都拥有一个原型对象，而指向该原型对象的内部指针则是__proto__,通过它可以从中继承原型对象的属性，
		原型是JavaScript中的基因链接，有了这个，才能知道这个对象的祖祖辈辈。从对象中的__proto__可以访问到他所继承的原型对象。

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
		除了使用.__proto__方式访问对象的原型，还可以通过Object.getPrototypeOf方法来获取对象的原型，以及通过Object.setPrototypeOf方法来重写对象的原型。
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
		PS: a.constructor属性并不属于a（a.hasOwnProperty("constructor") === false），而是读取的a.__proto__.constructor，
		    所以上图用虚线表示a.constructor，方便理解。
	原型链
		概念：

			原型链作为实现继承的主要方法，其基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法。
			每个构造函数都有一个原型对象(prototype)，原型对象都包含一个指向构造函数的指针(constructor)，而实例都包含一个指向原型对象的内部指针(__proto__)。

			那么，假如我们让原型对象等于另一个类型的实例，此时的原型对象将包含一个指向另一个原型的指针，
			相应地，另一个原型中也包含着一个指向另一个构造函数的指针。假如另一个原型又是另一个类型的实例，那么上述关系依然成立。
			如此层层递进，就构造了实例与原型的链条，这就是原型链的基本概念。

			意义：“原型链”的作用在于，当读取对象的某个属性时，JavaScript引擎先寻找对象本身的属性，如果找不到，就到它的原型去找，
			如果还是找不到，就到原型的原型去找。以此类推，如果直到最顶层的Object.prototype还是找不到，则返回undefine。
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
	7.klass
		var Man = klass(null,{
			_construct:function(what){
				console.log("Man's construct");
				this.name = what;
			},
			getName:function(){
				return this.name;
			}
		})
		var first = new Man('Adam');
		first.getName();//"Adam"

		var SuperMan = klass(Man,{
			_construct:function(what){
				console.log("SuperMan's construct")
			},
			getName:function(){
				var name = SuperMan.uber.getName.call(this);
				return "I am"+ name;
			}
		})

		var clark = new SuperMan('Clark Kent');
		clark.getName();//结果为"I am Clark Kent"

		var klass = function(Parent,props){
			var Child,F,i;
			//1.
			//新构造函数
			Child = function(){
				if(Child.uber && Child.uber.hasOwnProperty("_construct")){
					Child.uber._construct.apply(this,arguments);
				}
				if(Child.prototype.hasOwnProperty("_construct")){
					Child.prototype._construct.apply(this,arguments)
				}
			}
			//2
			//继承
			Parent = Parent || Object;
			F = function(){};
			F.prototype = Parent.prototype;
			Child.prototype = new F();
			Child.uber = Parent.prototype;
			Child.prototype.construct =Child;  
			//3
			//添加实现方法
			for(i in props){
				if(props.hasOwnProperty(i)){
					Child.prototype[i] = props[i];
				}
			}
			return Child;
		}
		klass()实现中三个令人关注且独特的部分:
		1.创建Child()构造函数。该函数将是最后返回的，并且该函数也用作类。在这个函数中，如果
		  存在_construct方法，那么将会调用该方法。另外，在此之前，通过使用静态uber属性，其父
		  类的_construct方法也会被自动调用（同样，如果存在改方法的话）。可能在有些情况下，当没
		  有定义uber属性时，比如直接从Object类中继承时，这与Man类的定义中继承时相似的情况。

		2.第二部分在一定程度上处理继承关系。它只是采用了本章前面章节中所讨论的类式继承的终极版。
		从代码上，只有一个新语句（Parent = Parent || Object），即如果没有传递需要被继承的类，那
		么就将Parent变为Object。

		3.最后一节是遍历所有的实现方法（比如，本例中的_construct和getName），这些是该类的实际定义，
		并且也是将它们添加到Child的原型中的部分代码。

```

- new过程

```
	对于 var o = new Foo();

	//JavaScript 实际上执行的是：
		var o = new Object();
		o.[[Prototype]] = Foo.prototype;
		Foo.call(o);
		在JS中,绝大多数的函数都是既可以调用也可以实例化的.我们既可以直接执行函数得到函数的返回值.也可以通过new操作符得到一个对象.
		在javascript中, 通过new可以产生原对象的一个实例对象，而这个实例对象继承了原对象的属性和方法。
		因此，new存在的意义在于它实现了javascript中的继承，而不仅仅是实例化了一个对象！
	new不new的区别：
		如果函数返回值为常规意义上的值类型（Number、String、Boolean）时，new函数将会返回一个该函数的实例对象，
		而如果函数返回一个引用类型（Object、Array、Function），则new函数与直接调用函数产生的结果等同。
```

- 对象的属性

```
	1.数据属性：4个特性[[Configurable]]、[[Enumerable]]、[[Writable]]、[[Value]] 
		例子：
		var person = {};
		Object.defineProperty(person,"name",{
			writable: false,
			value:"Jimmy"
		})
		alert(person.name); //"Jimmy"
		person.name = "Jason";
		alert(person.name)//Jimmy

		一旦配置了Configurable，就无法修改，尝试修改会在严格模式报错    
		var person = {};
		Object.defineProperty(person,"name",{
			configurable: false,
			value:"Jimmy"
		})
		//抛出错误
		var person = {};
		Object.defineProperty(person,"name",{
			configurable: true,
			value:"Jimmy"
		})

	2.访问器属性：4个特性[[Configurable]]、[[Enumerable]]、[[Get]]、[[Set]] 
		var book = {
			_year: 2014,
			edition；1
		};

		Object.defineProperty(book,"year",{
			get:function(){
				return this._year;
			},
			set: function(newValue){
				if(newValue > 2004){
					this._year = newValue;
					this.edition += newValue -2004;
				}
			}
		});
		book.year =2005;
		alert(book.edition);//2

	3.定义多属性：defineproperties

	4.读取属性：getOwnPropertyDescriptor
	
```

### 4.内置对象

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
		否  concat()	连接两个或更多的数组，并返回结果。  
		否  join()	把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。
		是  pop()	删除并返回数组的最后一个元素
		是  push()	向数组的末尾添加一个或更多元素，并返回新的长度。
		是  reverse()	颠倒数组中元素的顺序。
		是	shift()	删除并返回数组的第一个元素
		否	slice()	从某个已有的数组返回选定的元素
		是	sort()	对数组的元素进行排序
		是   splice()	删除元素，并向数组添加新元素。
			toSource()	返回该对象的源代码。
			toString()	把数组转换为字符串，并返回结果。
			toLocaleString()	把数组转换为本地数组，并返回结果。 
		是	unshift()	向数组的开头添加一个或更多元素，并返回新的长度。
			valueOf()	返回数组对象的原始值
```

- String

```
	方法	描述
	anchor()	创建 HTML 锚。
	big()	用大号字体显示字符串。
	blink()	显示闪动字符串。
	bold()	使用粗体显示字符串。
	charAt()	返回在指定位置的字符。
	charCodeAt()	返回在指定的位置的字符的 Unicode 编码。
	concat()	连接字符串。
	fixed()	以打字机文本显示字符串。
	fontcolor()	使用指定的颜色来显示字符串。
	fontsize()	使用指定的尺寸来显示字符串。
	fromCharCode()	从字符编码创建一个字符串。
	indexOf()	检索字符串。
	italics()	使用斜体显示字符串。
	lastIndexOf()	从后向前搜索字符串。
	link()	将字符串显示为链接。
	localeCompare()	用本地特定的顺序来比较两个字符串。
	match()	找到一个或多个正则表达式的匹配。
	replace()	替换与正则表达式匹配的子串。
	search()	检索与正则表达式相匹配的值。
	slice()	提取字符串的片断，并在新的字符串中返回被提取的部分。
	small()	使用小字号来显示字符串。
	split()	把字符串分割为字符串数组。
	strike()	使用删除线来显示字符串。
	sub()	把字符串显示为下标。
	substr()	从起始索引号提取字符串中指定数目的字符。
	substring()	提取字符串中两个指定的索引号之间的字符。
	sup()	把字符串显示为上标。
	toLocaleLowerCase()	把字符串转换为小写。
	toLocaleUpperCase()	把字符串转换为大写。
	toLowerCase()	把字符串转换为小写。
	toUpperCase()	把字符串转换为大写。
	toSource()	代表对象的源代码。
	toString()	返回字符串。
	valueOf()	返回某个字符串对象的原始值。
```

- Date

```
	var cur = new Date();
	ES5 新增了Date.now()可以获取当前时间的毫秒数
	常用方法 
	getFullYear() 取得4位数年份
	getMonth() 返回月份 从0开始
	getDate() 返回日期月份中的天数（1到31）
	getDay() 返回星期几（0是周日，6是周六）
	getHours() 小时（0-23）
	getMinutes() 分钟（0-59）
	getSeconds() 秒（0-59）

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

### 5.[正则](https://github.com/wenkangzhou/RegularExpression)

### 6.[ES6](http://es6.ruanyifeng.com/)


## WEB API

### 1.DOM API

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
	PS:效率不如innerHTML
```

- insertAdjacentHTML

```
	element.insertAdjacentHTML(position, text);
	1.beforeBegin: 插入到标签开始前
	2.afterBegin:插入到标签开始标记之后
	3.beforeEnd:插入到标签结束标记前
	4.afterEnd:插入到标签结束标记后
	var d1 = document.getElementById('one');
	d1.insertAdjacentHTML('afterend', '<div id="two">two</div>');
	// At this point, the new structure is:
	// <div id="one">one</div><div id="two">two</div>
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

- NodeType 

```
	.nodeType .nodeName
	节点操作
	appendChild()
	insertBefore()
	replaceChild()
	removeChild()
	cloneNode()//true、false深、浅复制
	节点关系
	childNodes
	firstChild
	lastChild
	parentNode
	nextSibling
	previousSibling

	Node类型(nodeType)
	Node.ELEMENT_NODE 1
		HTML
			HTMLElement:
				id
				title
				lang 元素语言代码
				dir
				className
			var div = document.getElementById("div")
			alert(div.id)
			alert(div.className)
			....
		取得特性
			var div = document.getElementById("div")
			document.getAttribute("id")
			document.getAttribute("class")
			document.getAttribute("title")
		var a = document.getElementsByTagNames("*");
		for(var i in a){
			if(a[i].nodeType == 1){
				console.log(a[i].getAttribute("class"))
			}
		}
		设置特性
			document.setAttribute("id",'111')
		删除特性
			document.removeAttribute("id")
		attributes
			Element类型是使用attributes属性唯一一个DOM节点类型
			attributes属性包含一个NamedNodeMap，与NodeList类似
			元素每个特性都由一个Attr节点表示
			每个节点保存在NamedNodeMap，NameNodeMap：
				getNamedItem(name) 返回nodeName属性等于name的节点
				removeNamedItem(name) 列表中移除nodeName属性等于name
				setNamedItem(node) 列表添加节点，节点的nodeName为索引
				item(pos) 返回数字pos处的节点
			var value = element.attributes.getNamedItem("id").nodeValue
			相当于 element.getAttribute("id")
			var name = element.attributes.getNamedItem("id").nodeName
		创建元素 
			document.createElement
	Node.ATTRIBUTE_NODE 2
		Attr元素特性，对应三个属性
			name 特性名称
			value 特性值
			specified 区别特性是在代码中指定的
		var attr = document.createAttribute("align")
		attr.value = "left"
		element.setAttributeNode(attr)
		alert(elemnt.attributes["align"].value)//left
		alert(elemnt.getAttributeNode("align").value)//left
		alert(elemnt.getAttribute("align"))//left
	Node.TEXT_NODE 3
		document.createTextNode
		normalize()//合并相邻文本节点
		splitText()//将一个文本节点拆分成两个文本节点
	Node.CDATA_SECTION_NODE 4
	Node.ENTITY_REFERENCE_NODE 5
	Node.ENTITY_NODE 6
	Node.PROCESSING_INSTRUCTION_NODE 7
	Node.COMMENT_NODE 8
	Node.DOCUMENT_NODE 9
		document是HTMLDocument（继承自Document类型）的实例
		document.documentElement//取得对<html>的引用
		document.body//取得对<body>的引用
		查找元素
			getElementById
			getElementsByTagName
				NodeList
				document.getElementByTagName(),返回HTMLCollection对象
				<img src="xx.jpg" name="myImg">
				var images = document.getElementByTagName("img")
				images[0].src images.item(0).src
				var myImg = images.namedItem("myImg")
				images["myImg"]
	Node.DOCUMENT_TYPE_NODE 10
		<DOCTYPE　HTML>
	Node.DOCUMENT_FRAGMENT_NODE 11
		document.createDocumentFragment
	Node.NOTATION_NODE 12
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
		扩展：event.preventDefault()方法是用于取消事件的默认行为，例如，当点击提交按钮时阻止对表单的提交
		
	(2) DOM事件三个阶段	
		1.捕获阶段：先由文档的根节点document往事件触发对象，从外向内捕获事件对象；
		2.目标阶段：到达目标事件位置（事发地），触发事件；
		3.冒泡阶段：再从目标事件位置往文档的根节点方向回溯，从内向外冒泡事件对象。
    (3) addEventListener/removeEventListener/attachEvent/detachEvent
        var addMyEvent = function (el,ev,fn){
            if(el.addEventListener){
                el.addEventListener(ev,fn,false)
            }else if(el.attachEvent){
                el.attachEvent("on"+ev,fn)
            }else{
                el["on" + ev] = fn;
            }
        }
    (4) createEvent/dispatchEvent
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

### 2.CSSDOM

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
        getClientRects返回的其实是个数组，数组中有很多个类似getBoundingClientRect返回的对象。
		getBoundingClientRect返回的永远是最外框框的那个矩形区域相关的坐标偏移对象；
		而getClientRects是多行文字区域的坐标偏移集合，在非IE浏览器下，只对inline的标签有反应。
        一般getBoundingClientRect方法用的多一点。我们可以很容易获取某个元素的偏移值。甚至高宽都能很轻松的计算出来。
		所以，下载你想用js获取元素的高宽尺寸，就可以试试getBoundingClientRect方法了。
        对getClientRects和getBoundingClientRect可以得到一个更好的说明.
        getClientRects 返回一个TextRectangle集合，就是TextRectangleList对象。
        getBoundingClientRect 返回 一个TextRectangle对象。
        那么这个TextRectangle对象有什么用呢，用来开判断文本是否换行！或者说用来获取矩形区域相关的坐标偏移对象！
        TextRectangle数组的长度可知道文字是否换行，甚至是换了几行，
        TextRectangle的几个属性和鼠标位置比较可以知道鼠标在哪一行上
```

### 3.canvas

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
### 4.BOM

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
	只读整数。声明了窗口的左上角在屏幕上的的 x 坐标和 y 坐标。IE、Safari 和 Opera 支持 screenLeft 和 screenTop，
	而 Firefox 和 Safari 支持screenX 和 screenY。
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
	HTML5加入history.pushState
		history.state
			当前URL下对应的状态信息。如果当前URL不是通过pushState或者replaceState产生的，那么history.state是null。
		history.pushState(state, title, url)
			将当前URL和history.state加入到history中，并用新的state和URL替换当前。不会造成页面刷新。
			state：与要跳转到的URL对应的状态信息。
			title：不知道干啥用，传空字符串就行了。
			url：要跳转到的URL地址，不能跨域。
		history.replaceState
			用新的state和URL替换当前。不会造成页面刷新。
			state：与要跳转到的URL对应的状态信息。
			title：不知道干啥用，传空字符串就行了。
			url：要跳转到的URL地址，不能跨域。
		window.onpopstate
			history.go和history.back（包括用户按浏览器历史前进后退按钮）触发，
			并且页面无刷的时候（由于使用pushState修改了history）会触发popstate事件，
			事件发生时浏览器会从history中取出URL和对应的state对象替换当前的URL和history.state。
			通过event.state也可以获取history.state。
```

## HTTP

### 1.状态码

```
    1XX：信息状态码
        100 Continue：客户端应当继续发送请求。这个临时相应是用来通知客户端它的部分请求已经被服务器接收，且仍未被拒绝。
					  客户端应当继续发送请求的剩余部分，或者如果请求已经完成，忽略这个响应。服务器必须在请求万仇向客户端发送一个最终响应
        101 Switching Protocols：服务器已经理解力客户端的请求，并将通过Upgrade消息头通知客户端采用不同的协议来完成这个请求。
								 在发送完这个响应最后的空行后，服务器将会切换到Upgrade消息头中定义的那些协议。
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
        302 Found：暂时的重定向
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
### 2.头

```
    Access-Control-Allow-Origin:* 支持跨域
    常见的request
        GET /Protocols/rfc2616/rfc2616-sec5.html HTTP/1.1
        Host: www.w3.org
        Connection: keep-alive
        Cache-Control: max-age=0
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
        User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.153Safari/537.36
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
        13、 ETag：就是一个对象（比如URL）的标志值，就一个对象而言，比如一个 html 文件，如果被修改了，其 Etag 也会别修改，
		           所以ETag 的作用跟Last-Modified 的作用差不多，主要供 WEB 服务器判断一个对象是否改变了。
				   比如前一次请求某个 html 文件时，获得了其 ETag，当这次又请求这个文件时，浏览器就会把先前获得的 ETag 值发送给WEB 服务器，
				   然后 WEB 服务器会把这个 ETag 跟该文件的当前 ETag 进行对比，然后就知道这个文件有没有改变了。
        14、 Expired：WEB服务器表明该实体将在什么时候过期，对于过期了的对象，只有在跟WEB服务器验证了其有效性后，才能用来响应客户请求。
		              是HTTP/1.0的头部。例如：Expires：Sat, 23 May 2009 10:02:12 GMT
        15、 Host：客户端指定自己想访问的WEB服务器的域名/IP 地址和端口号。例如：Host：rss.sina.com.cn
        16、 If-Match：如果对象的 ETag 没有改变，其实也就意味著对象没有改变，才执行请求的动作。
        17、If-None-Match：如果对象的 ETag 改变了，其实也就意味著对象也改变了，才执行请求的动作。
        18、 If-Modified-Since：如果请求的对象在该头部指定的时间之后修改了，才执行请求的动作（比如返回对象），否则返回代码304，
		                       告诉浏览器该对象没有修改。例如：If-Modified-Since：Thu, 10 Apr 2008 09:14:42 GMT
        19、If-Unmodified-Since：如果请求的对象在该头部指定的时间之后没修改过，才执行请求的动作（比如返回对象）。
        20、 If-Range：浏览器告诉 WEB 服务器，如果我请求的对象没有改变，就把我缺少的部分给我，如果对象改变了，就把整个对象给我。
					  浏览器通过发送请求对象的 ETag 或者 自己所知道的最后修改时间给 WEB 服务器，让其判断对象是否改变了。总是跟 Range 头部一起使用。
        21、 Last-Modified：WEB 服务器认为对象的最后修改时间，比如文件的最后修改时间，动态页面的最后产生时间等等。
		                   例如：Last-Modified：Tue,06May 2008 02:42:43 GMT
        22、 Location：WEB 服务器告诉浏览器，试图访问的对象已经被移到别的位置了，到该头部指定的位置去取。
		               例如：Location： http://i0.sinaimg.cn/dy/deco/2008/0528/sinahome_0803_ws_005_text_0.gif
        23、 Pramga：主要使用 Pramga: no-cache，相当于 Cache-Control： no-cache。例如：Pragma：no-cache
        24、 Proxy-Authenticate： 代理服务器响应浏览器，要求其提供代理身份验证信息。Proxy-Authorization：浏览器响应代理服务器的身份验证请求，提供自己的身份信息。
        25、 Range：浏览器（比如 Flashget 多线程下载时）告诉 WEB 服务器自己想取对象的哪部分。例如：Range: bytes=1173546-
        26、 Referer：浏览器向 WEB 服务器表明自己是从哪个 网页/URL 获得/点击 当前请求中的网址/URL。例如：Referer：http://www.sina.com/
        27、 Server: WEB 服务器表明自己是什么软件及版本等信息。例如：Server：Apache/2.0.61 (Unix)
        28、 User-Agent: 浏览器表明自己的身份（是哪种浏览器）。例如：User-Agent：Mozilla/5.0 (Windows; U; Windows NT 5.1; zh-CN;rv:1.8.1.14) Gecko/20080404 Firefox/2、0、0、14
        29、 Transfer-Encoding: WEB 服务器表明自己对本响应消息体（不是消息体里面的对象）作了怎样的编码，比如是否分块（chunked）。例如：Transfer-Encoding: chunked
        30、 Vary: WEB服务器用该头部的内容告诉 Cache 服务器，在什么条件下才能用本响应所返回的对象响应后续的请求。
		           假如源WEB服务器在接到第一个请求消息时，其响应消息的头部为：Content-Encoding: gzip; Vary: Content-Encoding
				   那么Cache 服务器会分析后续请求消息的头部，检查其Accept-Encoding，是否跟先前响应的 Vary 头部值一致，
				   即是否使用相同的内容编码方法，这样就可以防止 Cache 服务器用自己 Cache 里面压缩后的实体响应给不具备解压能力的浏览器。
				   例如：Vary：Accept-Encoding
        31、 Via： 列出从客户端到 OCS 或者相反方向的响应经过了哪些代理服务器，他们用什么协议（和版本）发送的请求。
		           当客户端请求到达第一个代理服务器时，该服务器会在自己发出的请求里面添加 Via 头部，并填上自己的相关信息，
				   当下一个代理服务器收到第一个代理服务器的请求时，会在自己发出的请求里面复制前一个代理服务器的请求的Via 头部，
				   并把自己的相关信息加到后面，以此类推，当 OCS 收到最后一个代理服务器的请求时，检查 Via 头部，就知道该请求所经过的路由。
				   例如：Via：1.0 236.D0707195.sina.com.cn:80 (squid/2.6.STABLE13)
```

### 3.方法

```
    一台服务器要与HTTP1.1兼容，只要为资源实现GET和HEAD方法即可
    GET是最常用的方法，通常用于请求服务器发送某个资源。
    HEAD与GET类似，但服务器在响应中值返回首部，不返回实体的主体部分
    PUT让服务器用请求的主体部分来创建一个由所请求的URL命名的新文档，或者，如果那个URL已经存在的话，就用干这个主体替代它
    POST起初是用来向服务器输入数据的。实际上，通常会用它来支持HTML的表单。表单中填好的数据通常会被送给服务器，然后由服务器将其发送到要去的地方。
    TRACE会在目的服务器端发起一个环回诊断，最后一站的服务器会弹回一个TRACE响应并在响应主体中携带它收到的原始请求报文。
		 TRACE方法主要用于诊断，用于验证请求是否如愿穿过了请求/响应链。
    OPTIONS方法请求web服务器告知其支持的各种功能。可以查询服务器支持哪些方法或者对某些特殊资源支持哪些方法。
    DELETE请求服务器删除请求URL指定的资源
```
## 常见框架

### 1.vue

### 2.react

```
	https://github.com/bailicangdu/react-pxq
	
	React 是什么
		用脚本进行DOM操作的代价很昂贵。有个贴切的比喻，把DOM和JavaScript各自想象为一个岛屿，它们之间用收费桥梁连接，js每次访问DOM，
		都要途径这座桥，并交纳“过桥费”,访问DOM的次数越多，费用也就越高。
		因此，推荐的做法是尽量减少过桥的次数，努力待在ECMAScript岛上。
		因为这个原因react的虚拟dom就显得难能可贵了，它创造了虚拟dom并且将它们储存起来，每当状态发生变化的时候就会创造新的虚拟节点和以前的进行对比，
		让变化的部分进行渲染。整个过程没有对dom进行获取和操作，只有一个渲染的过程，所以react说是一个ui框架。
	React的 Diff算法
		react的diff算法用在什么地方呢？当组件更新的时候，react会创建一个新的虚拟dom树并且会和之前储存的dom树进行比较，
		这个比较多过程就用到了diff算法，所以组件初始化的时候是用不到的。
		react提出了一种假设，相同的节点具有类似的结构，而不同的节点具有不同的结构。
		在这种假设之上进行逐层的比较，如果发现对应的节点是不同的，那就直接删除旧的节点以及它所包含的所有子节点然后替换成新的节点。
		如果是相同的节点，则只进行属性的更改。对于列表的diff算法稍有不同，因为列表通常具有相同的结构，在对列表节点进行删除，插入，排序的时候，
		单个节点的整体操作远比一个个对比一个个替换要好得多，所以在创建列表的时候需要设置key值，这样react才能分清谁是谁。
		当然不写key值也可以，但这样通常会报出警告，通知我们加上key值以提高react的性能。
```

### 3.angular

## 模块化开发

### 1.AMD（RequireJS）

### 2.CMD（SeaJS）

### 3.CommonJS

```
	CommonJS就是为JS的表现来制定规范，NodeJS是这种规范的实现，webpack 也是以CommonJS的形式来书写。
		因为js没有模块的功能所以CommonJS应运而生，它希望js可以在任何地方运行，不只是浏览器中。它的终极目标是提供一个类似Python，Ruby和Java标准库。
	CommonJS定义的模块分为:{模块引用(require)} {模块定义(exports)} {模块标识(module)}
	require()用来引入外部模块；exports对象用于导出当前模块的方法或变量，唯一的导出口；module对象就代表模块本身。
	虽说Node遵循CommonJS的规范，但是相比也是做了一些取舍，填了一些新东西的。
	不过，说了CommonJS也说了Node，那么我觉得也得先了解下NPM了。NPM作为Node的包管理器，不是为了帮助Node解决依赖包的安装问题嘛，
	那它肯定也要遵循CommonJS规范啦，它遵循包规范（还是理论）的。
	CommonJS WIKI讲了它的历史，还介绍了modules和packages等。
```
### 4.UMD(通用模块)

```javascript
	var root = (window !== 'undefined' ? window : self);

	(function (global, factory) {

		'use strict';

		/* Use AMD */
		if (typeof define === 'function' && define.amd) {
			define(function () {
				return new (factory(global, global.document))();
			});
		}
		/* Use CommonJS */
		else if (typeof module !== 'undefined' && module.exports) {
			module.exports = (factory(global, global.document))();
		}
		/* Use Browser */
		else {
			global.Push = new (factory(global, global.document))();
		}

	})(root, function (w, d){})
```

### 5.区别

```
	1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。
	CMD 推崇 as lazy as possible.

	2. CMD 推崇依赖就近，AMD 推崇依赖前置。看代码：

	// CMD
	define(function(require, exports, module) {
	var a = require('./a')
	a.doSomething()
	// 此处略去 100 行
	var b = require('./b') // 依赖可以就近书写
	b.doSomething()
	// ... 
	})

	// AMD 默认推荐的是
	define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
	a.doSomething()
	// 此处略去 100 行
	b.doSomething()
	...
	}) 

	虽然 AMD 也支持 CMD 的写法，同时还支持将 require 作为依赖项传递，但 RequireJS 的作者默认是最喜欢上面的写法，也是官方文档里默认的模块定义写法。

	3. AMD 的 API 默认是一个当多个用，CMD 的 API 严格区分，推崇职责单一。比如 AMD 里，require 分全局 require 和局部 require，都叫require。
	   CMD 里，没有全局 require，而是根据模块系统的完备性，提供 seajs.use 来实现模块系统的加载启动。CMD 里，每个 API 都简单纯粹。
	4. UMD 通用模块适合前后端同构
```
## 构建工具

### 1.Grunt

### 2.Gulp

### 3.Webpack

### 4.区别

```
	Gulp应该和Grunt比较，他们的区别我就不说了，说说用处吧。Gulp / Grunt 是一种工具，能够优化前端工作流程。比如自动刷新页面、combo、压缩css、js、编译less等等。
	简单来说，就是使用Gulp/Grunt，然后配置你需要的插件，就可以把以前需要手工做的事情让它帮你做了。

	说到 browserify / webpack ，那还要说到 seajs / requirejs。这四个都是JS模块化的方案。其中seajs / require是一种类型，browserify / webpack是另一种类型。

	seajs / require : 是一种在线"编译" 模块的方案，相当于在页面上加载一个 CMD/AMD 解释器。这样浏览器就认识了 define、exports、module 这些东西。也就实现了模块化。

	browserify / webpack : 是一个预编译模块的方案，相比于上面 ，这个方案更加智能。没用过browserify，这里以webpack为例。首先，它是预编译的，不需要在浏览器中加载解释器。
	另外，你在本地直接写JS，不管是 AMD / CMD / ES6 风格的模块化，它都能认识，并且编译成浏览器认识的JS。
	这样就知道，Gulp是一个工具，而webpack等等是模块化方案。Gulp也可以配置seajs、requirejs甚至webpack的插件。
```


## 版本控制

### 1.Git

```
	https://github.com/wenkangzhou/GitCmd
```
### 2.Svn

```
	http://www.jianshu.com/p/786d225860cd
```

## [优化](https://aotu.io/notes/2016/03/16/optimization/)

### 1.雅虎

![](http://img.aotu.io/wangcainuan/2016-03-16-optimization/%E9%9B%85%E8%99%8E35%E6%9D%A1%E5%86%9B%E8%A7%84.jpg)

```
		
	content方面
		减少HTTP请求：合并文件、CSS精灵、inline Image
		减少DNS查询：DNS查询完成之前浏览器不能从这个主机下载任何任何文件。方法：DNS缓存、将资源分布到恰当数量的主机名，平衡并行下载和DNS查询
		避免重定向：多余的中间访问
		使Ajax可缓存
		非必须组件延迟加载
		未来所需组件预加载
		减少DOM元素数量
		将资源放到不同的域下：浏览器同时从一个域下载资源的数目有限，增加域可以提高并行下载量
		减少iframe数量
		不要404
	Server方面
		使用CDN
		添加Expires或者Cache-Control响应头
		对组件使用Gzip压缩
		配置ETag
		Flush Buffer Early
		Ajax使用GET进行请求
		避免空src的img标签
	Cookie方面
		减小cookie大小
		引入资源的域名不要包含cookie
	css方面
		将样式表放到页面顶部
		不使用CSS表达式
		使用不使用@import
		不使用IE的Filter
	Javascript方面
		将脚本放到页面底部
		将javascript和css从外部引入
		压缩javascript和css
		删除不需要的脚本
		减少DOM访问
		合理设计事件监听器
	图片方面
		优化图片：根据实际颜色需要选择色深、压缩
		优化css精灵
		不要在HTML中拉伸图片
		保证favicon.ico小并且可缓存
	移动方面
		保证组件小于25k
		Pack Components into a Multipart Document
```

### 2.More

```
	1.没事少烦我-服务端
		1.1 使用内容分发网络（Content Delivery Network，CDN）
			通过在现有的Internet中增加一层新的网络架构，将网站的内容发布到最接近用户的 cache服务器内，通过DNS负载均衡的技术，
			判断用户来源就近访问cache服务器取得所需的内容。深圳用户访问遥远的美国服务器，当然不理想了。
			把静态内容分布到CDN可以减少用户响应时间20%或更多。
		1.2 静态资源缓存，移动端离线缓存
			缓存利用可包括：添加 Expires 头，配置 ETag，使 Ajax 可缓存等。其实，恰当的缓存设置可以大大的减少 HTTP请求，也可以节省带宽 。
			1.2.1 配置 ETag：即If-None-Match: 上次 ETag 的内容。浏览器会发出请求询问服务端，资源是否过期；
			      服务端发现,没有过期，直接返回一个状态码为304、正文为空的响应，告知浏览器使用本地缓存；
				  如果资源有更新，服务端返回状态码 200、Etag 和正文。这个过程被称之为 HTTP 的协商缓存，通常也叫做弱缓存。
			1.2.2 添加 Expires 头：服务端通过响应头告诉浏览器，在什么时间之前（Expires）或在多长时间之内（Cache-Control: Max-age=xxx），
			      不要再请求服务器了。这个机制我们通常称之为 HTTP 的强缓存。一般会对 CSS、JS、图片等资源使用强缓存，
				  而入口文件（HTML）一般使用协商缓存或不缓存。
			1.2.3 AppCache：AppCache主要利用manifest 文本文件，告知浏览器被缓存的内容以及不缓存的内容。
			1.2.4 LocalStorage：用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
	2.省着点用-网络
		2.1 减少请求数
			可通过以下方式减少请求数：
				小图片合并雪碧图；
				JS、CSS文件选择性合并；
				避免重复的资源请求。
			减少请求数对于速度优化来说最重要最有效的，特别是网络差的用户。
			一个完整的请求需要经过域名解析以及DNS寻址、与服务器建立连接、发送数据、等待服务器响应、接收数据的过程；
			每个请求都需要携带数据，因此每个请求都需要占用带宽；浏览器进行并发请求的请求数是有上限的。
			请求多了的情况,明显增加了网页的响应时间。一个页面由多个模块拼接而成，几个模块中请求了同样的资源时，就会导致资源的重复请求。
		2.2 减少文件大小（减少请求带宽）
			压缩CSS、JS、图片；
			尽可能控制DOM节点数；
			精简css、 JavaScript，移除注释、空格、重复css和脚本。
			开启Gzip，Gzip的思想就是把文件先在服务器端进行压缩，且压缩率达到85%，然后再传输，传输完毕后浏览器会 重新对压缩过的内容进行解压缩，并执行。
			好处在于Gzip的支持已经很好，且爬虫可识别，压缩率达到66%-85%显著减少了文件传输的大小。另外，gzip对pdf文件的压缩效果不大，而且会浪费CPU。
		2.3 合理使用静态资源域名
			域名的要求是短小且独立。
			短小可以减少头部开销，因为域名越短请求头起始行的 URI 就越短。之所以要求独立，因为独立域名不会共享主域的 Cookie，可以有效减小请求头大小，
			这个策略一般称之为 Cookie-Free Domain；另外一个原因是浏览器对相同域名的并发连接数限制，一般允许同域名并发 6~8 个连接，
			域名不是越多越好，每个域名的第一个连接都要经历 DNS 查询（DNS Lookup），导致会耗费一定的时间，控制域名使用在2-4个之间。
			另外注意：同一静态资源在不同页面被散列到不同子域下，会导致无法利用 HTTP 缓存。
		2.4 使用HTTP 2
			HTTP 2 相比 HTTP 1.1 的更新大部分集中于：
			多路复用：多路复用很好地解决如何让重要资源尽快加载这个问题。同域名下或者不同域但是同时满足同一个IP以及使用同一个证书的这两个条件中的所有通信都在单个连接上完成，
					 此连接上同时打开任意数量的双向数据流（ HTTP 1.1 有连接数限制）。
					 使用多域名加上相同的 IP 和证书部署 Web 服务有特殊的意义：让支持 HTTP/2 的终端只建立一个连接，用上 HTTP/2 协议带来的各种好处；
					 而只支持 HTTP/1.1 的终端则会建立多个连接，达到同时更多并发请求的目的。
			HEAD 压缩：HTTP/2 将请求和响应数据分割为更小的帧，并对它们采用二进制编码（ Binary Framing ）。
					  在HTTP/1 中，HTTP 请求和响应都是由「状态行、请求 / 响应头部、消息主体」三部分组成，状态行和头部却没有经过任何压缩，
					  直接以纯文本传输。在 HTTP/2 中，每个数据流都以消息的形式发送，而消息又由一个或多个帧组成。
					  多个帧之间可以乱序发送，因为根据帧首部的流标识可以重新组装。
			请求优先级：服务器可以根据流的优先级，控制资源分配(CPU、内存、带宽)，而在响应数据准备好之后，优先将最高优先级的帧发送给客户端。
			服务器推送：启动Server Push，意味着服务端可以在发送页面HTML时主动推送其它资源，有自己独立的URL，可以被浏览器缓存；
					   如果服务端推送的资源已经被浏览器缓存过，浏览器可以通过发送 RST_STREAM 帧来拒收。
	3.学会持家，让家变得简洁漂亮-客户端
		3.1 使用外链CSS和JS，CSS放头，JS放尾，防止阻塞以减少对并发下载的影响，尽早刷新文档的输出。
		3.2 html的代码优化，如：
			避免空的图片src；
			协议自适应，减少html文件大小，将https://和http://都替换成//。
		3.3 css的代码优化，如：
			建议使用类选择器，访问比较快；
			不建议使用很长的base64；
			避免CSS表达式；
			避免使用Filters。
		3.4 js的代码优化，如：
			避免使用eval和width；
			减少作用域链查找；
			减少DOM访问，尽量缓存DOM；
			充分利用事件委托；
			减少Repaint（重绘）和Reflow（重排）最好通过批量更新元素减少重排次数，如设置类class统一更新样式，在添加多个li
			元素将会触发多次页面重排的情况下使用 DOM fargment 在内存中创建完整的 DOM 节点，然后再一次性添加到 DOM 中。
		3.5 图片格式的选择：
			颜色较为丰富的图片而且文件比较大的（40KB - 200KB）或者有内容的图片优先考虑 jpg；图标等颜色比较简单、文件体积不大、起修饰作用的图片，
			优先考虑使用 PNG8 格式；图像颜色丰富而且图片文件不太大的（40KB 以下）或有半透明效果的优先考虑 PNG24 格式。
			条件允许的，使用新格式WEBP和BPG。
			用SVG和ICONFONT代替简单的图标。
			颜色较为丰富的图片而且文件比较大的（40KB - 200KB）或者有内容的图片优先考虑 jpg；图标等颜色比较简单、文件体积不大、起修饰作用的图片，
			优先考虑使用 PNG8 格式；图像颜色丰富而且图片文件不太大的（40KB 以下）或有半透明效果的优先考虑 PNG24 格式。			
			用「字蛛」来代替艺术字体切图，它可剔除没有使用的字符，从而解决中文字体过大的问题，并编码成跨平台兼容的格式。
		3.6 合理分配资源加载时间，按需加载，包括CSS、JS文件以及图片、业务模块等。
			根据我们网页最初加载需要的最小内容集推断其他内容延迟加载；无条件提前加载公共内容或根据用户行为推断提前加载某些内容，
			如根据搜索框输入的文字来判断加载的内容。加载机制如下：
				预加载
				Dom Ready后加载
				onLoad后加载
				滚动加载
		3.7 减少DNS 查询：DNS 查询一般需要几毫秒到几百毫秒，移动环境下会更慢。我们可以预先读取DNS，减少用户等待时间。
```
### 3.稳定性

```
	稳定性的第一要求是可用。最起码的要求是页面得出来，要不然没法用了。
	其次讲究的是页面的可维护性，假如页面挂了，多久可以恢复过来，另外考虑页面挂的期间是否可以采取静态页面处理等方式。
	页面的稳定性其实和前端安全挂钩，即使页面可以出来了，但是不能保证不会被黑掉，下文从前端安全的方面讲解。
	3.1 常见攻击：
		XSS (Cross Site Script) ，跨站脚本攻击，往Web页面里插入恶意html代码。特点是攻击者的代码必须能获取用户浏览器端的执行权限，
		要杜绝此类攻击出现可以在入口和出口进行严格的过滤。
			三种类型：
				（1） 反射型XSS：一次性；将包含注入脚本的恶意链接发送给受害者。
				（2） 持久型XSS：用户输入的数据“存储”在服务器端，比如一条包含XSS代码的留言。
				（3） DOM XSS：使用一些eval等有输出的语句意味着多了一份被XSS的风险。
			应对策略：
				当恶意代码值被作为某一标签的内容显示：在不需要html输入的地方对html 标签及一些特殊字符( ” < > & 等等 )做过滤，
				将其转化为不被浏览器解释执行的字符。
				当恶意代码被作为某一标签的属性显示，通过用 “将属性截断来开辟新的属性或恶意方法：属性本身存在的 单引号和双引号都需要进行转码；
				对用户输入的html 标签及标签属性做白名单过滤，也可以对一些存在漏洞的标签和属性进行专门过滤。
		CSRF(Cross Site Request Forgery)，跨站点伪造请求，
			通过伪造连接请求在用户不知情的情况下，让用户以自己的身份来完成攻击者需要达到的一些目的。
		XSS是你访问正常网站的时候，你浏览器执行了攻击者的代码。有XSS的网站可以直接伪造请求，比CSRF强多了。
        CSRF是你点击了攻击者提供的链接的时候（正常网站或其它有攻击者代码的网站），你的浏览器向正常网站发送攻击者期望的请求。	
		cookie劫持
			通过获取页面的权限，在页面中写一个简单的到恶意站点的请求，并获取用户的cookie登录某些站点。
		对于crsf 和cookie 劫持的策略：
			通过 referer、token 或者 验证码 来检测用户提交。
			尽量不要在页面的链接中暴露用户隐私信息。
			对于用户修改删除等操作最好都使用post 操作 。
			避免全站通用的cookie，严格设置cookie的域。
	3.2 数据通道安全
		国内的众多网站都没有实现全站HTTPS。这是目前为止最重要的一步，所有的数据在发送之前就会被加密，攻击者无法查看或篡改数据包的内容。
		HTTPS可以理解为HTTP+SSL/TLS，通过数据加密、校验数据完整性和身份认证三种机制来保障安全。
		HTTPS的缺点是网站在加上TLS证书时，可能导致RTT往返时延增加，并且 HTTPS通信过程的非对称和对称加解密计算会产生更多的服务器性能和时间上的消耗，
		但是这是可以优化的，这里就不细说了。
	3.3 浏览器安全
		3.3.1 同源策略
			首先了解一下同源策略：
				源指的是有相同的HOST、相同的协议、相同的端口。
				同源策略以源为单位，把资源天然分隔，保护了用户的信息安全。
				绕过同源策略让javascript访问其他源的资源的方法，如：JSONP、CORS、flash等。
				同源策略不是绝对安全的，面对很多攻击是无能为力的，比如XSS，因为此时攻击者就在同源之内。
			不建议使用JSONP，因为JSONP通常在脚本中写一个回调函数，然后把回调函数的名字写在请求的URL中，因此如果请求数据的服务器被黑了，
			那么黑客就能在返回的数据中植入恶意代码，从而窃取用户的隐私信息。
			跨域资源共享CORS允许资源提供方在响应头中加入一个特殊的标记，使你能通过XHR来获取、解析并验证数据。这样就能避免恶意代码在你的应用中执行。
			在响应头中加入的标记如下：
				Access-Control-Allow-Origin: allowed origins
			如果对Access–Control-Allow-Origin设置为*其实是比较危险的，如果没有携带会话认证意味着信息被公开在全网，建议设置具体的域名，
			而且跨域的时候记得带上session id；严格审查请求信息，比如请求参数，还有http头信息，因为 http头可以伪造。
		3.3.2 CSP(Content Security Policy)
			CSP指定网站上所有脚本和图片等资源的源站点，也能阻止所有内联（inline）的脚本和样式。即使有人在页面评论或者留言中嵌入了脚本标签，
			这些脚本代码也不会被执行。可通过两种方式设置，如果 HTTP 头与 Meta 定义同时存在，则优先采用 HTTP 头中的定义：
				通过 HTTP 头，比如只允许脚本从本源加载：Content-Security-Policy: script-src ‘self’，其中script-src ‘self’是策略。
				通过HTML的Meta标签，比如只允许脚本从本源加载：
				<meta http-equiv="Content-Security-Policy" content="script-src 'self'">
			其他策略：
				script-src – 设置可以接受的JavaScript代码的源站点
				style-src – 设置可以接受的CSS样式代码的源站点
				connect-src – 定义浏览器可以通过XHR、WebSocket或者 EventSource访问哪些站点
				font-src – 设置可以接受的字体文件的源站点
				frame-src – 定义浏览器可以通过iframe访问哪些站点
				img-src – 设置可以接受的图片的源站点
				media-src – 设置可以接受的音频和视频文件的源站点
				object-src – 设置可以接受的Flash和其它插件的源站点
				缺点：
				默认情况下，所有的内联JavaScript脚本都不会被执行，因为浏览器无法区分自己的内联脚本和黑客注入的脚本。
				CSP还会默认阻止所有eval()风格的代码的执行，包括setInterval/setTimeout中的字符串和类似于new Function(‘return false’)之类的代码。
		3.3.3 iframe 沙箱环境
			利用iframe进行跨源：HTML5为iframe提供了安全属性 sandbox，iframe的能力将会被限制。
		3.3.4 Secure和HttpOnly属性
			Seure能确保cookie的内容只能通过SSL连接进行传输。Secure和HttpOnly属性告诉浏览器cookie的内容只能分别通过HTTP(S)协议进行访问，
			从而避免了被轻易窃取，比如禁止从JavaScript中的document.cookie访问，因此cookie在浏览器document中不可见了。
			如果单独使用的话，无法全面抵御跨站点脚本攻击，通常和其他技术组合使用。使用方法如下：
			Set-Cookie: <name>=<value>[; <name>=<value>] [; expires=<date>][; domain=<domain_name>][; path=<some_path>][;secure][; HttpOnly]
		3.3.5 其他安全相关的HTTP头
			X-Content-Type-Options 告诉浏览器相信此服务器下发的资源的类型，防止类型嗅探攻击。
			HPKP(Public Key Pinning) Public Key Pinning 是一个response 头，用来检测一个证书的公钥是否发生了改变，防止中间人攻击。
			HSTS (HTTP Strict-Transport-Security) 强制使用TSL作为数据通道。
	3.4 HTML5 对web安全的影响
		html5有很多新的特性能力，然而能力越大，被攻破后的危险就越大。
		HTML5 对xss的影响主要体现在:
			攻击面更大，html5带来更多的标签和更多的属性如<video>,<audio>,<canvas>等；
			危害更大，HTML5更多的资源可以被xss利用。黑客可以利用浏览器的一切权限，比如本地存储、GEO、服务器推送机制WebSocket，js多线程执行Webworker等。
			比如localstorage只能通过js设置和获取，导致的结果是不能像cookie一样设置httponly等属性，所以localstorage中不能存放敏感信息，
			最好能够在服务端进行加密，可以配合CORS来获取网站的localstorage的信息。
```

### 4.响应式

```
	基于栅格布局规划响应式设计，每个模块尽可能严格遵循栅格布局，符合栅格的小模块能很灵活的适应多个分辨率的展示。
	拥抱flexbox。
	使用动态的字体大小单位+rem单位使用。
	使用CSS3 mediaQuery 技术响应用户设备。
	利用百分比。
	对低版本浏览器使用JS动态响应。
	一套“自适应”素材兼容各种分辨率，提升页面性能，比如自适应的图片/视频素材。
```

### 5.搜索SEO

```
	1 语义化
		标签语义化对搜索引擎友好，良好的结构和语义容易被搜索引擎抓取。
		善用标题h1，h2，h3，h4，h5，h6，特别是h1和h2；H(x)标签中使用关键字，可提升排名。同时设置 rel=“nofollow”避免权重流失。
		使用 HTML5 中的 Microdata 对 Web 页面上已经存在的数据提供附加的语义。Microdata 由名字 / 值（name/value）对组成，每一个词汇表定义一组命名的属性。
		对 Microdata 的支持可以影响搜索结果的显示，使得显示结果更加丰富，虽然不能影响搜索结果的排名，但是网站的流量可能会有所增加。
		类似的技术还有资源描述框架RDF、微格式Microformat 。
	2 衡量站点关键词优化
		站点内容以及关键词的选择。
		描述标签、关键词标签、代替属性。
		长尾关键词：非目标关键词但也可以带来搜索流量的关键词；例如，目标关键词是服装，其长尾关键词可以是男士服装、冬装、户外运动装等。
				   长尾关键词基本属性是：可延伸性，针对性强，范围广。
		关键词的分布情况。
		关键词密度、看重：合理的关键字密度可获得较高的排名位置，密度过大会起到相反的效果。一般说来，在大多数的搜索引擎中，
		关键词密度在2%~8%是一个较为适当的范围，有利于网站在搜索引擎中排名。
		是否存在作弊行为。
	3 链接
		优化文件目录结构和URL。URL应该有语义性，简短易懂。
		通过推广暴露自己的链接，增加信任度。链接分为外向链接和内向（反向）链接，外向链接就是从本站点到其他站点，内向链接就是从其他站点到我的站点，
		可以尝试使用反向链接生成器。或者通过写软文、发布分类信息、发布博客文章来推广自己的网站。
		锚文本 ：把关键词做一个链接，指向别的网页，这种形式的链接就叫作锚文本。搜索引擎可以根据指向某一个网页的链接的锚文本描述来判断该网页的内容属性。
	4 良好的网站导航和sitemap
		网站需要有一个良好的导航，控制根目录和各子目录的关键，通过sitemap可以帮助网站主了解网站结构，也方便搜索引擎收录整个站点。
```

## 算法

### 1.[排序](http://www.jianshu.com/p/7e6589306a27)

```
	1.插入排序
		// 插入排序 从下标1开始每增1项排序一次，越往后遍历次数越多
		function sort1(array) {
		  var len = array.length,
			  i, j, tmp, result;

		  // 设置数组副本
		  result = array.slice(0);
		  for(i=1; i < len; i++){
			tmp = result[i];
			j = i - 1;
			while(j>=0 && tmp < result[j]){
			  result[j+1] = result[j];
			  j--;
			}
			result[j+1] = tmp;
		  }
		  return result;
		}
	2.二分插入排序
		// 先在有序区通过二分查找的方法找到移动元素的起始位置，
		// 然后通过这个起始位置将后面所有的元素后移
		function sort2(array) {
		  var len = array.length,
			  i, j, tmp, low, high, mid, result;
		  // 赋予数组副本
		  result = array.slice(0);
		  for(i = 1; i < len; i++){
			tmp = result[i];
			low = 0;
			high = i - 1;
			while(low <= high){
			  mid = parseInt((low + high)/2, 10);
			  if(tmp < result[mid]) high = mid - 1;
			  else low = mid + 1;
			}
			for(j = i - 1; j >= high+1; j--){
			  result[j+1] = result[j];            
			}
			result[j+1] = tmp;
		  }
		  return result;
		}
	3.希尔排序
		// 希尔排序：先将整个待排序记录序列分割成若干个子序列
		// 在序列内分别进行直接插入排序，待整个序列基本有序时，
		// 再对全体记录进行一次直接插入排序
		function sort3(array){
		  var len = array.length, gap = parseInt(len/2), 
			  i, j, tmp, result;
		  // 复制数组
		  result = array.slice(0);
		  while(gap > 0){
			for(i = gap; i < len; i++){
			  tmp = result[i];
			  j = i - gap;
			  while(j>=0 && tmp < result[j]){
				result[j + gap] = result[j];
				j = j - gap;
			  }
			  result[j + gap] = tmp;
			}
			gap = parseInt(gap/2);
		  }
		  return result;
		}
	4.冒泡排序
		// 冒泡排序 每次将最小元素推至最前
		function sort4(array) {
		  var len = array.length,
		  i, j, tmp, result;
		  result = array.slice(0);
		  for (i = 0; i < len; i++) {
			for (j = len - 1; j > i; j--) {
			  if (result[j] < result[j - 1]) {
				tmp = result[j - 1];
				result[j - 1] = result[j];
				result[j] = tmp;
			  }
			}
		  }
		  return result;
		}
	5.改进冒泡排序
		// 如果在某次的排序中没有出现交换的情况，
		// 那么说明在无序的元素现在已经是有序了，就可以直接返回了。
		function sort5(array) {
		  var len = array.length,
		  i, j, tmp, exchange, result;

		  result = array.slice(0);
		  for (i = 0; i < len; i++) {
			exchange = 0;
			for (j = len - 1; j > i; j--) {
			  if (result[j] < result[j - 1]) {
				tmp = result[j];
				result[j] = result[j - 1];
				result[j - 1] = tmp;
				exchange = 1;
			  }
			}
			if (!exchange) return result;
		  }
		  return result;
		}
	6.快速排序
		//（1）在数据集之中，选择一个元素作为"基准"（pivot）。
		//（2）所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边。
		//（3）对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止。
		function sort6(array) {
		  var tmp_array = array.slice(0), result,
		  quickSort = function(arr) {
		  if (arr.length <= 1) { return arr; }
		  var pivotIndex = Math.floor(arr.length / 2);
		  var pivot = arr.splice(pivotIndex, 1)[0];
		  var left = [];
		  var right = [];
		  for (var i = 0; i < arr.length; i++){
			if (arr[i] < pivot) {
			  left.push(arr[i]);
			} else {
			  right.push(arr[i]);
			}
		  }
		  return quickSort(left).concat([pivot], quickSort(right));
		  };
		  result = quickSort(tmp_array);
		  return result;
		}
	7.选择排序
		// 在无序区中选出最小的元素，然后将它和无序区的第一个元素交换位置。
		// 原理跟冒泡排序一样，算是冒泡的衍生版本
		function sort7(array) {
		  var len = array.length,
		  i, j, k, tmp, result;

		  result = array.slice(0);
		  for (i = 0; i < len; i++) {
			k = i;
			for (j = i + 1; j < len; j++) {
			  if (result[j] < result[k]) k = j;
			}
			if (k != i) {
			  tmp = result[k];
			  result[k] = result[i];
			  result[i] = tmp;
			}
		  }
		  return result;
		}
	8.堆排序
		// 1) 初始堆：将原始数组调整成大根堆的方法——筛选算法:子节点都比父节点小
		// 2) 堆排序： 每次将堆顶元素与数组最后面的且没有被置换的元素互换。
		// 参考代码： http://bubkoo.com/2014/01/14/sort-algorithm/heap-sort/
		function sort8(array) {
		  var result = array.slice(0);

		  function swap(array, i, j) {
			var temp = array[i];
			array[i] = array[j];
			array[j] = temp;
		  }

		  function maxHeapify(array, index, heapSize) {
			var iMax, iLeft, iRight;
			while (true) {
			  iMax = index;
			  iLeft = 2 * index + 1;
			  iRight = 2 * (index + 1);

			  if (iLeft < heapSize && array[index] < array[iLeft]) {
				iMax = iLeft;
			  }

			  if (iRight < heapSize && array[iMax] < array[iRight]) {
				iMax = iRight;
			  }

			  if (iMax != index) {
				swap(array, iMax, index);
				index = iMax;
			  } else {
				break;
			  }
			}
		  }

		  function buildMaxHeap(array) {
			var i, iParent = Math.floor(array.length / 2) - 1;

			for (i = iParent; i >= 0; i--) {
			  maxHeapify(array, i, array.length);
			}
		  }

		  function sort(array) {
			buildMaxHeap(array);

			for (var i = array.length - 1; i > 0; i--) {
			  swap(array, 0, i);
			  maxHeapify(array, 0, i);
			}
			return array;
		  }

		  return sort(result);
		}
	9.归并排序
		// 合并排序：将无序的数组 拆成N部分进行有序处理，然后合并；
		// 参考代码： https://gist.github.com/paullewis/1982121
		function sort9(array) {
		  var result = array.slice(0);

		  // 递归调用合并函数
		  function sort(array) {
			var length = array.length,
			mid = Math.floor(length * 0.5),
			left = array.slice(0, mid),
			right = array.slice(mid, length);

			if (length === 1) {
			  return array;
			}
			return merge(sort(left), sort(right));
		  }

		  // 合并 两有序的数组
		  function merge(left, right) {
			var result = [];

			while (left.length || right.length) {

			  if (left.length && right.length) {

				if (left[0] < right[0]) {
				  result.push(left.shift());
				} else {
				  result.push(right.shift());
				}

			  } else if (left.length) {
				result.push(left.shift());
			  } else {
				result.push(right.shift());
			  }
			}
			return result;
		  }

		  return sort(result);
		}
	10.全排序
		<script type="text/javascript">  
		/*  
		全排列（递归交换）算法  
		1、将第一个位置分别放置各个不同的元素；  
		2、对剩余的位置进行全排列（递归）；  
		3、递归出口为只对一个元素进行全排列。  
		*/ 
		function swap(arr,i,j) {  
			if(i!=j) {  
				var temp=arr[i];  
				arr[i]=arr[j];  
				arr[j]=temp;  
			}  
		}  
		var count=0;  
		function show(arr) {  
			document.write("P<sub>"+ ++count+"</sub>: "+arr+"<br />");  
		}  
		function perm(arr) {  
			(function fn(n) { //为第n个位置选择元素  
				for(var i=n;i<arr.length;i++) {  
					swap(arr,i,n);  
					if(n+1<arr.length-1) //判断数组中剩余的待全排列的元素是否大于1个  
						fn(n+1); //从第n+1个下标进行全排列  
					else 
						show(arr); //显示一组结果  
					swap(arr,i,n);  
				}  
			})(0);  
		}  
		perm(["e1","e2","e3","e4"]);  
		</script>  
```

### 2.搜索

```
	1.二分搜索
		function binarySearch(data, dest, start, end){  
			var end = end || data.length - 1,  
				start = start || 0,  
				m = Math.floor((start + end) / 2);  
			if(data[m] == dest){  
				return m;  
			}  
			if(dest < data[m]){  
				return binarySearch(data, dest, 0, m-1);  
			}else{  
				return binarySearch(data, dest, m+1, end);  
			}  

			return false;  
		}  
		var arr = [-34, 1, 3, 4, 5, 8, 34, 45, 65, 87];  
		binarySearch(arr,4);  
```

### 3.[动态规划](http://blog.jobbole.com/83949/)


### 4.[二叉树](http://blog.csdn.net/wbxx727124/article/details/52292832)

## 数据结构

### 1.二叉树（AVL树、红黑树）

```
	在计算机科学中，二叉树是每个节点最多有两个子树的树结构。通常子树被称作“左子树”（left subtree）和“右子树”（right subtree）。
 	AVL树是最先发明的自平衡二叉查找树。在AVL树中任何节点的两个子树的高度最大差别为一，所以它也被称为高度平衡树。
	AVL树本质上还是一棵二叉搜索树，它的特点是：
		1.本身首先是一棵二叉搜索树。
		2.带有平衡条件：每个结点的左右子树的高度之差的绝对值（平衡因子）最多为1。
		也就是说，AVL树，本质上是带了平衡功能的二叉查找树（二叉排序树，二叉搜索树）。
	红黑树（Red Black Tree） 是一种自平衡二叉查找树，是在计算机科学中用到的一种数据结构，典型的用途是实现关联数组。
```

### 2.二叉堆

```
	二叉堆是一种特殊的堆，二叉堆是完全二元树（二叉树）或者是近似完全二元树（二叉树）。二叉堆有两种：最大堆和最小堆。
	最大堆：父结点的键值总是大于或等于任何一个子节点的键值；最小堆：父结点的键值总是小于或等于任何一个子节点的键值。
```

## 常见面试题

### 1.从浏览器地址栏输入url到显示页面的步骤(以HTTP为例)？

```
	1.在浏览器地址栏输入URL
	2.浏览器查看缓存，如果请求资源在缓存中并且新鲜，跳转到转码步骤
		2.1如果资源未缓存，发起新请求
		2.2如果已缓存，检验是否足够新鲜，足够新鲜直接提供给客户端，否则与服务器进行验证。
		2.3检验新鲜通常有两个HTTP头进行控制Expires和Cache-Control：
			HTTP1.0提供Expires，值为一个绝对时间表示缓存新鲜日期
			HTTP1.1增加了Cache-Control: max-age=,值为以秒为单位的最大新鲜时间
	3.浏览器解析URL获取协议，主机，端口，path
	4.浏览器组装一个HTTP（GET）请求报文
	5.浏览器获取主机ip地址，过程如下：
		浏览器缓存
		本机缓存
		hosts文件
		路由器缓存
		ISP DNS缓存
		DNS递归查询（可能存在负载均衡导致每次IP不一样）
	6.打开一个socket与目标IP地址，端口建立TCP链接，三次握手如下：
		客户端发送一个TCP的SYN=1，Seq=X的包到服务器端口
		服务器发回SYN=1， ACK=X+1， Seq=Y的响应包
		客户端发送ACK=Y+1， Seq=Z
	7.TCP链接建立后发送HTTP请求
	8.服务器接受请求并解析，将请求转发到服务程序，如虚拟主机使用HTTP Host头部判断请求的服务程序
	9.服务器检查HTTP请求头是否包含缓存验证信息如果验证缓存新鲜，返回304等对应状态码
	10.处理程序读取完整请求并准备HTTP响应，可能需要查询数据库等操作
	11.服务器将响应报文通过TCP连接发送回浏览器
	12.浏览器接收HTTP响应，然后根据情况选择关闭TCP连接或者保留重用，关闭TCP连接的四次握手如下：
		主动方发送Fin=1， Ack=Z， Seq= X报文
		被动方发送ACK=X+1， Seq=Z报文
		被动方发送Fin=1， ACK=X， Seq=Y报文
		主动方发送ACK=Y， Seq=X报文
	13.浏览器检查响应状态吗：是否为1XX，3XX， 4XX， 5XX，这些情况处理与2XX不同
	14.如果资源可缓存，进行缓存
	15.对响应进行解码（例如gzip压缩）
	16.根据资源类型决定如何处理（假设资源为HTML文档）
	17.解析HTML文档，构件DOM树，下载资源，构造CSSOM树，执行js脚本，这些操作没有严格的先后顺序，以下分别解释
	18.构建DOM树：
		Tokenizing：根据HTML规范将字符流解析为标记
		Lexing：词法分析将标记转换为对象并定义属性和规则
		DOM construction：根据HTML标记关系将对象组成DOM树
	19.解析过程中遇到图片、样式表、js文件，启动下载
	20.构建CSSOM树：
		Tokenizing：字符流转换为标记流
		Node：根据标记创建节点
		CSSOM：节点创建CSSOM树
	21.根据DOM树和CSSOM树构建渲染树:
		从DOM树的根节点遍历所有可见节点，不可见节点包括：1）script,meta这样本身不可见的标签。2)被css隐藏的节点，如display: none
		对每一个可见节点，找到恰当的CSSOM规则并应用
		发布可视节点的内容和计算样式
	22.js解析如下：
		浏览器创建Document对象并解析HTML，将解析到的元素和文本节点添加到文档中，此时document.readystate为loading
		HTML解析器遇到没有async和defer的script时，将他们添加到文档中，然后执行行内或外部脚本。
		这些脚本会同步执行，并且在脚本下载和执行时解析器会暂停。这样就可以用document.write()把文本插入到输入流中。
		同步脚本经常简单定义函数和注册事件处理程序，他们可以遍历和操作script和他们之前的文档内容
		当解析器遇到设置了async属性的script时，开始下载脚本并继续解析文档。脚本会在它下载完成后尽快执行，但是解析器不会停下来等它下载。
		异步脚本禁止使用document.write()，它们可以访问自己script和之前的文档元素
		当文档完成解析，document.readState变成interactive
		所有defer脚本会按照在文档出现的顺序执行，延迟脚本能访问完整文档树，禁止使用document.write()
		浏览器在Document对象上触发DOMContentLoaded事件
		此时文档完全解析完成，浏览器可能还在等待如图片等内容加载，等这些内容完成载入并且所有异步脚本完成载入和执行，
		document.readState变为complete,window触发load事件
	23.显示页面（HTML解析过程中会逐步显示页面）
```

### 2.原生AJAX

```
	
	(() => {
	  'use strict'

	  // 创建一个新的 XMLHttpRequest。这是在无框架情况下使用 AJAX 的方法
	  const xhr = new XMLHttpRequest()
	  // 声明 HTTP 请求方法和地址
	  xhr.open('GET', 'https://randomuser.me/api/?results=3')
	  // in a GET request what you send doesn't matter GET 请求
	  // in a POST request this is the request body
	  xhr.send(null)//data:{name:1}

	  // 等待 'readystatechange' 状态改变去触发 xhr 对象
	  xhr.onreadystatechange = function () {
		//等待 xhr 成功成功返回
		if (xhr.readyState !== 4 ) { return }
		// 非 200 状态时输出错误信息
		if (xhr.status !== 200) { return console.log('Error: ' + xhr.status) }

		// 一切正常！输出响应
		console.log(xhr.responseText)
	  }
	})()
	xhr.readyState
    0：未初始化。尚未调用open()方法
    1：启动。已经调用open()方法，但尚未调用send()方法
    2：发送。已经调用send()方法，但尚未接收到响应
    3：接收。已经接收到部分响应数据
    4：完成。已经接收到全部响应数据，而且已经可以再客户端使用了
```

### 3.深浅复制

```
	浅复制：
		function extend(parent,child){
			var i;
			child = child || {};
			for (i in parent){
				if(parent.hasOwnProperty(i)){
					child[i] = parent[i];
				}
			}
			return child;
		}

		var dad = {name:"Adam"};
		var kid = extend(dad);
		kid.name;//结果为"Adam"

		浅复制，由于通过引用传递，对子属性改变会影响父对象

		var dad = {
			counts:[1,2,3],
			reads:{paper:true}
		}
		var kid = extend(dad);
		kid.counts.push(4);
		dad.counts.toString();//1,2,3,4
		dad.reads === kid.reads;//true

	深复制：
		function extendDeep(parent,child){
			var i,
				toStr = Object.prototype.toString,
				astr = "[object Array]";
			child = child || {}; 
			for(i in parent){
				if(parent.hasOwnProperty(i)){
					console.log(parent[i] +"##"+i+"###"+child[i])
					if(typeof parent[i] === "object"){
						console.log("@@@"+parent[i] +"##"+i+"###"+child[i])
						console.log(parent)
						console.log("###############")
						child[i] = (toStr.call(parent[i]) == astr)?[]:{};
						extendDeep(parent[i],child[i]);
					}else{
						console.log("!!!"+parent[i] +"##"+i+"###"+child[i])
						console.log(child)
						console.log("###############")
						console.log(parent)
						console.log("###############")
						child[i] = parent[i]
					}   
				}
			}
			return child;
		}

		var dad = {
			counts:[1,2,3],
			reads:{paper:true}
		}
		var kid = extendDeep(dad);
		kid.counts.push(4);
		kid.counts.toString();//1,2,3,4
		dad.counts.toString();//1,2,3

		dad.reads === kid.reads;//false
		kid.reads.paper = false;

		kid.reads.web =true;
		dad.reads.paper//结果为true
```

### 4.跨域方式

```
	1.CORS(Cross-Origin Resource Sharing,跨源資源共享) (http://www.ruanyifeng.com/blog/2016/04/cors.html)
        背后的基本思想，就是使用自定义的HTTP头部让浏览器与服务器进行沟通，从而决定请求或响应式应该成功还是失败
        检测xhr是否支持CORS，就是检查是否存在withCredentials属性，再结合检测XDomainRequest对象是否存在，就可以兼顾所以浏览器。
        "withCredentials" in xhr
        typeof XDomainRequest != "undefined"
		Access-Control-Allow-Origin:example.com //允许任意访问的用*
    	Access-Control-Request-Method:GET,POST
		
		浏览器将CORS请求分成两类：简单请求（simple request）和非简单请求（not-so-simple request）。
		只要同时满足以下两大条件，就属于简单请求。
			（1) 请求方法是以下三种方法之一：
			HEAD
			GET
			POST
			（2）HTTP的头信息不超出以下几种字段：
			Accept
			Accept-Language
			Content-Language
			Last-Event-ID
			Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain
		凡是不同时满足上面两个条件，就属于非简单请求。
		
		简单请求
			基本流程
				对于简单请求，浏览器直接发出CORS请求。具体来说，就是在头信息之中，增加一个Origin字段。
				下面是一个例子，浏览器发现这次跨源AJAX请求是简单请求，就自动在头信息之中，添加一个Origin字段。
					GET /cors HTTP/1.1
					Origin: http://api.bob.com
					Host: api.alice.com
					Accept-Language: en-US
					Connection: keep-alive
					User-Agent: Mozilla/5.0...
				上面的头信息中，Origin字段用来说明，本次请求来自哪个源（协议 + 域名 + 端口）。服务器根据这个值，决定是否同意这次请求。
				如果Origin指定的源，不在许可范围内，服务器会返回一个正常的HTTP回应。
				浏览器发现，这个回应的头信息没有包含Access-Control-Allow-Origin字段（详见下文），就知道出错了，
				从而抛出一个错误，被XMLHttpRequest的onerror回调函数捕获。
				注意，这种错误无法通过状态码识别，因为HTTP回应的状态码有可能是200。
				如果Origin指定的域名在许可范围内，服务器返回的响应，会多出几个头信息字段:
					Access-Control-Allow-Origin: http://api.bob.com
					Access-Control-Allow-Credentials: true
					Access-Control-Expose-Headers: FooBar
					Content-Type: text/html; charset=utf-8
				（1）Access-Control-Allow-Origin
					该字段是必须的。它的值要么是请求时Origin字段的值，要么是一个*，表示接受任意域名的请求。
				（2）Access-Control-Allow-Credentials
						该字段可选。它的值是一个布尔值，表示是否允许发送Cookie。
						默认情况下，Cookie不包括在CORS请求之中。
						设为true，即表示服务器明确许可，Cookie可以包含在请求中，一起发给服务器。
						这个值也只能设为true，如果服务器不要浏览器发送Cookie，删除该字段即可。
				（3）Access-Control-Expose-Headers
						该字段可选。CORS请求时，XMLHttpRequest对象的getResponseHeader()方法只能拿到6个基本字段：
						Cache-Control、Content-Language、Content-Type、Expires、Last-Modified、Pragma。
						如果想拿到其他字段，就必须在Access-Control-Expose-Headers里面指定。
						上面的例子指定，getResponseHeader('FooBar')可以返回FooBar字段的值。
			withCredentials 属性
				上面说到，CORS请求默认不发送Cookie和HTTP认证信息。
				如果要把Cookie发到服务器，一方面要服务器同意，指定Access-Control-Allow-Credentials字段。
					Access-Control-Allow-Credentials: true
				另一方面，开发者必须在AJAX请求中打开withCredentials属性。
					var xhr = new XMLHttpRequest();
					xhr.withCredentials = true;
				否则，即使服务器同意发送Cookie，浏览器也不会发送。或者，服务器要求设置Cookie，浏览器也不会处理。
				但是，如果省略withCredentials设置，有的浏览器还是会一起发送Cookie。这时，可以显式关闭withCredentials。
					xhr.withCredentials = false;
				需要注意的是，如果要发送Cookie，Access-Control-Allow-Origin就不能设为星号，必须指定明确的、与请求网页一致的域名。
				同时，Cookie依然遵循同源政策，只有用服务器域名设置的Cookie才会上传，其他域名的Cookie并不会上传，
				且（跨源）原网页代码中的document.cookie也无法读取服务器域名下的Cookie。
		非简单请求
			预检请求
				非简单请求是那种对服务器有特殊要求的请求，比如请求方法是PUT或DELETE，或者Content-Type字段的类型是application/json。
				非简单请求的CORS请求，会在正式通信之前，增加一次HTTP查询请求，称为"预检"请求（preflight）。
				浏览器先询问服务器，当前网页所在的域名是否在服务器的许可名单之中，以及可以使用哪些HTTP动词和头信息字段。
				只有得到肯定答复，浏览器才会发出正式的XMLHttpRequest请求，否则就报错。
				下面是一段浏览器的JavaScript脚本。
					var url = 'http://api.alice.com/cors';
					var xhr = new XMLHttpRequest();
					xhr.open('PUT', url, true);
					xhr.setRequestHeader('X-Custom-Header', 'value');
					xhr.send();
				上面代码中，HTTP请求的方法是PUT，并且发送一个自定义头信息X-Custom-Header。
				浏览器发现，这是一个非简单请求，就自动发出一个"预检"请求，要求服务器确认可以这样请求。下面是这个"预检"请求的HTTP头信息。
					OPTIONS /cors HTTP/1.1
					Origin: http://api.bob.com
					Access-Control-Request-Method: PUT
					Access-Control-Request-Headers: X-Custom-Header
					Host: api.alice.com
					Accept-Language: en-US
					Connection: keep-alive
					User-Agent: Mozilla/5.0...
				"预检"请求用的请求方法是OPTIONS，表示这个请求是用来询问的。头信息里面，关键字段是Origin，表示请求来自哪个源。
				除了Origin字段，"预检"请求的头信息包括两个特殊字段。
					（1）Access-Control-Request-Method
					该字段是必须的，用来列出浏览器的CORS请求会用到哪些HTTP方法，上例是PUT。
					（2）Access-Control-Request-Headers
					该字段是一个逗号分隔的字符串，指定浏览器CORS请求会额外发送的头信息字段，上例是X-Custom-Header。
			预检请求的回应
				服务器收到"预检"请求以后，检查了Origin、Access-Control-Request-Method和Access-Control-Request-Headers字段以后，
				确认允许跨源请求，就可以做出回应。
				如果浏览器否定了"预检"请求，会返回一个正常的HTTP回应，但是没有任何CORS相关的头信息字段。
				这时，浏览器就会认定，服务器不同意预检请求，因此触发一个错误，被XMLHttpRequest对象的onerror回调函数捕获。
				控制台会打印出如下的报错信息。
			浏览器的正常请求和回应
				一旦服务器通过了"预检"请求，以后每次浏览器正常的CORS请求，就都跟简单请求一样，会有一个Origin头信息字段。
				服务器的回应，也都会有一个Access-Control-Allow-Origin头信息字段。
	2.图片Ping（广告跟踪浏览的主要方式）
		图片Ping是于服务器进行简单、单向的跨域通信的一种方式。
		var img = new Image();
		img.onload = img.onerror = function(){
			alert("Done!");
		}
		img.src = "http://xx.com/t?name=xx"
		图片Ping有两个主要缺点，一是只能发送GET请求，而是无法访问服务器的响应文本。
	3.JSONP(JSON with padding)
		JSONP由两部分组成：回调函数和数据。回调函数式当响应到来时应该在页面中调用的函数。回调函数的名字一般在请求中指定的。而
		数据就是传入回调函数中的JSON数据。下面是一个典型的JSONP
		"http://xx.com/t/?callback=handleResponse"
		JSONP是通过动态<script>元素来使用的，<script>和<img>都有能力不受限制的从其它域加载资源。
		function handleResponse(){
			alert(data)
		}
		var script = document.createElement("script");
		script.src = "http://xx.com/t/?callback=handleResponse"
		document.body.insertBefore(script,document.body.firstChild)
		JSONP两个缺点，1是从其它域加载代码，其它域的安全要保证2是要确定JSONP请求是否失败并不容易
```

### 5.[移动端1px细线解决方案总结](http://www.cnblogs.com/lunarorbitx/p/5287309.html)

```
	css中的1px并不等于设备的1px,viewport的设置和屏幕物理分辨率是按比例而不是相同的
	1px解决方案:
		1.用小数来写px值
			IOS8下已经支持带小数的px值, media query对应devicePixelRatio有个查询值-webkit-min-device-pixel-ratio, css可以写成这样
				.border { border: 1px solid #999 }
				@media screen and (-webkit-min-device-pixel-ratio: 2) {
					.border { border: 0.5px solid #999 }
				}
				@media screen and (-webkit-min-device-pixel-ratio: 3) {
					.border { border: 0.333333px solid #999 }
				}
		2.border-image
			这样的1张6X6的图片, 9宫格等分填充border-image, 这样元素的4个边框宽度都只有1px
				@media screen and (-webkit-min-device-pixel-ratio: 2){ 
					.border{ 
						border: 1px solid transparent;
						border-image: url(border.gif) 2 repeat;
					}
				}
			图片可以用gif, png, base64多种格式, 以上是上下左右四条边框的写法, 需要单一边框只要定义单一边框的border, 代码比较直观.
		3. background渐变
			背景渐变, 渐变在透明色和边框色中间分割, frozenUI用的就是这种方法, 借用它的上边框写法:
				@media screen and (-webkit-min-device-pixel-ratio: 2){
					.ui-border-t {
						background-position: left top;
						background-image: -webkit-gradient(linear,left bottom,left top,color-stop(0.5,transparent),color-stop(0.5,#e0e0e0),to(#e0e0e0));
					}
				}
		4.flexible.js
			这是淘宝移动端采取的方案, github的地址:https://github.com/amfe/lib-flexible. 前面已经说过1px变粗的原因就在于一刀切的设置viewport宽度,
			如果能把viewport宽度设置为实际的设备物理宽度, css里的1px不就等于实际1px长了么. flexible.js就是这样干的.

			<meta name=”viewport”>里面的scale值指的是对ideal viewport的缩放, flexible.js检测到IOS机型, 会算出scale = 1/devicePixelRatio, 然后设置viewport

			metaEl = doc.createElement('meta');
			metaEl.setAttribute('name', 'viewport');
			metaEl.setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
			devicePixelRatio=2时输出meta如下, 这样viewport与ideal viewport的比是0.5, 也就与设备物理像素一致

			<meta name="viewport" content="initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no">
			另外html元素上的font-size会被设置为屏幕宽的1/10, 这样css可以以rem为基础长度单位进行改写, 比如rem是28px, 原先的7px就是0.25rem. border的宽度能直接写1px.

			function refreshRem() {
				var width = docEl.getBoundingClientRect().width;
				if (width / dpr > 540) { //大于540px可以不认为是手机屏
					width = 540 * dpr;
				}
				var rem = width / 10; 
				docEl.style.fontSize = rem + 'px';
				flexible.rem = win.rem = rem;
			}
```

### 6.请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象

```
	function getQueryStringArgs() {
        var qs = (location.search.length > 0 ? location.search.substring(1) : ""),
            args = {},
            items =qs.length ? qs.split("&") : [],
            item = null,
            name = null,
            value = null,
            i = 0,
            len = items.length;

        for (i = 0; i < len; i++){
            item = items[i].split("=");
            name = decodeURIComponent(item[0]);
            value = decodeURIComponent(item[1]);
            if(name.length){
                args[name] = value;
            }
        }
        return args;
    }
```
### 7.说说get和post请求的区别

```
 三个误解：
 	GET和POST与数据如何传递没有关系
	HTTP协议对GET和POST都没有对长度的限制
	安全不安全和GET、POST没有关系
	所以我对于GET和POST的理解，是纯粹地来源于HTTP协议。GET和POST本质上就是TCP链接，并无差别。
	他们只有一点根本区别，简单点儿说，语义上一个用于获取数据，一个用于修改数据。
```
### 8.什么是 "use strict"? 使用它的好处和坏处分别是什么？

```
	（http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html）
	ECMAscript 5添加了第二种运行模式："严格模式"（strict mode）。顾名思义，这种模式使得Javascript在更严格的条件下运行。
	设立"严格模式"的目的，主要有以下几个：
	1. 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;
	2. 消除代码运行的一些不安全之处，保证代码运行的安全；
	3. 提高编译器效率，增加运行速度；
	4. 为未来新版本的Javascript做好铺垫。
	注：经过测试 IE6,7,8,9 均不支持严格模式。
	缺点：
	现在网站的 JS 都会进行压缩，一些文件用了严格模式，而另一些没有。
	这时这些本来是严格模式的文件，被 merge 后，这个串就到了文件的中间，不仅没有指示严格模式，反而在压缩后浪费了字节。
```

### 9.有一个长度为100的数组，请以优雅的方式求出该数组的前10个元素之和

```
	 var a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15],
		sum = 0;  
	 sum = a.slice(0, 10).reduce(function(pre, current) {
		return pre + current;
	 });
	 console.log(sum); //55
```

### 10.不使用loop循环，创建一个长度为100的数组，并且每个元素的值等于它的下标。

```
	var a = Array(100).join(",").split(",").map(function(item, index) {
	  return index;
	});
```

### 11.实现对数组进行乱序

```
	var a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    sign = 1; 
	a.sort(function(a, b) {
		//因为Math.random产生的数在0-1之间
		//所以0.5两边的概率是相等的
		//大于0.5时为升序，小于0.5时为降序
		sign = (Math.random() > 0.5) ? 1 : -1;
		return (a - b) * sign;
	});

```

### 12.xss和csrf分别是什么？

```
	XSS (Cross Site Script) ，跨站脚本攻击
		XSS是你访问正常网站的时候，你浏览器执行了攻击者的代码
	CSRF(Cross Site Request Forgery)，跨站点伪造请求
		CSRF是你点击了攻击者提供的链接的时候（正常网站或其它有攻击者代码的网站）
```

### 13.说说前端如何解决异步回调地狱？

```
	使用Promise来解决回调地狱问题
```

### 14.淘宝那里的商品项，如图片，滚动到了才加载，你知道怎么实现么(图片可视区域加载)

```
	https://www.talkingcoder.com/article/6370149516108046040
	<script type="text/javascript">
		var aImages = document.getElementById("SB").getElementsByTagName('img'); //获取id为SB的文档内所有的图片
		loadImg(aImages);
		window.onscroll = function() { //滚动条滚动触发
			loadImg(aImages);
		};
		//getBoundingClientRect  是图片懒加载的核心
		function loadImg(arr) {
			for(var i = 0, len = arr.length; i < len; i++) {
				if(arr[i].getBoundingClientRect().top < document.documentElement.clientHeight && !arr[i].isLoad) {
					arr[i].isLoad = true; //图片显示标志位
					//arr[i].style.cssText = "opacity: 0;";  
					(function(i) {
						setTimeout(function() {
							if(arr[i].dataset) { //兼容不支持data的浏览器
								aftLoadImg(arr[i], arr[i].dataset.imgurl);
							} else {
								aftLoadImg(arr[i], arr[i].getAttribute("data-imgurl"));
							}
							arr[i].style.cssText = "transition: 1s; opacity: 1;" //相当于fadein
						}, 500)
					})(i);
				}
			}
		}

		function aftLoadImg(obj, url) {
			var oImg = new Image();
			oImg.onload = function() {
				obj.src = oImg.src; //下载完成后将该图片赋给目标obj目标对象
			}
			oImg.src = url; //oImg对象先下载该图像
		}
	</script>
```

### 15.到底该不该用 CSS reset？

```
	https://www.zhihu.com/question/23554164
```

### 16.前端link和import的区别

```
	link是HTML方式， @import是CSS方式
	link最大限度支持并行下载，@import过多嵌套导致串行下载，出现FOUC
	link可以通过rel="alternate stylesheet"指定候选样式
	浏览器对link支持早于@import，可以使用@import对老浏览器隐藏样式
	@import必须在样式规则之前，可以在css文件中引用其他文件
	总体来说：link优于@import
```
### 17.理解HTTP/304响应(HTTP原理中的缓存机制)

![](http://static.oschina.net/uploads/space/2015/0119/015353_P04w_568818.png)

```
	http://blog.csdn.net/soonfly/article/details/50953814
	https://my.oschina.net/leejun2005/blog/369148
	辨别条件请求
		当客户端缓存了目标资源但不确定该缓存资源是否是最新版本的时候,就会发送一个条件请求.在Fiddler中,
		你可以在Headers Inspector查找相关请求头,这样就可以辨别出一个请求是否是条件请求.
		在进行条件请求时,客户端会提供给服务器一个If-Modified-Since请求头,其值为服务器上次返回的Last-Modified响应头中的日期值,
		还会提供一个If-None-Match请求头,值为服务器上次返回的ETag响应头的值:
		服务器会读取到这两个请求头中的值,判断出客户端缓存的资源是否是最新的,
		如果是的话,服务器就会返回HTTP/304 Not Modified响应,但没有响应体.客户端收到304响应后,就会从缓存中读取对应的资源.
		另一种情况是,如果服务器认为客户端缓存的资源已经过期了,那么服务器就会返回HTTP/200 OK响应,响应体就是该资源当前最新的内容.
		客户端收到200响应后,就会用新的响应体覆盖掉旧的缓存资源.
		只有在客户端缓存了对应资源且该资源的响应头中包含了Last-Modified或ETag的情况下,才可能发送条件请求.
		如果这两个头都不存在,则必须无条件(unconditionally)请求该资源,服务器也就必须返回完整的资源数据.
	为什么要使用条件请求
		当用户访问一个网页时,条件请求可以加速网页的打开时间(因为可以省去传输整个响应体的时间),但仍然会有网络延迟,
		因为浏览器还是得为每个资源生成一条条件请求,并且等到服务器返回HTTP/304响应,才能读取缓存来显示网页.
		更理想的情况是,服务器在响应上指定Cache-Control或Expires指令,这样客户端就能知道该资源的可用时间为多长,
		也就能跳过条件请求的步骤,直接使用缓存中的资源了.可是,即使服务器提供了这些信息,在下列情况下仍然需要使用条件请求:
			在超过服务器指定的过期时间之后
			如果用户执行了刷新操作的话
		在上节给出的图片中,请求头中包含了一个Pragma: no-cache.这是由于用户使用F5刷新了网页.
		如果用户按下了CTRL-F5 (有时称之为“强刷-hard refresh”),你会发现浏览器省略了If-Modified-Since和If-None-Match请求头,也就是无条件的请求页面中的每个资源.
	避免条件请求
		通常来说,缓存是个好东西.如果你想提高自己网站的访问速度,缓存是必须要考虑的.可是在调试的时候,有时候需要阻止缓存,这样才能确保你所访问到的资源是最新的.
		如果你想全局阻止HTTP/304响应,可以这么做:首先清除浏览器的缓存,
		可以使用Fiddler工具栏上的Clear Cache按钮(仅能清除Internet Explorer缓存),
		或者在浏览器上按CTRL+SHIFT+DELETE(所有浏览器都支持).
		在清除浏览器的缓存之后,回到Fiddler中,在菜单中选择Rules > Performance > Disable Caching选项,
		然后Fiddler就会:删除所有请求中的条件请求相同的请求头以及所有响应中的缓存时间相关的响应头.
		此外,还会在每个请求中添加Pragma: no-cache请求头,在每个响应中添加Cache-Control: no-cache响应头,阻止浏览器缓存这些资源.
```
### 18.css实现超出字体内容出现 ...

```
	overflow: hidden;
	text-overflow:ellipsis;
	white-space: nowrap;
	
	display: -webkit-box;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 3;
	overflow: hidden;
```

### 19.JavaScript函数节流和函数防抖之间的区别

```
	http://www.jianshu.com/p/b73c2acad696?utm_campaign=hugo&utm_medium=reader_share&utm_content=note
	函数节流是指一定时间内js方法只跑一次。比如人的眨眼睛，就是一定时间内眨一次。这是函数节流最形象的解释。
	函数防抖是指频繁触发的情况下，只有足够的空闲时间，才执行代码一次。比如生活中的坐公交，就是一定时间内，如果有人陆续刷卡上车，司机就不会开车。
	只有别人没刷卡了，司机才开车。
	// 函数节流
	var canRun = true;
	document.getElementById("throttle").onscroll = function(){
		if(!canRun){
			// 判断是否已空闲，如果在执行中，则直接return
			return;
		}

		canRun = false;
		setTimeout(function(){
			console.log("函数节流");
			canRun = true;
		}, 300);
	};
	// 函数防抖
	var timer = false;
	document.getElementById("debounce").onscroll = function(){
		clearTimeout(timer); // 清除未执行的代码，重置回初始化状态

		timer = setTimeout(function(){
			console.log("函数防抖");
		}, 300);
	};
```

### 20.实现一个LazyMan

```
	function _LazyMan(name) {
	    this.tasks = [];   
	    var self = this;
	    var fn =(function(n){
	        var name = n;
	        return function(){
	            console.log("Hi! This is " + name + "!");
	            self.next();
	        }
	    })(name);
	    this.tasks.push(fn);
	    setTimeout(function(){
	        self.next();
	    }, 0); // 在下一个事件循环启动任务
	}
	/* 事件调度函数 */
	_LazyMan.prototype.next = function() { 
	    var fn = this.tasks.shift();
	    fn && fn();
	}
	_LazyMan.prototype.eat = function(name) {
	    var self = this;
	    var fn =(function(name){
	        return function(){
	            console.log("Eat " + name + "~");
	            self.next()
	        }
	    })(name);
	    this.tasks.push(fn);
	    return this; // 实现链式调用
	}
	_LazyMan.prototype.sleep = function(time) {
	    var self = this;
	    var fn = (function(time){
	        return function() {
	            setTimeout(function(){
	                console.log("Wake up after " + time + "s!");
	                self.next();
	            }, time * 1000);
	        }
	    })(time);
	    this.tasks.push(fn);
	   return this;
	}
	_LazyMan.prototype.sleepFirst = function(time) {
	    var self = this;
	    var fn = (function(time) {
	        return function() {
	            setTimeout(function() {
	                console.log("Wake up after " + time + "s!");
	                self.next();
	            }, time * 1000);
	        }
	    })(time);
	    this.tasks.unshift(fn);
	    return this;
	}
	/* 封装 */
	function LazyMan(name){
	    return new _LazyMan(name);
	}
```

### 21.在textarea光标处插入内容

```
	<html>   
	<head>   
	<script type='text/javascript'>   
	function test(str){  

		var tc = document.getElementById("mytextarea");  
		var tclen = tc.value.length;  
		tc.focus();  
		if(typeof document.selection != "undefined")  
		{  
			document.selection.createRange().text = str;    
		}  
		else  
		{  
			tc.value = tc.value.substr(0,tc.selectionStart)+str+tc.value.substring(tc.selectionStart,tclen);  
		}  
	}  
	</script>   
	</head>   
	<body>  
	<textarea rows=5 name=s1 cols=27  id="mytextarea">目的通过点击页面上的按钮button 在textarea中的光标停留处插上文字 </textarea>   
	<input type=button onclick="test('这是需要加入的文字')" />   
	</body>   
	</html> 
```
### 22.如何快速把一个多维数组转换成一个简单一维数组

```
	var a = [1,3,4,5,[6,7,9],[2],[5]];
	a = a.join(",").split(",");//a.toString()..split(",")
```

### 23.nodeType

```
	Node类型(nodeType )
		Node.ELEMENT_NODE 1
		Node.ATTRIBUTE_NODE 2
		Node.TEXT_NODE 3
		Node.CDATA_SECTION_NODE 4
		Node.ENTITY_REFERENCE_NODE 5
		Node.ENTITY_NODE 6
		Node.PROCESSING_INSTRUCTION_NODE 7
		Node.COMMENT_NODE 8
		Node.DOCUMENT_NODE 9
		Node.DOCUMENT_TYPE_NODE 10
		Node.DOCUMENT_FRAGMENT_NODE 11
		Node.NOTATION_NODE 12
		节点类型	描述	子节点
	1	Element	代表元素	Element, Text, Comment, ProcessingInstruction, CDATASection, EntityReference
	2	Attr	代表属性	Text, EntityReference
	3	Text	代表元素或属性中的文本内容。	None
	4	CDATASection	代表文档中的 CDATA 部分（不会由解析器解析的文本）。	None
	5	EntityReference	代表实体引用。	Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
	6	Entity	代表实体。	Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
	7	ProcessingInstruction	代表处理指令。	None
	8	Comment	代表注释。	None
	9	Document	代表整个文档（DOM 树的根节点）。	Element, ProcessingInstruction, Comment, DocumentType
	10	DocumentType	向为文档定义的实体提供接口	None
	11	DocumentFragment	代表轻量级的 Document 对象，能够容纳文档的某个部分	Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
	12	Notation	代表 DTD 中声明的符号。	None

```

### 24.正则表达式贪婪与非贪婪模式

```
	贪婪匹配:正则表达式一般趋向于最大长度匹配，也就是所谓的贪婪匹配。
	非贪婪匹配：就是匹配到结果就好，就少的匹配字符。
	默认是贪婪模式；在量词后面直接加上一个问号？就是非贪婪模式。
		量词：{m,n}：m到n个

　　　　　*：任意多个

　　　　　+：一个到多个

　　　　　？：0或一个
	String rule1="content:\".+\"";    //贪婪模式
	String rule2="content:\".+?\"";    //非贪婪模式
	
```

### 25.正则捕获

```
	捕获组  
		捕获组可以通过从左到右计算其开括号来编号 。例如，在表达式 (A)(B(C)) 中，存在四个这样的组：
		0   (A)(B(C))
		1   (A)
		2  (B(C))
		3  (C)
		组零始终代表整个表达式,捕获的子序列稍后可以通过 Back 引用（反向引用） 在表达式中使用(\1)
	非捕获组
		以 (?) 开头的组是纯的非捕获 组，它不捕获文本 ，也不针对组合计进行计数。就是说，如果小括号中以?号开头，那么这个分组就不会捕获文本，
		当然也不会有组的编号，因此也不存在Back 引用。
		
		1、非捕获组(?:Pattern)
			它的作用就是匹配Pattern字符，好处就是不捕获文本，不将匹配到的字符存储到内存中，从而节省内存。
		2、零宽度断言
			(?=X ) 零宽度正先行断言。仅当子表达式 X 在 此位置的右侧匹配时才继续匹配。(正向预搜索)
			也就是说要使此零宽度断言起到我们想要的效果的话，就必须把这个非捕获组放在整个表达式的右侧。
			例如，/w+(?=/d) 与后跟数字的单词匹配，而不与该数字匹配。此构造不会回溯。
			(?!X)零宽度负先行断言。仅当子表达式 X 不在 此位置的右侧匹配时才继续匹配。(正向预搜索)
			例如，例如，/w+(?!/d) 与后不跟数字的单词匹配，而不与该数字匹配 。
			(?<=X)零宽度正后发断言。仅当子表达式 X 在 此位置的左侧匹配时才继续匹配。(反向预搜索)
			例如，(?<=19)99 与跟在 19 后面的 99 的实例匹配。此构造不会回溯。(反向预搜索)
			(?<!X)零宽度负后发断言。仅当子表达式 X 不在此位置的左侧匹配时才继续匹配。
			例如，(?<!19)99 与不跟在 19 后面的 99 的实例匹配
		3、模式修正符
			(?)开头的非捕获组除了零宽度断言之外，还有模式修正符。
			正则表达式中常用的模式修正符有i、g、m、s、x、e等。它们之间可以组合搭配使用。
			(?imnsx-imnsx: ) 应用或禁用子表达式中指定的选项。例如，(?i-s: ) 将打开不区分大小写并禁用单行模式。
			【例1】(?i)ab
			表示对(?i)后的所有字符都开启不区分大小写的开关。故它可以匹配ab、aB、Ab、AB
		4、(?>Pattern)等同于侵占模式
			匹配成功不进行回溯，这个比较复杂，与侵占量词“+”可以通用，比如：\d++ 可以写为 (?>\d+)。
```
### 26.重排与重绘

```
	浏览器下载完页面中的所有组件——HTML标记、JavaScript、CSS、图片之后会解析生成两个内部数据结构——DOM树和渲染树。
	DOM树表示页面结构，渲染树表示DOM节点如何显示。
	DOM树中的每一个需要显示的节点在渲染树种至少存在一个对应的节点（隐藏的DOM元素 disply值为none 在渲染树中没有对应的节点）。
	渲染树中的节点被称为“帧”或“盒",符合CSS模型的定义，理解页面元素为一个具有填充，边距，边框和位置的盒子。
	一旦 DOM和渲染树构建完成，浏览器就开始显示（绘制）页面元素。
	当DOM的变化影响了元素的几何属性（宽或高），浏览器需要重新计算元素的几何属性，同样其他元素的几何属性和位置也会因此受到影响。
	浏览器会使渲染树中受到影响的部分失效，并重新构造渲染树。这个过程称为重排。
	完成重排后，浏览器会重新绘制受影响的部分到屏幕，该过程称为重绘。
	由于浏览器的流布局，对渲染树的计算通常只需要遍历一次就可以完成。
	但table及其内部元素除外，它可能需要多次计算才能确定好其在渲染树中节点的属性，通常要花3倍于同等元素的时间。
	这也是为什么我们要避免使用table做布局的一个原因。
	并不是所有的DOM变化都会影响几何属性，比如改变一个元素的背景色并不会影响元素的宽和高，这种情况下只会发生重绘。
```
### 27.Underscore _.template 方法使用详解

```
	https://github.com/hanzichi/underscore-analysis/issues/26
	_.template 支持以下三种模板。
		1. <%  %> - to execute some code
		2. <%= %> - to print some value in template
		3. <%- %> - to print some values HTML escaped
	如果你不喜欢它默认的模板风格，也可以自己定义，注意 key 必须和源码中的 key 保持一致，才能覆盖。
	_.templateSettings = {
	  // 三种渲染模板
	  evaluate    : /<%([\s\S]+?)%>/g,
	  interpolate : /<%=([\s\S]+?)%>/g,
	  escape      : /<%-([\s\S]+?)%>/g
	};
	扩展-EJS（正好和_.template相反）：
		Escapes html by default with <%= code %>
		Unescaped buffering with <%- code %>
```


## 移动端常见问题

### 1.移动端click屏幕产生200-300 ms的延迟响应

```
	解决方案：
		fastclick可以解决在手机上点击事件的300ms延迟
		zepto的touch模块，tap事件也是为了解决在click的延迟问题
```

### 2.消除transition闪屏

```
	开启硬件加速
		解决页面闪白
		保证动画流畅
	当它们检测到页面中某个DOM元素应用了某些CSS规则时就会开启，最显著的特征的元素的3D变换。
	可是在一些情况下，我们并不需要对元素应用3D变换的效果，那怎么办呢？这时候我们可以使用个小技巧“欺骗”浏览器来开启硬件加速。
	虽然我们可能不想对元素应用3D变换，可我们一样可以开启3D引擎。例如我们可以用transform: translateZ(0); 来开启硬件加速。
	或者可以用transform: translateZ(0); 来开启硬件加速 。
	.css {
	   -webkit-transform: translate3d(0, 0, 0);
	   -moz-transform: translate3d(0, 0, 0);
	   -ms-transform: translate3d(0, 0, 0);
	   transform: translate3d(0, 0, 0);
	}

```

### 3.fixed定位的问题

```
	遇到的都知道在ios的safari里面不支持position:fixed;(呵呵了),其实也不算是不支持，只是在软键盘弹出来的时候使用fixed的元素就开始各种抽风了。
	解决方法：在键盘弹出来之前按照正常的定位，使用fixed，弹出来的时候将footer这部分position:static;然后这样footer就会跑向页面的最下面了，然后再将页面主动滚动到底部。
	当blur的时候再把footer设置回去.或者ISCROLL.js	
```

### 4.0.1+0.2 != 0.3

```
	解决方案：
		确定小数点后位数范围的话，(a*10+b*10)/10 
		三方库BigDecimal
```

### 5.Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示

```
	可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.	
```

### 6.textarea的focus问题

```
	这次有个需求是点击main的某个元素，需要textarea获取焦点并弹出软键盘。其实这些都不是关键。
	问题是在点击main的该元素的时候，还是需要跑个ajax判断下能否进行评论，这样一跑ajax就获取不了焦点了。
	解决方法：其实为啥使用了oTextarea.focus()不管用，其实就是中间的这层ajax使用了异步了。
	这样浏览器以为这是两件事，处于安全性考虑它给禁止了，然后将ajax改成同步的就OK了。
    同样在window.open()的时候也会遇到这个问题，解法相同。
```

### 7.在特定的android的机子(vivo…)里，在键盘收起来不会失焦

```
	本来是在失焦的时候触发了一个blur事件的东西，这样就会出现问题。
	解决方法：
	(function() {
		var height = window.innerHeight;
		function loop_height() {
			setTimeout(function() {
				if(window.innerHeight > height + 200){
					//触发blur事件
				}else{
					height = window.height;
				}
			},1000);
		}
		loop_height();
	})();
	其实就是一直获取页面的可视高度，在键盘弹出来的时候键盘的部分不算innerHeight;这样在键盘收起来的时候就能知道了，
	如果感觉时间比较长可以把setTimeout的时间改小一点，默认在少于300ms的时候感觉不出页面的迟钝。
```

### 8.微信

```
	通过微信分享链接，后面被加上from=singlemessage&isappinstalled=1，会导致你之前的from参数可能获取不到	
```

### 9.IOS上带-的日期，new Date时会出错

```
	换个格式
```

### 10.revert merge会导致下次merge无效

```
	http://www.tuicool.com/articles/iIzeY3e
```
### 11.jquery在ios上事件委托失效

```
	PC、Android都没问题，IOS无法冒泡到，原因是事件委托在了body上，改为body内的元素即可；
	另外，加cursor:pointer;也可以解决，但不明白为什么，如果a标签不加href也会失效，这个问题解决了，但原因还有待研究。
```
