# JQuery基础学习（二）--DOM
## 原生JS添加节点
- 创建元素：document.createElement
- 设置属性：setAttribute
- 添加文本：innerHTML
- 加入文档：appendChild

示例：
```
//创建2个div元素
var rightdiv = document.createElement('div')
var rightaaron = document.createElement("div");

//给2个div设置不同的属性
rightdiv.setAttribute('class', 'right')
rightaaron.className = 'aaron'
rightaaron.innerHTML = "动态创建DIV元素节点";

//2个div合并成包含关系
rightdiv.appendChild(rightaaron)
		   	
//绘制到页面body
body.appendChild(rightdiv)    
```
此过程十分繁琐且需要考虑众多兼容性问题，而jQuery给出了一套非常完美的接口方法。

## DOM节点创建

### 节点创建与属性的处理

#### 创建元素节点
**语法：**  
*$("< div>< /div>")*  

#### 创建文本节点
与创建元素节点类似，可以直接把文本内容一并描述  
**语法：**  
*$("< div>我是文本节点< /div>")*  

#### 创建为属性节点
**语法为：**  
*$("< div id='test' class='aaron'>我是文本节点< /div>")*  

**通过以上方法改造上一节的代码：**
```
//只需要两条代码
//创建节点
$("<div class='right'><div class='aaron'>动态创建DIV元素节点</div></div>");
//插入节点
$body.append(div);
```

## DOM节点的插入

### DOM内部插入  

#### append()与appendTo()
动态创建的元素是不够的，它只是临时存放在内存中，最终我们需要放到页面文档并呈现出来。这里就涉及到一个位置关系，常见的就是把这个新创建的元素，**当作页面某一个元素的子元素放到其内部**。针对这样的处理，jQuery就定义2个操作的方法：  

**语法：**  
*.append(content)*  
*.appendTo(content)*

- append：这个操作与对指定的元素执行原生的appendChild方法，将它们添加到文档中的情况类似。
- appendTo：实际上，使用这个方法是颠倒了常规的$(A).append(B)的操作，即不是把B追加到A中，而是把A追加到B中。

