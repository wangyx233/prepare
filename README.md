## javascript
#### 原生DOM操作
#### 事件委托

#### 前端路由的原理  
` 路由分发：当用户使用 127.0.0.1/about           访问页面时，服务器接收到这个请求，然后解析url中的路径／about，这个路径对应这相应的处理逻辑，程序就把这个请求交给对应的逻辑处理。 这就完成了一次路由分发。`  
前端的路由和后端的路由在实现技术上不一样，但是原理都是一样的。    
有两种实现方式，hash和h5的history api    
> 1. 在h5的history API出现之前，前端路由都是用hash来实现的，url中加上“＃”,web服务器不会解析hash，就是说＃后的内容web服务器都会自动忽略。但是js可以用window.location.hash读取，读取到路径后加以解析就可以根据不同路径进行响应。     
`127.0.0.1/#/about` 用过angularjs1.x 的ui－router。  
2. hash能够兼容低版本的浏览器，对于h5的history api，可以用来操作浏览器的session history（会话历史）来实现。

优点：
> 与后台路由相比优点：后端路由每次访问一个新页面的时候都要向服务器发送请求，然后服务器再响应请求，这个过程会有延迟。而前端路由在访问一个新页面的时候仅仅是变换了一下路径，没有了网络延迟，对于用户体验来说会有相当大的提升。    
与传统ajax相比优点：ajax请求不会留下history记录，用户无法直接通过url进入指定页面，也没有办法收藏，分享等。

## html
#### doctype作用
> 告诉浏览器的解析器用什么样的文档标准来解析文档。要是没有doctype或者定义的不正确，浏览器则会以兼容模式呈现。    
标准模式：排版和js的运行模式都是以浏览器支持的最高标准来运行。 兼容模式是以向后兼容的模式显示，模仿老式的浏览器行为防止站点无法访问。

> html5 <!DOCTYPE HTML> 不基于SGML(标准通用标记语言)，所以不需要引用DTD(文档类型定义:SGML+XML),只需要用doctype来规范浏览器行为即可。  
html4.0.1是基于SGML的，需要引入DTD，才能告知浏览器所用的文档类型。  

#### html标签分类
` 通过元素的display属性，html标签可以分为： 块级元素和行内元素.`   
`display的值常用的：block，inline，inline－block，none，inherit `
> 块级元素：div，p，h1，h2，h3，h4，h5，h6，ul，ol，li，dl，dt，dd  
行内元素： span，input，a，img，select，strong(强调)，b(粗体)   
两者区别：  
1. block元素会独占一行，垂直方向排列，默认情况下，block元素宽度自动填满其父元素宽度。    
inline元素不会独占一行，水平方向排列，相邻的行内元素排列在一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化.  
2. block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。设置margin和padding属性。     
行内元素设置width无效，height无效(可以设置line-height)，margin上下无效，padding上下无效。    
3. 块级元素可以包含行内元素和块级元素。行内元素不能包含块级元素。每个特定的元素能包含的元素也是特定的，所以具体到个别元素上，这条规律是不适用的。比如 P 元素，只能包含inline元素，而不能包含block元素。      
ps: img、input、textarea、select、object都是替换元素.替换元素一般有内在尺寸，所以具有width和height，可以设定.    
常见的空标签：`<br/> ,<hr/>,<img/>,<input/>,<link>,<meta>`  
不常见的标签：`<area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>`  

#### html语义化的理解
1. 使用正确的标签做正确的事
2. 让页面内容结构化，便于浏览器的解析
3. 即使没有css样式，也是容易阅读的。
4. 便于seo(搜索引擎的爬虫依赖于HTML标记来确定上下文和各个关键字的权重)
5. 便于代码维护

## css
#### 引入页面样式，link和@import的区别
> 1. 根本区别：link是xhtml标签，除了可以引入css外，还可以定义rel连接属性，定义rss，等；而@import是css提供的，只能加载css  
2. 加载顺序区别：link在页面加载的同时加载css；@import是在页面加载结束完再加载。所以，有时候浏览@import引入css的页面开始会没有样式==@import闪烁问题,网速慢的时候尤其。  
3.兼容性区别：@import是css2.1，所以ie5以上的浏览器才能识别；而link属于xhtml标签，没有兼容性问题。  
4.dom修改样式，只能控制link引入的css，@import无法。  
5.@import可以在css里再引入别的css样式，但是容易对服务器产生多次http请求，对服务器造成压力。    

#### css选择器及其权重
就近原则，!important > id >class  !important的优先级比内联高  
1.id选择器（ # myid）  
2.类选择器（.myclassname）  
3.标签选择器（div, h1, p）  
4.相邻选择器（h1 + p）  
5.子选择器（ul > li）  
6.后代选择器（li a）  
7.通配符选择器（ * ）  
8.属性选择器（a[rel = "external"]）  
9.伪类选择器（a:hover, li:nth-child）  
*   可继承的样式： font-size font-family color, UL LI DL DD DT;
*   不可继承的样式：border padding margin width height ;  
  
#### 居中问题   
1. 居中一个div:给div一个宽度，然后设置margin:0 auto  
``` 
div{
      width:200px;
      margin:0 auto;
}
```
ps: 文字居中，text-align:center ; 配合 line-height
2. 居中一个浮动元素  
3. 居中一个绝对定位的元素     
```
div{
  position: absolute;
  width: 1200px;
  margin: 0 auto;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  }
```
