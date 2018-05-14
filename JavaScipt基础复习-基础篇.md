# JavaScipt基础复习-基础篇

---
##  准备工作
### 插入JavaScript代码
使用script标签在HTML网页中插入JavaScript代码
```
<script type="text/javascript">JS代码</script>
``` 
### 应用外部JS文件
使用script标签的src属性引入外部文件
```
<script src="script.js"></script>
```
**在JS文件中不需要写script标签，直接编辑代码即可**
### script标签的位置
#### 放在head部分中
最常用的方式是在页面中head部分放置script元素，浏览器解析head部分就会执行这个代码，然后才解析页面的其余部分。
#### 放在body部分中
JavaScript代码在网页读取到该语句的时候就会执行。  

**在HTML页面中的任何位置都可以插入JS代码，但要注意，HTML在解析文件时是按顺序进行的，所以放在前面的代码就会被先执行。比如进行页面显示初始化的js必须放在head里面，因为初始化都要求提前进行（如给页面body设置css等）；而如果是通过事件调用执行的function那么对位置没什么要求的。**
### JS语句格式
JS语句代码都要在英文格式下输入
**语法为**
*语句；*
```
<script src="script.js">
    alert("JS复习");//JS语句
</script>
```
### JS注释
注释的内容不会在页面中生效适当的注释可以提高代码的可读性。
#### 单行注释"//"
```
<script src="script.js">
    alert("JS复习");//我是单行注释
</script>
```
#### 多行注释，以"/*" 开始，以 " */"结尾
```
<script src="script.js">
    alert("JS复习");//我是单行注释
    /*
    我是注释
    有很多行
    */
</script>
```

### JS中的变量
变量相当于装着某些数值的容器，可以取任意名（区分大小写），但要遵循以下规则：

 1. 变量必须使用字母、下划线(_)或者美元符($)开始。
 
 2. 然后可以使用任意多个英文字母、数字、下划线(_)或者美元符($)组成。

**语法为：**  
*var 变量名;*
```
<script src="script.js">
    var a=100;//声明一个变量
</script>
```
变量可以重复赋值。

### JS的判断语句（if...else）
if...else语句是在指定的条件成立时执行代码，在条件不成立时执行else后的代码。
**语法为：**
*if(条件)
{ 条件成立时执行的代码 }
else
{ 条件不成立时执行的代码 }*
```
<script src="script.js">
    var a = 10;
    var b = 5;
    if(a>b){
        document.write("a比b大");
    }
    else{
        document.write("a不比b大");
    }
    //执行结果为：a比b大
</script>
```
### JS中的函数（function）
函数是完成某个特定功能的一组语句。如果有一组代码需要反复执行，则将这些代码放入函数中，在使用时只需调用函数即可。
**语法为：**  
*function 函数名()  
{  
     函数代码;  
}*  
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>调用函数</title>
	<script>
		function haha(){
			alert("haha!");
		}
	</script>
</head>
<body>
	<button onclick="haha()">点击调用函数</button>
</body>
</html>
```
以上例子使用按钮的点击事件调用函数haha()，我们将不需要编写具体的代码，只需要调用函数即可。
## JS与浏览器互动
### 向网页输出内容
使用*document.write()*可以直接向HTML流书写内容，也就是向网页中输出内容。
```
<script type="text/javascript">
  document.write("I love JavaScript！"); //内容用""括起来，""里的内容直接输出。
  
  var mystr="hello";
  document.write(mystr+"I love JavaScript");//多项内容之间用+号连接
  
  var mystr="hello";
  document.write(mystr+"<br>");//输出hello后，输出一个换行符
  document.write("JavaScript");
</script>
```
### 弹出警告（alert）
alert可以在网页中弹出一个包含“确定”按钮的小窗口，如果你不点击“确定”，就不能对网页做任何操作。
语法为：
*alert(字符串或变量);* 
```
<script type="text/javascript">
   var mynum = 30;
   alert("hello!");//弹出字符串的内容
   alert(mynum);//弹出变量的值
</script>
```
**alert经常在调试程序中使用**
### 弹出确认框(confirm)
confirm 消息对话框通常用于允许用户做选择的动作，如：“你对吗？”等。弹出对话框(包括一个确定按钮和一个取消按钮)，用户在点击对话框按钮前，不能进行任何其它操作。  
**语法为：**  
*confirm(str);*  
**返回值：**  
当用户点击"确定"按钮时，返回true  
当用户点击"取消"按钮时，返回false  
```
<script type="text/javascript">
    var mymessage=confirm("你喜欢JavaScript吗?");
    if(mymessage==true)//用户点击了确定
    {   document.write("很好,加油!");   }
    else//用户点击了取消
    {  document.write("JS功能强大，要学习噢!");   }
