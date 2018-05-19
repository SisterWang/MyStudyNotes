# JavaScript基础复习--进阶篇（二）

---

## 流程控制语句

### if语句
if语句是基于条件成立才执行相应代码时使用的语句。  
**语法为：**  
*if(条件)  
{ 条件成立时执行代码}*  
```
var score=60;
if(score>=60){
    alert("恭喜你及格了");
}
```

### if...else语句
if...else语句是在指定的条件成立时执行代码，在条件不成立时执行else后的代码。  
**语法为：**  
*if(条件)  
{ 条件成立时执行的代码}  
else  
{条件不成立时执行的代码}*  
```
var score=60;
if(score>=60){
    alert("恭喜你及格了");
}
else{
    alert("没及格");
}
```

### else if语句
要在多组语句中选择一组来执行，使用else if语句。  
**语法为：**  
*if(条件1)  
{ 条件1成立时执行的代码}  
else  if(条件2)  
{ 条件2成立时执行的代码}  
...  
else  if(条件n)  
{ 条件n成立时执行的代码}  
else  
{ 条件1、2至n不成立时执行的代码}*  
```
var score=60;
if(score>=60 && score<90){
    alert("恭喜你及格了");
}
else if(scroe>90){
    alert("你很优秀！");
}
else{
    alert("没及格");
}
```

### switch语句
当有很多种选项的时候，switch比if else使用更方便。 
Switch必须赋初始值，值与每个case值匹配。满足执行该 case 后的所有语句，并用break语句来阻止运行下一个case。如所有case值都不匹配，执行default后的语句。  
**语法为：**  
*switch(表达式)  
{  
case值1:  
  执行代码块 1  
  break;  
case值2:  
  执行代码块 2  
  break;  
...  
case值n:  
  执行代码块 n  
  break;  
default:  
  与 case值1 、 case值2...case值n 不同时执行的代码  
}*  
```
var week = 1;
switch(score){
    case 1:
        alert("周一");
    case 2:
        alert("周二");
    ...
    default:
        alert("出错了！");
}
```

### for循环
很多事情不只是做一次，要重复做。如打印10份试卷，每次打印一份，重复这个动作，直到打印完成。这些事情，我们使用循环语句来完成，循环语句，就是重复执行一段代码。  
**语法为：**  
*for(初始化变量;循环条件;循环迭代)  
{  
    循环语句  
}*  
```
<script type="text/javascript">
var num=1;
for (num=1;num<=6;num++)  //初始化值；循环条件；循环后条件值更新
{   document.write("取出第"+num+"个球<br />");//取出第1-6个球
}
</script>
```

### while循环
和for循环有相同功能的还有while循环, while循环重复执行一段代码，直到某个条件不再满足。  
**语法为：**  
*while(判断条件)  
{
    循环语句  
}*  
```
<script type="text/javascript">
var num=0;  //初始化值
while (num<=6)   //条件判断
{
  document.write("取出第"+num+"个球<br />");
  num=num+1;  //条件值更新
}
</script>
```

### Do...while语句
和while语句基本相同，但Do...while语句保证循环中的代码至少被执行一次。  
**语法为**  
*do  
{  
    循环语句  
}  
while(判断条件)*  
```
<script type="text/javascript">
var num=0;  //初始化值
do//至少执行一次
{
  document.write("取出第"+num+"个球<br />");
  num=num+1;  //条件值更新
}
while (num<=6) //执行一次后进行条件判断
</script>
```

### 退出循环（break）
在while、for、do...while、while循环中使用break语句退出循环，直接执行后面的代码。  
**语法为**  
*for(初始条件;判断条件;循环后条件值更新)  
{  
  if(特殊情况)  
  {break;}  
  循环代码  
}*  
```
<script type="text/javascript">
var num=0;  //初始化值
while (num<=6)   //条件判断
{
    if(num==2)
        break;//累了，不想取了
    document.write("取出第"+num+"个球<br />");
    num=num+1;  //条件值更新
}
</script>
```

### 继续循环（continue）  
continue的作用是仅仅**跳过本次**循环，而整个循环体继续执行。  
**语法为**  
for(初始条件;判断条件;循环后条件值更新)  
{  
  if(特殊情况)  
  { continue; }  
 循环代码  
}  
```
<script type="text/javascript">
var num=0;  //初始化值
while (num<=6)   //条件判断
{
    if(num==2)
        continue;//2号球不好看，跳过它
    document.write("取出第"+num+"个球<br />");
    num=num+1;  //条件值更新
}
</script>
```

## 函数

### 什么是函数
函数的作用，可以写一次代码，然后反复地重用这个代码。  
如：我们要多次问好：  
```
alert("Hello!");
alert("A!");
alert("Hello!");
alert("B!");
...//需要多次重复相同的代码
```
而我们可以定义一个函数：  
```
function sayHello(name){
    alert("Hello!");
    alert(name);
}
sayHello('A');
sayHello('B');//只需要调用函数即可
```

### 定义函数
**语法为：**  
*function  函数名( )  
{  
     函数体;  
}*  
function定义函数的关键字，“函数名”你为函数取的名字，“函数体”替换为完成特定功能的代码。
```
function sayHello(name){//sayHello为有意义的函数名
    alert("Hello!");
    alert(name);
}
```

### 调用函数
函数定义好后，是不能自动执行的，需要调用它,直接在需要的位置写函数名。可以再script标签内调用，或在HTML文件中调用，如通过点击按钮后调用定义好的函数。  
```
<html>
<head>
<script type="text/javascript">
   function add2()
   {
         sum = 5 + 6;
         alert(sum);
   }
</script>
</head>
<body>
<form>
<input type="button" value="click it" onclick="add2()">  //按钮,onclick点击事件，直接写函数名
</form>
</body>
</html>
```

### 函数的参数
参数可以多个，根据需要增减参数个数。参数之间用(逗号，）隔开。  
**语法为：**  
*function 函数名(参数1,参数2)  
{  
     函数代码  
}*  
```
function add2(x,y)//实现任意两数相加
{
   sum = x + y;
   document.write(sum);
}
```
x和y则是函数的两个参数，调用函数的时候，我们可通过这两个参数把两个实际的加数传递给函数了。  
例如，add2(3，4)会求3+4的和，add2(60,20)则会求出60和20的和。  

### 函数的返回值
如果想对函数的结果进行处理怎么办呢？我们只要把"document.write(sum)"这行改成如下代码：  
```
function add2(x,y)
{
   sum = x + y;
   return sum; //返回函数值,return后面的值叫做返回值。
}
```
还可以通过变量存储调用函数的返回值，代码如下:  
```
var result = add2(3,4);
```

---

次页面为本人学习慕课网JavaScript进阶篇的的个人学习笔记。原地址为 https://www.imooc.com/learn/10