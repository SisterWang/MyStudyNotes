# JavaScript基础复习--进阶篇（四）

## 浏览器对象（BOM）

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

## 文档对象（DOM）
未完待续...

---

次页面为本人学习慕课网JavaScript进阶篇的的个人学习笔记。原地址为https://www.imooc.com/learn/10