#### prepend()与prependTo()
在元素内部进行操作的方法，除了在被选元素的结尾（仍然在内部）通过append与appendTo插入指定内容外，相应的还可以在被选元素之前插入，jQuery提供的方法是prepend与prependTo
![image](http://img.mukewang.com/57481c3900013c6e05000193.jpg)

#### 四个内部插入方法的区别：
- append()向每个匹配的元素内部追加内容
- prepend()向每个匹配的元素内部前置内容
- appendTo()把所有匹配的元素追加到另一个指定元素的集合中，**不支持多参数**
- prependTo()把所有匹配的元素前置到另一个指定的元素集合中，**不支持多参数**

### DOM外部插入

#### after()与before()  
兄弟之间的关系处理，jQuery引入了2个方法，可以用来在匹配I的元素前后插入内容  ![image](http://img.mukewang.com/57481b6b00018e3405210197.jpg)

- before与after都是用来对相对选中元素外部增加相邻的兄弟节点
- 2个方法都是都可以接收HTML字符串，DOM 元素，元素数组，或者jQuery对象，用来插入到集合中每个匹配元素的前面或者后面
- 2个方法都支持多个参数传递after(div1,div2,....) 可以参考右边案例代码  

#### insertAfter()与insertBefore()
![image](http://img.mukewang.com/57481d230001b0f305170241.jpg)  
**这两个方法不支持多参数处理**  
- .before()和.insertBefore()实现同样的功能。主要的区别是语法——内容和目标的位置。 对于before()选择表达式在函数前面，内容作为参数，而.insertBefore()刚好相反，内容在方法前面，它将被放在参数里元素的前面
- .after()和.insertAfter() 实现同样的功能。主要的不同是语法——特别是（插入）内容和目标的位置。 对于after()选择表达式在函数的前面，参数是将要插入的内容。对于 .insertAfter(), 刚好相反，内容在方法前面，它将被放在参数里元素的后面
- before、after与insertBefore。insertAfter的除了目标与位置的不同外，后面的不支持多参数处理  

## DOM节点的删除

### empty()的基本用法
empty 顾名思义，清空方法，但是与删除又有点不一样，因为它只移除了**指定元素中的所有子节点**。  

这个方法不仅移除子元素（和其他后代元素），同样移除元素里的文本。  

**语法：**  
*content.empty()*

### remove()的有参用法和无参用法
remove与empty一样，都是移除元素的方法，但是remove会将元素**自身移除，同时也会移除元素内部的一切**，包括绑定的事件及与该元素相关的jQuery数据。  

如果不通过remove方法删除这个节点其实也很简单，但是同时需要把事件给销毁掉，这里是为了防止"内存泄漏"，所以前端开发者一定要注意，绑了多少事件，不用的时候一定要记得销毁。  

通过remove方法移除div及其内部所有元素，remove内部会自动操作事件销毁方法，所以使用使用起来非常简单。

```
//通过remove处理
$('.hello').remove();
//结果：<div class="hello"> <p>被移除</p></div> 全部被移除
//节点不存在了,同事事件也会被销毁
```

#### remove()的有参用法
remove比empty好用的地方就是可以传递一个选择器表达式用来过滤将被移除的匹配元素集合，可以选择性的删除指定的节点
```
$("p").remove(":contains(3)");
//或：
$("p").filter(":contains('3')").remove();
```

### 保留数据的删除操作detach()
如果我们希望临时删除页面上的节点，但是又**不希望节点上的数据与事件丢失**，并且**能在下一个时间段让这个删除的节点显示到页面**，这时候就可以使用detach方法来处理  

detach从字面上就很容易理解。让一个web元素托管。即从当前页面中移除该元素，但保留这个元素的内存模型对象（依然保存在内存中）。
```
//托管 p
var p = $("p").detach();
//添加 p
$("body").append(p);
```
**detach方法是JQuery特有的，所以它只能处理通过JQuery的方法绑定的事件或者数据**

## DOM节点的复制与替换

### 拷贝clone()
克隆节点是DOM的常见操作，jQuery提供一个clone方法，专门用于处理dom的克隆  

**clone()方法**：复制所有匹配的元素集合，包括所有匹配元素、匹配元素的下级元素、文字节点。如果节点有事件或者数据之类的其他处理，我们需要通过clone(ture)传递一个布尔值ture用来指定，这样不仅仅只是克隆单纯的节点结构，还要把附带的事件与数据给一并克隆了
```
//clone处理一
$("div").clone()   //只克隆了结构，事件丢失

//clone处理二
$("div").clone(true) //结构、事件与数据都克隆
```
- clone()方法时，在将它插入到文档之前，我们可以修改克隆后的元素或者元素内容，如右边代码我 $(this).clone().css('color','red') 增加了一个颜色
- 通过传递true，将所有绑定在原始元素上的事件处理函数复制到克隆元素上
- clone()方法是jQuery扩展的，只能处理通过jQuery绑定的事件与数据
- 元素数据（data）内对象和数组不会被复制，将继续被克隆元素和原始元素共享。深复制的所有数据，需要手动复制每一个

### 替换replaceWith()和replaceAll()
**.replaceWith( newContent )**：用提供的内容替换集合中所有匹配的元素并且返回被删除元素的集合  
**.replaceAll( target )** ：用集合的匹配元素替换每个目标元素  

```
$("p:eq(1)").replaceWith('<a style="color:red">替换第二段的内容</a>');
$('<a style="color:red">替换第二段的内容</a>').replaceAll('p:eq(1)');
```
- .replaceAll()和.replaceWith()功能类似，主要是目标和源的位置区别
- .replaceWith()与.replaceAll() 方法会删除与节点相关联的所有数据和事件处理程序
- .replaceWith()方法，和大部分其他jQuery方法一样，返回jQuery对象，所以可以和其他方法链接使用
- .replaceWith()方法返回的jQuery对象引用的是替换前的节点，而不是通过replaceWith/replaceAll方法替换后的节点

### 包裹wrap()
如果要将元素用其他元素包裹起来，也就是给它增加一个父元素，针对这样的处理，JQuery提供了一个wrap方法。  

**.wrap( wrappingElement )**：在集合中匹配的每个元素周围包裹一个HTML结构  
**.wrap( function )** ：一个回调函数，返回用于包裹匹配元素的 HTML 内容或 jQuery 对象
```
$('p').wrap('<div></div>')
//或
$('p').wrap(function() {
    return '<div></div>';   //与第一种类似，只是写法不一样
})
```
结果：
```
//在p之外包裹div
<div>
    <p>p元素</p>
</div>
```  

### 包裹unwrap()
jQuery提供了一个unwrap()方法 ，作用与wrap方法是相反的。将匹配元素集合的父级元素删除，保留自身（和兄弟元素，如果存在）在原来的位置。支持回调函数。  
```
$('p').unwrap();
```

### 包裹wrapAll()
**.wrapAll( wrappingElement )**：给集合中匹配的元素增加一个外面包裹HTML结构  
```
$('p').wrapAll('<div></div>')
```
给两个p元素增加了包裹：
```
<div>
    <p>p元素</p>
    <p>p元素</p>
</div>
```
**可以通过回调函数单独处理元素**：  
```
$('p').wrapAll(function() {
    return '<div><div/>'; 
})
```
为每个p元素都增加了包裹：
```
<div>
    <p>p元素</p>
</div>
<div>
    <p>p元素</p>
</div>
```

### 包裹wrapInner()
如果要将合集中的元素内部所有的子元素用其他元素包裹起来，并当作指定元素的子元素，针对这样的处理，JQuery提供了一个wrapInner方法。支持回调函数。  

**.wrapInner( wrappingElement )**：给集合中匹配的元素的内部，增加包裹的HTML结构  
```
$('div').wrapInner('<p></p>')
```
将每个div的内部元素用p包裹了起来：
```
<div>
    <p>曾经的div子元素</p>
</div>
<div>
    <p>曾经的div子元素</p>
</div>
```

##  jQuery遍历

### children()方法
jQuery是一个合集对象，如果想快速查找合集里面的第一级子元素，此时可以用children()方法。  

.children()方法选择性地接受同一类型选择器表达式
```
$("div").children(".selected")
```

### find()方法
jQuery是一个合集对象，如果想快速查找DOM树中的这些元素的后代元素，此时可以用find()方法，这也是开发**使用频率很高的方法**。  
**children是父子关系查找，find是后代关系（包含父子关系）**  

- find是遍历当前元素集合中每个元素的后代。只要符合，不管是儿子辈，孙子辈都可以。
- 与其他的树遍历方法不同，选择器表达式对于 .find() 是必需的参数。如果我们需要实现对所有后代元素的取回，可以传递通配选择器 '*'。
- find只在后代中遍历，不包括自己。
- 选择器 context 是由 .find() 方法实现的；因此，$('.item-ii').find('li') 等价于 $('li', '.item-ii')(找到类名为item-ii的标签下的li标签)。

```
//找到div的后代中最后一个 li并添加样式
$("div").find("li:last").css("color",red);
```

### parent()方法
jQuery是一个合集对象，如果想快速查找合集里面的**每一个元素的父元素**（这里可以理解为就是父亲-儿子的关系），此时可以用parent()方法。

**因为是父元素，这个方法只会向上查找一级**
```
$('.item-a').parent(':last').css('border', '1px solid blue');
```

### parents()方法

jQuery是一个合集对象，如果想快速查找合集里面的每一个元素的**所有祖辈**元素，此时可以用parents()方法。

**jQuery是一个合集对象，所以通过parent是匹配合集中所有元素的祖辈元素**  
- .parents()和.parent()方法是相似的，但后者只是进行了一个单级的DOM树查找
- $( "html" ).parent()方法返回一个包含document的集合，而$( "html" ).parents()返回一个空集合。
```
//找到当前元素的所有祖辈元素,筛选出class="first-div"的元素并且附上一个边
$('.item-b').parents('.first-div').css('border', '2px solid blue')
```

### closest()方法  
以选定的元素为中心，往内查找可以通过find、children方法。如果往上查找，也就是查找当前元素的父辈祖辈元素，jQuery提供了closest()方法，这个方法类似parents但是又有一些细微的区别，属于**使用频率很高的方法**。  

**closest()方法接受一个匹配元素的选择器字符串**  
```
$("div").closet("li')
```
**jQuery是一个合集对象，所以通过closest是匹配合集中每一个元素的祖先元素**  

和上面的方法一样，closest()方法也可以用选择器筛选。

### next()方法
jQuery是一个合集对象，如果想快速查找指定元素集合中每一个元素**紧邻的下一个同辈元素**的元素集合，此时可以用next()方法。

**jQuery是一个合集对象，所以通过next匹配合集中每一个元素的下一个兄弟元素**  

和上面的方法一样，next()方法也可以用选择器筛选。  

### prev()方法
jQuery是一个合集对象，如果想快速查找指定元素集合中每一个元素**紧邻的上一个同辈元素的元素集合**，此时可以用prev()方法。

**其他内容同上**

### siblings()方法
jQuery是一个合集对象，如果想快速查找指定元素集合中每一个元素的**同辈元素**，此时可以用siblings()方法。  

**其他内容同上**

### add()方法  
jQuery为此提供add方法，用来创建一个新的jQuery对象 ，元素添加到匹配的元素集合中。  

**.add()的参数可以几乎接受任何的$()，包括一个jQuery选择器表达式，DOM元素，或HTML片段引用**。  
```
//传递选择器
$('li').add('p');
//传递dom元素
$('li').add(document.getElementsByTagName('p')[0])
```

### each()方法  
.each() 方法就是一个for循环的迭代器，它会迭代jQuery对象合集中的每一个DOM元素。每次回调函数执行时，会传递当前循环次数作为参数(从0开始计数）  
- each是一个for循环的包装迭代器
- each通过回调的方式处理，并且会有2个固定的实参，索引与元素
- each回调方法中的this指向当前迭代的dom元素

示例：  
```
$("li").each(function(index, element) {
    //index 索引 0,1
    //element是对应的li节点 li,li
    //this 指向的是li
})
```

**如果需要提前退出，可以以通过返回 false以便在回调函数内中止循**  

---

此页面为本人学习慕课网jQuery基础的个人学习笔记，原地址为 https://www.imooc.com/learn/530