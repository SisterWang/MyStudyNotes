# jQuery基础学习（一）--样式

## 认识jQuery

### 环境搭建
进入官方网站获取最新的版本 http://jquery.com/download/   
其中2.x 以上版本不再兼容 IE6、7、8浏览器，这样做的目的是为了兼容移动端开发。  

jQuery是一个JavaScript脚本库，不需要特别的安装，只需要我们在页面 <head> 标签内中，通过 script 标签引入 jQuery 库即可。
```
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <script type="text/javascript" src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
    <title>环境搭建</title>
</head> 
```
 
### HelloWorld
 
```
$(document).ready(function() {
    $("div").html("Hello world!");
});
```
$(document).ready 的作用是等页面的文档（document）中的节点都加载完毕后，再执行后续的代码
 
### jQuery对象与DOM对象
**jQuery对象与DOM对象是不一样的**  
 
假设有一个p节点,id为pp，其通过标准JavaScript处理：
```
var p = document.getElementById('pp');
p.innerHTML = 'Hello';
p.style.color = 'red';
```
通过JQuery处理：
```
var $p = $('#pp');
$p.html('Hello').css('color','red');
```
通过原生DOM模型提供的document.getElementById获取的p为一个DOM对象。而通过$('#pp')获得的$p为一个JQuery对象，其中包含DOM对象的信息，并封装了许多方法。
- 通过jQuery方法包装后的对象，是一个类数组对象。它与DOM对象完全不同，唯一相似的是它们都能操作DOM。
- 通过jQuery处理DOM的操作，可以让开发者更专注业务逻辑的开发，而不需要我们具体知道哪个DOM节点有那些方法，也不需要关心不同浏览器的兼容性问题，我们通过jQuery提供的API进行开发，代码也会更加精短。

### jQuery对象转化成DOM对象
jQuery库本质上还是JavaScript代码，它只是对JavaScript语言进行包装处理，为的是提供更好更方便快捷的DOM处理与开发中经常使用的功能。我们需要jQuery与DOM能够相互的转换，它们都是可以操作的DOM元素，**jQuery是一个类数组对象，而DOM对象就是一个单独的DOM元素。**  

转换为DOM对象：
```
var $div = $('div') //jQuery对象
var div = $div.get(0) //转化成DOM对象
div.style.color = 'red' //操作dom对象的属性
```

### DOM对象转化成jQuery对象
相比较jQuery转化成DOM，开发中更多的情况是把一个dom对象加工成jQuery对象。  
**$(参数)是一个多功能的方法，通过传递不同的参数而产生不同的作用**。  

如果传递给$(DOM)函数的参数是一个DOM对象，jQuery方法会把这个DOM对象给包装成一个新的jQuery对象:
```
var div = document.getElementsByTagName('div'); //dom对象
var $div = $(div); //jQuery对象
var $first = $div.first(); //找到第一个div元素
$first.css('color', 'red'); //给第一个元素设置颜色
```

## jQuery选择器

### id选择器
一个用来查找的ID，即元素的id属性。id选择器也是基本的选择器，jQuery内部使用JavaScript函数document.getElementById()来处理ID的获取。有原生的方法支持，更高效。  
**语法：**  
*$( "#id" )*  
**id是唯一的**。 如果多个元素分配了相同的id，将只匹配该id选择集合的第一个DOM元素。 

### 类选择器
类选择器，顾名思义，通过class样式类名来获取节点。类选择器，相对id选择器来说，**效率相对会低一点**，但是优势就是**可以多选**。  

**语法：**  
*$( ".class" )*  
```
$( ".class1" ).css("color","red");//可以不用循环处理多个元素
```

### 元素选择器
元素选择器：根据给定（html）标记名称选择所有的元素。这个是一个合集的操作，同样的也有原生方法getElementsByTagName()函数支持。  
**语法：**  
*$( "element" )*  
```
$( "div" ).css("color","red");//可以不用循环处理多个元素
```
### 全选择器（*选择器）
jQuery中我们可以通过传递*选择器来选中文档页面中的元素。  
**语法：**  
*$( "*" )*