</script>
```
### 弹出提问框（prompt）
prompt弹出消息对话框,通常用于询问一些需要与用户交互的信息。弹出消息对话框（包含一个确定按钮、取消按钮与一个文本输入框）。  
**语法为：**  
*prompt(str1, str2);*  
**参数：**  
str1: 要显示在消息对话框中的文本，不可修改  
str2：文本框中的内容，可以修改  
**返回值：**  
点击确定按钮，文本框中的内容将作为函数返回值  
点击取消按钮，将返回null  
```
var myname=prompt("请输入你的姓名:");
if(myname!=null)
  {   alert("你好"+myname); }
else
  {  alert("你好 my friend.");  }
```
### 打开新窗口
open() 方法可以查找一个已经存在或者新建的浏览器窗口。  
**语法为：**  
*window.open([URL], [窗口名称], [参数字符串])*  
**参数：**  
URL：可选参数，在窗口中要显示网页的网址或路径。如果省略这个参数，或者它的值是空字符串，那么窗口就不显示任何文档。  
窗口名称：可选参数，被打开窗口的名称。
参数字符串：可选参数，设置窗口参数，各参数用逗号隔开。

打开http://www.imooc.com网站，大小为300px * 200px，无菜单，无工具栏，无状态栏，有滚动条窗口：
```
<script type="text/javascript"> window.open('http://www.imooc.com','_blank','width=300,height=200,menubar=no,toolbar=no, status=no,scrollbars=yes')
</script>
```
### 关闭窗口
close()关闭窗口
**语法为：**  
*window.close();或*  
*<窗口对象>.close();*  
## JS进行DOM操作
### 认识DOM
文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。
![DOM结构][1]


  [1]: http://img.mukewang.com/52e4bd0f0001dd8d04830279.jpg
### 通过ID获取元素
学过HTML/CSS样式，都知道，网页由标签将信息组织起来，而标签的id属性值是唯一的，就像是每人有一个身份证号一样，只要通过身份证号就可以找到相对应的人。那么在网页中，我们通过id先找到标签，然后进行操作。
**语法为：**  
*document.getElementById("id")*  
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>调用函数</title>
	<script>
		var pp = document.getElementById('pp');
		document.write(pp);//输出获取的元素
	</script>
</head>
<body>
	<p id="pp"></p>
</body>
</html>
```
### innerHTML
innerHTML 属性用于获取或替换HTML元素的内容。
**语法为：**  
*Object.innerHTML*  
其中Object为获取的元素对象  
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>调用函数</title>
	<script>
		var pp = document.getElementById('pp');
		pp.innerHTML = "aha!";
		document.write(pp.innerHTML);//输出获取的元素的HTML内容
	</script>
</head>
<body>
	<p id="pp"></p>
</body>
</html>
```
### 改变HTML样式
**语法为：**  
*Object.style.property=new style;*  
其中Object为获取的元素对象，property为基本属性，如height等。  
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>调用函数</title>
	<script>
		var pp = document.getElementById('pp');
		pp.style.color="red";//修改文字颜色为红色
		pp.style.backgroundColor ="blue";//修改背景颜色为蓝色
	</script>
</head>
<body>
	<p id="pp">yeah!</p>
</body>
</html>
```
### 显示和隐藏元素（display属性）
显示和隐藏的效果，可通过display属性来设置。
**语法为：**  
*Object.style.display = value*  
其中Object为获取的元素对象，value为display属性的值，如none,block等。  
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>调用函数</title>
	<script>
		function hide(){
			var pp = document.getElementById('pp');
			pp.style.display = "none";//隐藏pp
		}
		function show(){
			var pp = document.getElementById('pp');
			pp.style.display = "block";//显示pp
		}
	</script>
</head>
<body>
    <p id="pp">yeah!</p>
	<button onclick="hide()">隐藏</button>
	<button onclick="show()">显示</button>
</body>
</html>
```
### 控制类名（className属性）
className 属性设置或返回元素的class 属性。.
**语法为：**  
*object.className = classname*  
**作用：**  
1.获取元素的class 属性  
2. 为网页内的某个元素指定一个css样式来更改该元素的外观  

---
此页面为本人学习慕课网JavaScript入门篇的个人学习笔记。原地址为https://www.imooc.com/learn/36
