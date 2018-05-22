# JavaScript基础复习--进阶篇（四）

## 浏览器对象模型（BOM）

### window对象
window对象是BOM的核心，window对象指**当前的浏览器窗口**。  
  
window对象方法：  
![image](http://img.mukewang.com/535483720001a54506670563.jpg)

### JS计时器
在JavaScript中，我们可以在设定的时间间隔之后来执行代码，而不是在函数被调用后立即执行。
- 一次性计时器：仅在指定的延迟时间之后触发一次。
- 间隔性触发计时器：每隔一定的时间间隔就触发一次。

计时器方法：  
![image](http://img.mukewang.com/56976e1700014fc504090143.jpg)

#### 计时器（setInterval()）
在执行时,从载入页面后每隔指定的时间执行代码。返回一个可以传递给 clearInterval() 从而取消对"代码"的周期性执行的值。  
**语法为：**  
*setInterval(代码,交互时间);*  
**交互时间以毫秒为单位**  
```
var int=setInterval(clock, 100)//每隔100毫秒调用clock()函数，并将时间显示出来
function clock(){
    var time=new Date();
    document.getElementById("clock").value = time;
}
```

#### 取消计时器（clearInterval()）
clearInterval() 方法可取消由 setInterval() 设置的交互时间。   
**语法为：**  
*clearInterval(id_of_setInterval)*  
id_of_setInterval：由 setInterval() 返回的 ID 值。
```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>计时器</title>
<script type="text/javascript">
   function clock(){
    var time=new Date();                     
    document.getElementById("clock").value = time;
   }
// 每隔100毫秒调用clock函数，并将返回值赋值给i
var i=setInterval("clock()",100);
</script>
</head>
<body>
  <form>
    <input type="text" id="clock" size="50"  />
    <input type="button" value="Stop" onclick="clearInterval(i)"  />
  </form>
</body>
</html>
``` 

#### 延迟计时（setTimeout()）
setTimeout()计时器，在载入后延迟指定时间后,去执行一次表达式,仅执行一次。  
**语法为：**  
*setTimeout(代码,延迟时间);*  
延迟时间以毫秒为单位
```
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
  //页面打开3秒后弹出对话框
  setTimeout("alert('Hello!')", 3000 );
</script>
</head>
<body>
</body>
</html>
```

#### 停止延迟计时（clearTimeout()）
setTimeout()和clearTimeout()一起使用，停止计时器。  
**语法为：**  
*clearTimeout(id_of_setTimeout)*  
id_of_setTimeout：由 setTimeout() 返回的 ID 值。该值标识要取消的延迟执行代码块。

```
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
  var num=0,i;
  function timedCount(){
    document.getElementById('txt').value=num;
    num=num+1;
    i=setTimeout(timedCount,1000);
  }
    setTimeout(timedCount,1000);
  function stopCount(){
    clearTimeout(i);
  }
</script>
</head>
<body>
  <form>
    <input type="text" id="txt">
    <input type="button" value="Stop" onClick="stopCount()">
  </form>
</body>
</html>
```

### History对象
history对象记录了用户曾经浏览过的页面(URL)，并可以实现浏览器前进与后退相似导航的功能。**从窗口被打开的那一刻开始记录，每个浏览器窗口、每个标签页乃至每个框架，都有自己的history对象与特定的window对象关联。**  
**语法为：**  
*window.history.[属性|方法]*
window可以省略  

属性：  
![image](http://img.mukewang.com/53548c030001759e05840068.jpg)  
方法：  
![image](http://img.mukewang.com/53548c200001228206210123.jpg)  
```
<script type="text/javascript">
  var HL = window.history.length;
  document.write(HL);
</script>
```

#### 返回前一个浏览的页面（back()）
back()方法，加载 history 列表中的前一个 URL。  
**语法为：**  
*window.history.back();*  
back()相当于go(-1)

#### 返回下一个浏览的页面（forward()）
forward()方法，加载 history 列表中的下一个 URL。  
**语法为：**   
*window.history.forward();*  
forward()相当于go(1)

#### 返回浏览历史中的其他页面（go()）
go()方法，根据当前所处的页面，加载 history 列表中的某个具体的页面。  
**语法为：**  
*window.history.go(number);*  
当参数为1、0、-1时，表示前一个、当前、后一个页面。当为其他时，为在url列表的相应位置。

### Location对象
location用于获取或设置窗体的URL，并且可以用于解析URL。  
**语法为：**  
*location.[属性|方法]*  

属性：  
![image](http://img.mukewang.com/5354b1d00001c4ec06220271.jpg)  
属性图示：  
![image](http://img.mukewang.com/53605c5a0001b26909900216.jpg)  
方法：  
![image](http://img.mukewang.com/5354b1eb00016a2405170126.jpg)  

```
document.write(location.href);//显示当前页面URl
```

### Navigator对象
Navigator 对象包含有关浏览器的信息，通常用于检测浏览器与操作系统的版本。  
属性：  
![image](http://img.mukewang.com/5354cff70001428b06880190.jpg)

```
var bro = navigator.appName;//浏览器名称
var bVersion = navigator.appVersion;//浏览器版本
```

#### userAgent属性
返回用户代理头的字符串表示(就是包括浏览器版本信息等的字符串)  
**语法为：**  
*navigator.userAgent*   
```
function validB(){ //查看浏览器版本
    var u_agent = navigator.userAgent; 
    var B_name="Failed to identify the browser"; 
    if(u_agent.indexOf("Firefox")>-1){ 
        B_name="Firefox"; 
    }else if(u_agent.indexOf("Chrome")>-1){ 
        B_name="Chrome"; 
    }else if(u_agent.indexOf("MSIE")>-1&&u_agent.indexOf("Trident")>-1){ 
    B_name="IE(8-10)";  
    }
    document.write("B_name:"+B_name+"<br>");
    document.write("u_agent:"+u_agent+"<br>"); 
}
```

### screen对象
screen对象用于获取用户的屏幕信息。  
**语法为：**  
*window.screen.属性*  

属性：  
![image](http://img.mukewang.com/5354d2810001a47706210213.jpg)

#### 屏幕分辨率的高和宽
- screen.height 返回屏幕分辨率的高
- screen.width 返回屏幕分辨率的宽

其中，单位以像素计；window.screen 对象在编写时可以不使用 window 这个前缀。

```
<script type="text/javascript">
  document.write( "屏幕宽度："+screen.width+"px<br />" );
  document.write( "屏幕高度："+screen.height+"px<br />" );
</script>
```

#### 屏幕可用高和宽度
-  screen.availWidth 属性返回访问者屏幕的宽度，以像素计，减去界面特性，比如任务栏。
-  screen.availHeight 属性返回访问者屏幕的高度，以像素计，减去界面特性，比如任务栏。

```
<script type="text/javascript">
document.write("可用宽度：" + screen.availWidth);
document.write("可用高度：" + screen.availHeight);
</script>
```

## 文档对象模型（DOM）
文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。  

### getElementsByName()方法
返回带有指定名称的节点对象的**集合（数组）**。与getElementById() 方法不同的是，通过元素的 name 属性查询元素，而不是通过 id 属性。  
**语法为：**  
*document.getElementsByName(name)*  

### getElementsByTagName()方法
返回带有指定标签名的节点对象的**集合（数组）**。返回元素的顺序是它们在文档中的顺序。Tagname是标签的名称，如p、a、img等标签名。  
**语法为：**  
*document.getElementsByName(name)*   

### getAttribute()方法
通过元素节点的属性名称获取属性的值。  
**语法为：**  
*elementNode.getAttribute(name)*  

注：
- elementNode：使用getElementById()、getElementsByTagName()等方法，获取到的元素节点。
- name：要想查询的元素节点的属性名字

### setAttribute()方法
setAttribute() 方法增加一个指定名称和值的新属性，或者把一个现有的属性设定为指定的值。  
**语法为：**  
*elementNode.setAttribute(name,value)*  

注：  
- 把指定的属性设置为指定的值。如果不存在具有指定名称的属性，该方法将创建一个新属性。
- 类似于getAttribute()方法，setAttribute()方法只能通过元素节点对象调用的函数。

### 节点属性
在文档对象模型 (DOM) 中，每个节点都是一个对象。DOM 节点有三个重要的属性 ：  
1. nodeName : 节点的名称
2. nodeValue ：节点的值
3. nodeType ：节点的类型

#### nodeName属性
nodeName为节点的名称，是只读的。  
1. 元素节点的 nodeName 与标签名相同
2. 属性节点的 nodeName 是属性的名称
3. 文本节点的 nodeName 永远是 #text
4. 文档节点的 nodeName 永远是 #document

#### nodeValue属性
nodeValue为节点的值
1. 元素节点的 nodeValue 是 undefined 或 null
2. 文本节点的 nodeValue 是文本自身
3. 属性节点的 nodeValue 是属性的值

#### nodeType属性
nodeType为节点的类型，是只读的。以下常用的几种结点类型:  

元素类型 | 节点类型
---|---
元素 | 1
属性 | 2
文本 | 3
注释 | 8
文档 | 9

### 访问子节点childNodes
访问选定元素节点下的所有子节点的列表，返回的值可以看作是一个数组，他具有length属性。如果选定的节点没有子节点，则该属性返回不包含节点的 NodeList。  
**语法**  
*elementNode.childNodes*  

### 访问子节点的第一和最后项

#### firstChild
firstChild 属性返回‘childNodes’数组的第一个子节点。如果选定的节点没有子节点，则该属性返回 NULL。  
与elementNode.childNodes[0]是同样的效果。   
**语法：**  
*node.firstChild*  

###语法lastChild
lastChild 属性返回‘childNodes’数组的最后一个子节点。如果选定的节点没有子节点，则该属性返回 NULL。  
与elementNode.childNodes[elementNode.childNodes.length-1]是同样的效果。   
**语法：**
*node.lastChild*  

### 访问父节点parentNode
获取指定节点的父节点。**注意:父节点只能有一个。**  
**语法：**  
*elementNode.parentNode*  
**访问祖节点**  
*elementNode.parentNode.parentNode*  

### 访问兄弟节点
- nextSibling 属性可返回某个节点之后紧跟的节点（处于同一树层级中）。如果无此节点，则该属性返回 null。  
**语法：**  
*nodeObject.nextSibling*  
- previousSibling 属性可返回某个节点之前紧跟的节点（处于同一树层级中）。如果无此节点，则该属性返回 null。
**语法：**  
*nodeObject.previousSibling*  

**两个属性获取的是节点。Internet Explorer 会忽略节点间生成的空白文本节点（例如，换行符号），而其它浏览器不会忽略。**  

**解决方法：  
判断节点nodeType是否为1, 如是为元素节点，跳过。**

### 插入节点appendChild()
在指定节点的最后一个子节点列表之后添加一个新的子节点。  
**语法：**  
*elementNode.appendChild(newnode)*  
newnode为追加的节点  

### 插入节点insertBefore()
insertBefore() 方法可在已有的子节点前插入一个新的子节点。  
**语法：**  
*elementNode.insertBefore(newnode,node);*  
newnode: 要插入的新节点。node: 指定此节点前插入节点。  

### 删除节点removeChild()   
removeChild() 方法从子节点列表中删除某个节点。如删除成功，此方法可返回被删除的节点，如失败，则返回 NULL。  
**语法：**  
*nodeObject.removeChild(node)*  
node ：必需，指定需要删除的节点。

### 替换元素节点replaceChild()
replaceChild 实现子节点(对象)的替换。返回被替换对象的引用。  
**语法：**  
*node.replaceChild (newnode,oldnode )*  

### 创建元素节点createElement
createElement()方法可创建元素节点。此方法可返回一个 Element 对象。要**与appendChild() 或 insertBefore()方法联合使用**，将元素显示在页面中。  
**语法：**  
*document.createElement(tagName)*

### 创建文本节点createTextNode
createTextNode() 方法创建新的文本节点，返回新创建的 Text 节点。  
**语法**  
*document.createTextNode(data)*  
data : 字符串值，可规定此节点的文本。  

### 浏览器窗口可是区域大小
获得浏览器窗口的尺寸（浏览器的视口，不包括工具栏和滚动条）的方法:  

**一、对于IE9+、Chrome、Firefox、Opera 以及 Safari：**
- window.innerHeight - 浏览器窗口的内部高度
- window.innerWidth - 浏览器窗口的内部宽度

**二、对于 Internet Explorer 8、7、6、5：**  
- document.documentElement.clientHeight表示HTML文档所在窗口的当前高度。
- document.documentElement.clientWidth表示HTML文档所在窗口的当前宽度。

**三、通用**  
- document.body.clientHeight
- document.body.clientWidth 

通用方法：
```
var w= document.documentElement.clientWidth
      || document.body.clientWidth;
var h= document.documentElement.clientHeight
      || document.body.clientHeight;
```

### 网页尺寸scrollHeight/scrollWidth
scrollHeight和scrollWidth，获取网页内容高度和宽度。  
scrollHeight和scrollWidth还可获取Dom元素中内容实际占用的高度和宽度。  

**一、针对IE、Opera:**  

scrollHeight 是**网页内容实际高度**，可以小于 clientHeight。  

**二、针对NS、FF:**  

scrollHeight 是网页内容高度，不过最小值是 clientHeight。**也就是说网页内容实际高度小于 clientHeight 时，scrollHeight 返回 clientHeight 。**  
  
  
通用方法：  
```
var w=document.documentElement.scrollWidth
   || document.body.scrollWidth;
var h=document.documentElement.scrollHeight
   || document.body.scrollHeight;
```

### 网页尺寸offsetHeight/offsetWidth
offsetHeight和offsetWidth，获取网页内容高度和宽度(**包括滚动条等边线，会随窗口的显示大小改变**)。  
*offsetHeight = clientHeight + 滚动条 + 边框。*  

通用方法：
```
var w= document.documentElement.offsetWidth
    || document.body.offsetWidth;
var h= document.documentElement.offsetHeight
    || document.body.offsetHeight;
```

### 网页卷去的距离与偏移量
![image](http://img.mukewang.com/5347b2b10001e1a307520686.jpg)
- scrollLeft:设置或获取位于给定对象左边界与窗口中目前可见内容的最左端之间的距离 ，即左边灰色的内容。  
- scrollTop:设置或获取位于对象最顶端与窗口中可见内容的最顶端之间的距离 ，即上边灰色的内容。  
- offsetLeft:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算左侧位置 。  
- offsetTop:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算顶端位置 。 


---

次页面为本人学习慕课网JavaScript进阶篇的的个人学习笔记。原地址为 https://www.imooc.com/learn/10