原生方法兼容性问题：
- IE会将注释节点实现为元素，所以在IE中调用getElementsByTagName里面会包含注释节点，这个通常是不应该的
- getElementById的参数在IE8及较低的版本不区分大小写
- IE7及较低的版本中，表单元素中，如果表单A的name属性名用了另一个元素B的ID名并且A在B之前，那么getElementById会选中A
- IE8及较低的版本，浏览器不支持getElementsByClassName

### 层级选择器
文档中的所有的节点之间都是有这样或者那样的关系。我们可以把节点之间的关系可以用传统的家族关系来描述，可以把文档树当作一个家谱，那么节点与节点直接就会存在父子，兄弟，祖孙的关系了。  
选择器中的层级选择器就是用来处理这种关系。  

**各种层级选择器：**  
![image](http://img.mukewang.com/5590e98b0001f60d06130229.jpg)
```
<div class = "left">
    <div class = "a">
        <p>div下的第一个p元素</p>
    </div>
    <div class = "a">
        <p>div下的第一个p元素</p>
    </div>
</div>
<div class = "right">
    <div class = "b">
        <a>
            <p>div下的第一个p元素</p>
        </a>
    </div>
    <div class = "b">
        <a>
            <p>div下的第一个p元素</p>
        </a>
    </div>
</div>
<div>div</div>
<script>
    //子选择器,选择所有div元素里的子元素p
    $("div > p").css("color","red");
    //后代选择器,选择所有div元素里面的元素p
    $("div p").css("backgroundColor","#CCC");
    //相邻兄弟选择器，选择.left后的第一个div兄弟节点
    $(".left + div").css("backgroundColor","#CCC");
    //一般兄弟选择器，选择.left后的所有div兄弟节点
    $(".left ~ div").css("backgroundColor","#CCC");
</script>
```

### 基本筛选选择器
jQuery提供了一系列的筛选选择器用来更快捷的找到所需的DOM元素。筛选选择器很多都不是CSS的规范，而是jQuery自己为了开发者的便利延展出来的选择器。  

筛选选择器的用法与CSS中的伪元素相似，选择器用冒号“：”开头：  
![image](http://img.mukewang.com/57cd1df2000146de06020498.jpg)
- :eq(), :lt(), :gt(), :even, :odd 用来筛选他们前面的匹配表达式的集合元素，根据之前匹配的元素在进一步筛选，注意jQuery合集都是从0开始索引
- gt是一个段落筛选，从指定索引的下一个开始，gt(1) 实际从2开始
```

<h3>:eq/:gt/:lt</h3>
<div class="left">
    <div class="aaron">
        <p>:lt(3)</p>
    </div>
    <div class="aaron">
        <p>:lt(3)</p>
    </div>
    <div class="aaron">
        <p>:eq(2)</p>
    </div>
    <div class="aaron">
    </div>
    <div class="aaron">
        <p>:gt(3)</p>
    </div>
    <div class="aaron">
        <p>:gt(3)</p>
    </div>
</div>

<script type="text/javascript">
    //找到第一个div
    $(".aaron:first").css("color", "#CD00CD");
    </script>
    
    <script type="text/javascript">
    //找到最后一个div
    $(".aaron:last").css("color", "#CD00CD");
    </script>
    
    <script type="text/javascript">
    //:even 选择所引值为偶数的元素，从 0 开始计数
    $(".aaron:even").css("border", "3px groove red");
    </script>
    
    <script type="text/javascript">
    //:odd 选择所引值为奇数的元素，从 0 开始计数
    $(".aaron:odd").css("border", "3px groove blue");

    //:eq
    //选着单个
    $(".aaron:eq(2)").css("border", "3px groove blue");

    //:gt 选择匹配集合中所有索引值大于给定index参数的元素
    $(".aaron:gt(3)").css("border", "3px groove blue");

    //:lt 选择匹配集合中所有索引值小于给定index参数的元素
    //与:gt相反
    $(".aaron:lt(2)").css("color", "#CD00CD");
</script>
```

### 内容筛选选择器
![image](http://img.mukewang.com/57cd20bf0001a97f05290214.jpg)
- :contains与:has都有查找的意思，但是contains查找包含“指定文本”的元素，has查找包含“指定元素”的元素
- 如果:contains匹配的文本包含在元素的子元素中，同样认为是符合条件的。
- :parent与:empty是相反的，两者所涉及的子元素，包括文本节点

### 可见性筛选选择器
![image](http://img.mukewang.com/5590f6de0001e2b204460106.jpg)  
- **:hidden选择器，不仅仅包含样式是display="none"的元素，还包括隐藏表单、visibility等等**
- **如果元素中占据文档中一定的空间,元素被认为是可见的。可见元素的宽度或高度，是大于零。元素的visibility: hidden 或 opacity: 0被认为是可见的，因为他们仍然占用空间布局。**
- **不在文档中的元素是被认为是不可见的，如果当他们被插入到文档中，jQuery没有办法知道他们是否是可见的，因为元素可见性依赖于适用的样式**

### 属性筛选选择器
属性选择器让你可以基于属性来定位一个元素。可以只指定该元素的某个属性，这样所有使用该属性而不管它的值，这个元素都将被定位，也可以更加明确并定位在这些属性上使用特定值的元素，这就是属性选择器展示它们的威力的地方。  
![image](http://img.mukewang.com/57d654200001c46507360560.jpg)  
在这么多属性选择器中[attr="value"]和[attr*="value"]是最实用的。  
- [attr="value"]能帮我们定位不同类型的元素，特别是表单form元素的操作，比如说input[type="text"],input[type="checkbox"]等  
- [attr*="value"]能在网站中帮助我们匹配不同类型的文件
```
<script type="text/javascript">
    //查找所有div中，属性name=p1的div元素
    $('div[name=p1]').css("border", "3px groove red"); 
</script>
```

### 子元素筛选选择器
子元素筛选选择器不常使用，其筛选规则比起其它的选择器稍微要复杂点。  
![image](http://img.mukewang.com/559105da0001301105960331.jpg)
- :first只匹配一个单独的元素，但是:first-child选择器可以匹配多个：即为每个父级元素匹配第一个子元素。这相当于:nth-child(1)
- :last 只匹配一个单独的元素， :last-child 选择器可以匹配多个元素：即，为每个父级元素匹配最后一个子元素
- 如果子元素只有一个的话，:first-child与:last-child是同一个
-  :only-child匹配某个元素是父元素中唯一的子元素，就是说当前子元素是父元素中唯一的元素，则匹配
- jQuery实现:nth-child(n)是严格来自CSS规范，所以n值是“索引”，也就是说，**从1开始计数**，:nth-child(index)从1开始的，而eq(index)是从0开始的
- nth-child(n) 与 :nth-last-child(n) 的区别前者是从前往后计算，后者从后往前计算  

### 表单元素选择器
jQuery中专门加入了表单选择器，从而能够极其方便地获取到某个类型的表单元素  
![image](http://img.mukewang.com/5592040d0001f8eb04940441.jpg)  
**除了input筛选选择器，几乎每个表单类别筛选器都对应一个input元素的type值。大部分表单类别筛选器可以使用属性筛选器替换。比如 $(':password') == $('[type=password]')**  

### 表单对象属性筛选选择器
除了表单元素选择器外，表单对象属性筛选选择器也是专门针对表单元素的选择器，可以附加在其他选择器的后面，主要功能是对所选择的表单元素进行筛选  
![image](http://img.mukewang.com/55920c2f0001198b04940201.jpg)  
- 选择器适用于复选框和单选框，对于下拉框元素, 使用 :selected 选择器
- 在某些浏览器中，选择器:checked可能会错误选取到<option>元素，所以保险起见换用选择器input:checked，确保只会选取<input>元素  

## jQuery的属性与样式

### .attr()与.removeAttr()  
操作特性的DOM方法主要有3个，getAttribute方法、setAttribute方法和removeAttribute方法，就算如此在实际操作中还是会存在很多问题，这里先不说。而在jQuery中用一个attr()与removeAttr()就可以全部搞定了，包括兼容问题。  

**.attr()有4个表达式：**  
- attr(传入属性名)：获取属性的值
- attr(属性名, 属性值)：设置属性的值
- attr(属性名,函数值)：设置属性的函数值
- attr(attributes)：给指定元素设置多个属性值，即：{属性名一: “属性值一” , 属性名二: “属性值二” , … … }  

**.removeAttr()删除方法**
- .removeAttr( attributeName ) : 为匹配的元素集合中的每个元素中移除一个属性（attribute）

dom中有个概念的区分：**Attribute和Property**翻译出来都是“属性”，《js高级程序设计》书中翻译为“特性”和“属性”。   
简单理解，Attribute就是dom节点自带的属性,如：html中常用的id、class、title、align等  
而Property是这个DOM元素作为对象，其附加的内容，例如,tagName, nodeName, nodeType,, defaultChecked, 和 defaultSelected 使用.prop()方法进行取值或赋值等  
**获取Attribute就需要用attr，获取Property就需要用prop**  

### .html()及.text()  
读取、修改元素的html结构或者元素的文本内容是常见的DOM操作，jQuery针对这样的处理提供了2个便捷的方法.html()与.text()  

#### .html()方法
获取集合中第一个匹配元素的HTML内容 或 设置每一个匹配元素的html内容，具体有3种用法：  
1. .html() 不传入值，就是获取集合中第一个匹配元素的HTML内容
2. .html( htmlString )  设置每一个匹配元素的html内容
3. .html( function(index, oldhtml) ) 用来返回设置HTML内容的一个函数

.html()方法内部使用的是DOM的innerHTML属性来处理的，所以在设置与获取上需要注意的一个最重要的问题，这个操作是**针对整个HTML内容**（不仅仅只是文本内容）  

#### .text()方法
得到匹配元素集合中每个元素的文本内容结合，包括他们的后代，或设置匹配元素集合中每个元素的文本内容为指定的文本内容。，具体有3种用法：  
1. .text() 得到匹配元素集合中每个元素的合并文本，包括他们的后代
2. .text( textString ) 用于设置匹配元素内容的文本
3. .text( function(index, text) ) 用来返回设置文本内容的一个函数

**.text()结果返回一个字符串，包含所有匹配元素的合并文本**  

#### 异同点
- .html与.text的方法操作是一样，只是在具体针对处理对象不同
- .html处理的是元素内容，.text处理的是文本内容
- .html只能使用在HTML文档中，.text 在XML 和 HTML 文档中都能使用
- 如果处理的对象只有一个子文本节点，那么html处理的结果与text是一样的
- 火狐不支持innerText属性，用了类似的textContent属性，.text()方法综合了2个属性的支持，所以可以兼容所有浏览器  

### .val()  
.val()方法主要是用于处理表单元素的值，比如 input, select 和 textarea。  
1. .val()无参数，获取匹配的元素集合中第一个元素的当前值
2. .val( value )，设置匹配的元素集合中每个元素的值
3. .val( function ) ，一个用来返回设置值的函数

- ==通过.val()处理select元素， 当没有选择项被选中，它返回null==
- ==.val()方法多用来设置表单的字段的值==
- ==如果select元素有multiple（多选）属性，并且至少一个选择项被选中， .val()方法返回一个数组，这个数组包含每个选中选择项的值==

### 增加样式.addClass()
.addClass()方法，用于动态增加class类名  
1. .addClass( className ) : 为每个匹配元素所要增加的一个或多个样式名
2. .addClass( function(index, currentClass) ) : 这个函数返回一个或更多用空格隔开的要增加的样式名  

**.addClass()方法不会替换一个样式类名。它只是简单的添加一个样式类名到元素上**  
```
<p class="orgClass">
$("p").addClass("newClass");//class="orgClass newClass"
```

### 删除样式.removeClass()
如果需要样式之间的切换，同样jQuery提供了一个很方便的.removeClass()，它的作用是从匹配的元素中删除全部或者指定的class。  

1. .removeClass( [className ] )：每个匹配元素移除的一个或多个用空格隔开的样式名
2. .removeClass( function(index, class) ) ： 一个函数，返回一个或多个将要被移除的样式名

**如果一个样式类名作为一个参数,只有这样式类会被从匹配的元素集合中删除 。 如果没有样式名作为参数，那么所有的样式类将被移除**  

### 切换样式.toggleClass()
在做某些效果的时候，可能会针对同一节点的某一个样式不断的切换，也就是addClass与removeClass的互斥切换，比如隔行换色效果。  

jQuery提供一个toggleClass方法用于简化这种互斥的逻辑，通过toggleClass方法动态添加删除Class，一次执行相当于addClass，再次执行相当于removeClass  

.toggleClass()：在匹配的元素集合中的每个元素上添加或删除一个或多个样式类,取决于这个样式类是否存在或值切换属性。即：如果存在（不存在）就删除（添加）一个类。

1. .toggleClass( className )：在匹配的元素集合中的每个元素上用来切换的一个或多个（用空格隔开）样式类名
2. .toggleClass( className, switch )：一个布尔值，用于判断样式是否应该被添加或移除
3. .toggleClass( [switch ] )：一个用来判断样式类添加还是移除的 布尔值
4. .toggleClass( function(index, class, switch) [, switch ] )：用来返回在匹配的元素集合中的每个元素上用来切换的样式类名的一个函数。接收元素的索引位置和元素旧的样式类作为参数

### 样式操作.css()
.css() 方法：获取元素样式属性的计算值或者设置元素的CSS属性。  

获取：  
- .css( propertyName ) ：获取匹配元素集合中的第一个元素的样式属性的计算值
- .css( propertyNames )：传递一组数组，返回一个对象结果  

设置：
-  .css(propertyName, value )：设置CSS
- .css( propertyName, function )：可以传入一个回调函数，返回取到对应的值进行处理
- .css( properties )：可以传一个对象，同时设置多个样式

注：
-  .css(propertyName, value )：设置CSS
- .css( propertyName, function )：可以传入一个回调函数，返回取到对应的值进行处理
- .css( properties )：可以传一个对象，同时设置多个样式  

### .css()与.addClass()设置样式的区别
#### 可维护性
.addClass()的本质是通过定义个class类的样式规则，给元素添加一个或多个类。css方法是通过JavaScript大量代码进行改变元素的样式  

通过.addClass()我们可以批量的给相同的元素设置统一规则，变动起来比较方便，可以统一修改删除。如果通过.css()方法就需要指定每一个元素是一一的修改，日后维护也要一一的修改，比较麻烦  
#### 灵活性
通过.css()方式可以很容易动态的去改变一个样式的属性，不需要在去繁琐的定义个class类的规则。一般来说在不确定开始布局规则，通过动态生成的HTML代码结构中，都是通过.css()方法处理的
#### 样式值
.addClass()本质只是针对class的类的增加删除，不能获取到指定样式的属性的值，.css()可以获取到指定的样式值。
#### 样式的优先级
css的样式是有优先级的，当外部样式、内部样式和内联样式同一样式规则同时应用于同一个元素的时候，优先级如下：  

*外部样式 < 内部样式 < 内联样式*  
- .addClass()方法是通过增加class名的方式，那么这个样式是在外部文件或者内部样式中先定义好的，等到需要的时候在附加到元素上
- 通过.css()方法处理的是内联样式，直接通过元素的style属性附加到元素上的  

**通过.css方法设置的样式属性优先级要高于.addClass方法**

### 元素的数据存储
jQuery提供的存储接口：
```
jQuery.data( element, key, value )   //静态接口,存数据
jQuery.data( element, key )  //静态接口,取数据   
.data( key, value ) //实例接口,存数据
.data( key ) //实例接口,存数据
```
例子：
```
<script type="text/javascript">
    $('.left').click(function() {
        var ele = $(this);
        //通过$.data方式设置数据
        $.data(ele, "a", "data test")
        $.data(ele, "b", {
            name : "慕课网"
        })
        //通过$.data方式取出数据
        var reset = $.data(ele, "a") + "</br>" + $.data(ele, "b").name
        ele.find('span').append(reset)
    })
    </script>
    <script type="text/javascript">
    $('.right').click(function() {
        var ele = $(this);
        //通过.data方式设置数据
        ele.data("a", "data test")
        ele.data("b", {
            name: "慕课网"
        })
        //通过.data方式取出数据
        var reset = ele.data("a") + "</br>" + ele.data("b").name
        ele.find('span').append(reset)
    })
    </script>
```

 
 ---
 
 此页面为本人学习慕课网JQuery基础的学习笔记，原地址为：https://www.imooc.com/learn/418  
 