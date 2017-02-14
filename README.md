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
    如果一个元素绝对定位后，其参照物是以离自身最近元素是否设置了相对定位，如果有设置将以离自己最近元素定位，如果没有将往其祖先元素寻找相对定位元素，一直     找到html为止。
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
        “行高“指一行文字的高度，具体来说是指两行文字间基线间的距离。在CSS，line-height被用来控制行与行之间的垂直距离。line-height 属性会影响行框的     布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。
        从上到下四条线分别是顶线、中线、基线、底线，很像才学英语字母时的四线三格，我们知道vertical-align属性中有top、middle、baseline、bottom，就     是和这四条线相关。
        行高是指上下文本行的基线间的垂直距离，即图中两条红线间垂直距离。
    行距是指一行底线到下一行顶线的垂直距离，即第一行粉线和第二行绿线间的垂直距离。
    半行距是行距的一半，即区域3垂直距离/2，区域1，2，3，4的距离之和为行高，而区域1，2，4距离之和为字体size，所以半行距也可以这么算：（行高-字体         size）/2
    vertical-align（http://www.zhangxinxu.com/wordpress/2010/05/%E6%88%91%E5%AF%B9css-vertical-align%E7%9A%84%E4%B8%80%E4%BA%9B%E7%90%86%E8%A7%A3%E4%B8%8E%E8%AE%A4%E8%AF%86%EF%BC%88%E4%B8%80%EF%BC%89/）
    定义和用法
    vertical-align 属性设置元素的垂直对齐方式。
    说明
    该属性定义行内元素的基线相对于该元素所在行的基线的垂直对齐。允许指定负长度值和百分比值。这会使元素降低而不是升高。在表单元格中，这个属性会设置单     元格框中的单元格内容的对齐方式。
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
 
 
 2.绘制
 
 3.动画
 
##JS
<h3>ES6</h3>
##WEB API
##HTTP
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
