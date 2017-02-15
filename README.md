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
        “行高“指一行文字的高度，具体来说是指两行文字间基线间的距离。在CSS，line-height被用来控制行与行之间的垂直距离。line-height 属性会影响行框的         布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。
        从上到下四条线分别是顶线、中线、基线、底线，很像才学英语字母时的四线三格，我们知道vertical-align属性中有top、middle、baseline、bottom，就         是和这四条线相关。
        行高是指上下文本行的基线间的垂直距离，即图中两条红线间垂直距离。
        行距是指一行底线到下一行顶线的垂直距离，即第一行粉线和第二行绿线间的垂直距离。
        半行距是行距的一半，即区域3垂直距离/2，区域1，2，3，4的距离之和为行高，而区域1，2，4距离之和为字体size，所以半行距也可以这么算：（行高-字体         size）/2
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
 
##JS
<h3>ES6</h3>
##WEB API

1.DOM API

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
    
##数据结构
##常见面试题
1.从浏览器地址栏输入url到显示页面的步骤(以HTTP为例)？
##坑
