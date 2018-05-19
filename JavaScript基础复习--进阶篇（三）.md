# JavaScript基础复习--进阶篇（三）

---

## 事件响应

### 什么是事件
JavaScript 创建动态页面。事件是可以被 JavaScript 侦测到的行为。 网页中的每个元素都可以产生某些可以触发 JavaScript 函数或程序的事件。

![image](http://img.mukewang.com/53e198540001b66404860353.jpg)

### 鼠标点击事件（onclick）
onclick是鼠标单击事件，当在网页上单击鼠标时，就会发生该事件。同时onclick事件调用的程序块就会被执行，通常与按钮一起使用。
```
<html>
<head>
   <script type="text/javascript">
      function add2(){
        var numa,numb,sum;
        numa=6;
        numb=8;
        sum=numa+numb;
        document.write("两数和为:"+sum);  }
   </script>
</head>
<body>
   <form>
      <input name="button" type="button" value="点击提交" onclick="add2()" />
   </form>
</body>
</html>
```

#### 鼠标经过事件（onmouseover）
鼠标经过事件，当鼠标移到一个对象上时，该对象就触发onmouseover事件，并执行onmouseover事件调用的程序。其使用方法同鼠标点击事件onclick。

#### 鼠标移开事件（onmouseout）
鼠标移开事件，当鼠标移开当前对象时，执行onmouseout调用的程序。其使用方法同鼠标点击事件onclick。

#### 光标聚焦事件（onfocus）
当网页中的对象获得聚点时，执行onfocus调用的程序就会被执行。如聚焦在文本框中等。其使用方法同鼠标点击事件onclick。

#### 失焦事件(onblur)
onblur事件与onfocus是相对事件，当光标离开当前获得聚焦对象的时候，触发onblur事件，同时执行被调用的程序。其使用方法同鼠标点击事件onclick。

#### 内容选中事件（onselect）
选中事件，当文本框或者文本域中的文字被选中时，触发onselect事件，同时调用的程序就会被执行。其使用方法同鼠标点击事件onclick。

#### 文本框内容改变事件(onchange)
通过改变文本框的内容来触发onchange事件，同时执行被调用的程序。其使用方法同鼠标点击事件onclick。

#### 加载事件(onload)
事件会在页面加载完成后，立即发生，同时执行被调用的程序。
- 加载页面时，触发onload事件，事件写在<body>标签内。

#### 卸载事件(onunload)
当用户退出页面时（页面关闭、页面刷新等），触发onUnload事件，同时执行被调用的程序。 
- 注意：不同浏览器对onunload事件支持不同。

## JS内置对象

### 什么是对象
JavaScript 中的所有事物都是对象，如:字符串、数值、数组、函数等，每个对象带有属性和方法。

#### 对象的属性
反映该对象某些特定的性质的，如：字符串的长度、图像的长宽等。
```
var a = person.name;//访问person对象的name属性
```

#### 对象的方法
能够在对象上执行的动作。例如，表单的“提交”(Submit)，时间的“获取”(getYear)等。
```
person.talk();//使用person对象的talk方法
```

### 日期对象（Date）
日期对象可以储存任意一个日期，并且可以精确到毫秒数（1/1000 秒）。  
**定义语法：**  
*var Udate=new Date();*  
以上代码使 Udate 成为日期对象，并且已有初始值：当前时间(当前电脑系统时间)。  
  
如果要自定义初始值，可以用以下方法：
```
var d = new Date(2012, 10, 1);  //2012年10月1日
var d = new Date('Oct 1, 2012'); //2012年10月1日
```
Date对象的常用方法：  
![image](http://img.mukewang.com/555c650d0001ae7b04180297.jpg)

#### 返回/设置年份（get/setFullYear()）

```
var mydate=new Date();//当前时间
document.write(mydate.getFullYear()+"<br>");//输出当前年份
mydate.setFullYear(81);//不同浏览器， 结果不同，年份被设定为 0081或81两种情况。
```

#### 返回星期（getDay）
getDay() 返回星期，返回的是0-6的数字，0 表示星期天。可以用数组对应星期
```
var mydate=new Date();//定义日期对象
  var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
//定义数组对象,给每个数组项赋值
  var mynum=mydate.getDay();//返回值存储在变量mynum中
  document.write(mynum);//输出getDay()获取值
  document.write("今天是："+ weekday[mynum]);//输出星期几
```

#### 返回/设置时间（get/setTime()）
get/setTime() 返回/设置时间，单位毫秒数，计算从 **1970 年 1 月 1 日零时**到日期对象所指的日期的毫秒数。  

如果将目前日期对象的时间推迟1小时，代码如下:
```
<script type="text/javascript">
  var mydate=new Date();
  document.write("当前时间："+mydate+"<br>");
  //60分钟*60秒*1000毫秒为1小时
  mydate.setTime(mydate.getTime() + 60 * 60 * 1000);
  document.write("推迟一小时时间：" + mydate);
</script>
```

### 字符串对象（String）
定义字符串：  
*var mystr = "I love JavaScript!"*

#### length属性
```
var mystr = "I love JavaScript!"
alert(mystr.length);//18
```

#### 常用方法
- toUpperCase() 方法来将字符串小写字母转换为大写  
- toLowerCase() 方法来将字符串大写字母转换为小写  
- charAt() 方法可返回指定位置的字符。返回的字符是长度为 1 的字符串。  
```
stringObject.charAt(index)//index表示某个位置，字符串下标从0开始
```
- indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。第二个可选参数表示开始检索的位置（0开始）。
```
<script type="text/javascript">
  var str="I love JavaScript!"
  document.write(str.indexOf("I") + "<br />");//0
  document.write(str.indexOf("v") + "<br />");//4
  document.write(str.indexOf("v",8));//9
</script>
```
- split() 方法将字符串分割为字符串数组，并返回此数组。  
语法：  
*stringObject.split(separator,limit)*  
第一个参数表示从其位置分割字符串，第二个参数是可选的，表示限制分割的次数。若不指定第一个参数(str.split(""))，则会把字符串转换成字符。
```
var mystr = "www.abc.com";
document.write(mystr.split(".")+"<br>");//www,abc,com
document.write(mystr.split(".", 2)+"<br>");//www,abc
```
- substring() 方法用于提取字符串中介于两个指定下标之间的字符。（第二个参数为可选）  
返回的内容是从 start开始(包含start位置的字符)到 stop-1 处的所有字符，其长度为 stop 减start。
```
var mystr="I love JavaScript";
document.write(mystr.substring(7));//JavaScript
document.write(mystr.substring(2,6));//love
```
- substr() 方法从字符串中提取从 startPos位置开始的指定数目的字符串。  
语法：
*stringObject.substr(startPos,length)*  
第一个参数与substring中相同。  
第二个可选参数指定提取字符串的长度，若不指定，则提取到结尾。
```
 var mystr="I love JavaScript!";
  document.write(mystr.substr(7));//JavaScript!
  document.write(mystr.substr(2,4));//love
```

### Math方法
Math对象，提供对数据的数学计算。  
**Math 对象是一个固有的对象，无需创建它，直接把 Math 作为对象使用就可以调用其所有属性和方法。这是它与Date,String对象的区别。**
```
<script type="text/javascript">
  var mypi=Math.PI; 
  var myabs=Math.abs(-15);
  document.write(mypi);//3.141592653589793
  document.write(myabs);//15
</script>
```
math属性：  
![image](http://img.mukewang.com/532fe7cf0001e7b505170269.jpg)  
math方法：  
![image](http://img.mukewang.com/532fe841000174db05160622.jpg)

#### 向上取整（ceil()）
ceil() 方法可对一个数进行向上取整。 返回的是大于或等于x，并且与x最接近的整数。  
**语法为：**  
*Math.ceil(x)*  

```
document.write(Math.ceil(0.8) + "<br />")//1
document.write(Math.ceil(6.3) + "<br />")//7
document.write(Math.ceil(5) + "<br />")//5
document.write(Math.ceil(3.5) + "<br />")//4
document.write(Math.ceil(-5.1) + "<br />")//-5
document.write(Math.ceil(-5.9))//-5
```

#### 向下取整（floor()）
floor() 方法可对一个数进行向下取整。返回的是小于或等于x，并且与 x 最接近的整数。  
**语法为：**  
*Math.floor(x)*
```
document.write(Math.floor(0.8)+ "<br>")//0
document.write(Math.floor(6.3)+ "<br>")//6
document.write(Math.floor(5)+ "<br>")//5
document.write(Math.floor(3.5)+ "<br>")//3
document.write(Math.floor(-5.1)+ "<br>")//-6
document.write(Math.floor(-5.9))//-6
```

#### 四舍五入（round()）
round() 方法可把一个数字四舍五入为最接近的整数。
- 如果 x 与两侧整数同等接近，则结果接近 +∞方向的数字值 。(如 -5.5 将舍入为 -5; -5.52 将舍入为 -6)  

**语法为：**  
*Math.round(x);*
```
document.write(Math.round(1.6)+ "<br>");//2
document.write(Math.round(2.5)+ "<br>");//3
document.write(Math.round(0.49)+ "<br>");//0
document.write(Math.round(-6.4)+ "<br>");//-6
document.write(Math.round(-6.6));//-7
```

#### 随机数（radom()）
random() 方法可返回介于 0 ~ 1（大于或等于 0 但小于 1 )之间的一个随机数。  
**语法为：**  
*Math.random();*  
  
获得0 ~ 10之间的随机数：
```
document.write((Math.random())*10);
```

### 数组对象（Array）
数组对象是一个对象的集合，里边的对象可以是不同类型的。数组的每一个成员对象都有一个“下标”（从零开始），用来表示它在数组中的位置，是从零开始的。  
**语法为**
```
var myArray = new Array();//定义了一个空数组
var myArray = new Array(n);//定义时指定有n个空元素的数组
var myArray = [2, 8, 6]; //定义数组的时候，直接初始化数据
```

数组属性：  
length 用法：<数组对象>.length；返回：数组的长度，即数组里有多少个元素。它等于数组里最后一个元素的下标加一。  

数组方法：  
![image](http://img.mukewang.com/533295ab0001dead05190599.jpg)

#### 数组连接（concat()）
concat() 方法用于连接两个或多个数组。**此方法返回一个新数组，不改变原来的数组**。  
**语法为**  
*arrayObject.concat(array1,array2,...,arrayN)*  
```
var mya = new Array(3);
mya[0] = "1";
mya[1] = "2";
mya[2] = "3";
document.write(mya.concat(4,5)+"<br>");//1,2,3,4,5
document.write(mya); //1,2,3

var mya1= new Array("hello!")
var mya2= new Array("I","love");
var mya3= new Array("JavaScript","!");
var mya4=mya1.concat(mya2,mya3);
document.write(mya4);//hello!,I,love,JavaScript,!
```

#### 指定分隔符连接数组元素（join()）
join()方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的。返回一个字符串，该字符串把数组中的各个元素串起来，用<分隔符>置于元素与元素之间。**这个方法不影响数组原本的内容**。  
**语法为**  
*arrayObject.join(分隔符)*  

```
<script type="text/javascript">
  var myarr = new Array(3)
  myarr[0] = "I";
  myarr[1] = "love";
  myarr[2] = "JavaScript";
  document.write(myarr.join(".")); //I.love.JavaScript
  //若不指定分隔符，则默认用","分割
</script>
```

#### 颠倒数组元素顺序（reverse()）
reverse() 方法用于颠倒数组中元素的顺序。**该方法会改变原来的数组，而不会创建新的数组**。
```
<script type="text/javascript">
  var myarr = new Array(3)
  myarr[0] = "1"
  myarr[1] = "2"
  myarr[2] = "3"
  document.write(myarr + "<br />")//1,2,3
  document.write(myarr.reverse())//3,2,1
```

#### 选定元素(slice())
slice() 方法可从已有的数组中返回选定的元素。**返回一个新的数组，不会修改数组**。包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。  
**语法为：**  
*arrayObject.slice(start,end)*  
其中end参数为可选参数
    
注：  
1. 可使用负值从数组的尾部选取元素。
2. 如果 end 未被规定，那么 slice() 方法会选取从 start 到数组结尾的所有元素。
3. String.slice() 与 Array.slice() 相似。

```
var myarr = new Array(1,2,3,4,5,6);
document.write(myarr + "<br>");//1,2,3,4,5,6
document.write(myarr.slice(2,4) + "<br>");//3,4
document.write(myarr);//1,2,3,4,5,6
```

#### 数组排序（sort()）
sort()方法使数组中的元素按照一定的顺序排列。  
**语法为：**  
*arrayObject.sort(方法函数)*  
其中方法函数为可选参数  
1. 如果不指定<方法函数>，则按unicode码顺序排列。  
2. 如果指定<方法函数>，则按<方法函数>所指定的排序方法排序。

注：  
该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：   
- 若返回值<=-1，则表示 A 在排序后的序列中出现在 B 之前。
- 若返回值>-1 && <1，则表示 A 和 B 具有相同的排序顺序。
- 若返回值>=1，则表示 A 在排序后的序列中出现在 B 之后。

```
<script type="text/javascript">
  var myarr1 = new Array("Hello","John","love","JavaScript"); 
  var myarr2 = new Array("80","16","50","6","100","1");
  document.write(myarr1.sort()+"<br>");//Hello,JavaScript,John,love
  document.write(myarr2.sort());//1,100,16,50,6,80
</script>
```
方法函数示例（降序排序）：
```
function sortNum(a,b) {
    return b - a;
}
```

---

次页面为本人学习慕课网JavaScript进阶篇的的个人学习笔记。原地址为 https://www.imooc.com/learn/10