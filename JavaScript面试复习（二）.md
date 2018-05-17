# JavaScript面试复习（二）

---

## JS基础知识

### 原型和原型链

#### 构造函数
使用大写字母开头为构造函数命名，是一种约定俗成的方式。

```
function Person(name,age){
    this.name = name;
    this.age = age;
    //return this//默认有这一行
}
//通过return this来把this返回并赋值给变量
var p1 = new Person('wangjie',21);
var p2 = new Person('zhangsan',28);//创建多个对象
```
**扩展：**  
- var a = {}其实是var a = new Object()的语法糖  
- var a = []其实是var a = new Array()的语法糖  
- function Person(){...}其实是var Person = new Function(...)的语法糖  
- 使用instanceof判断一个函数是否是一个变量的构造函数：变量 instanceof Array

#### 原型规则
1. 所有的引用类型（数组、对象、函数），都具有对象特性，可自由扩展属性（null除外）
```
//为数组、对象、函数扩展属性
var a = {}; 
a.age = 10;
var b = [];
b.age = 15;
function c(){}
c.age = 21;
```
2. 所有的引用类型（数组、对象、函数）都有一个_proto_（隐式原型）属性，属性值是一个普通的对象。
```
//对象a中存在_proto_属性
alert(a._proto_);
```
3. 所有的函数，都有一个prototype（显式原型）属性，属性值也是一个普通的对象。
```
//函数c中存在prototype属性
alert(c.prototype);
```
4. 所有的引用类型（数组、对象、函数），_proto_属性值指向它的构造函数的prototype属性值。  
```
a._proto_ === Object.prototype;//Object为对象a的构造函数
```
5. 当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，那么会去它的_proto_（构造函数的prototype）中寻找。
```
//构造函数
function Person(name,age){
    this.name = name;
}
Person.prototype.alertName = function(){
//无论是从自身还是从构造函数的显示原型中调用函数，this永远指向调用这个函数的对象
    alert(this.name);
}
//创建示例
var p = new Person('Wangjie');
p.printName = function(){
    document.write(this.name);
}

//测试
p.printName();//this指向p
p.alertName();//this指向p
```
![image](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1526533915419&di=836b1a945b6b0934b35e3979996fb930&imgtype=0&src=http%3A%2F%2Fpic002.cnblogs.com%2Fimages%2F2012%2F302729%2F2012061620301421.jpg)

##### 循环对象自身的属性
可以通过hasOwnProperty(属性)方法判断该属性是否存在于其本身（返回ture），还是存在于原型中（返回false）。
```
var item;
for(item in p){
//高级浏览器已经在for in中屏蔽了来自原型的属性
//但加上这个判断，可以增加程序的健壮性
    if(p.hasOwnProperty(item)){
        document.write(item);
    }
}
```

#### 原型链
下面代码中p的_proto_属性指向其构造函数Peson的prototype属性指向的对象，即它的原型（Person Prototype）。  
而Person Prototype也是一个对象，同样拥有_proto_属性，指向Person Prototype的原型Object prototype（其构造函数Object的prototype属性指向的对象）。  
toString()不在p或它的原型中，因此，JS会继续向上查找p的原型的原型(Object prototype)中是否有此方法。

```
//构造函数
function Person(name,age){
    this.name = name;
}
Person.prototype.alertName = function(){
//无论是从自身还是从构造函数的显示原型中调用函数，this永远指向调用这个函数的对象
    alert(this.name);
}
//创建示例
var p = new Person('Wangjie');
p.printName = function(){
    document.write(this.name);
}

//测试
p.printName();//this指向p
p.alertName();//this指向p

p.toString();//去p._proto_._proto_中查找
```

##### instanceof判断其构造函数
p instanceof Person的判断逻辑是：  
p的_proto_一层一层向上查找，判断能否查找到Person.prototype。  
通过以上判断逻辑可知，p instanceof Person语句返回值为ture同时，p instanceof Object也将返回真。

```
if(p instanceof Person){//返回真
    alert("Person是p的构造函数！");
}
if(p instanceof Object){//返回真
    alert("Object是p的构造函数！");
}

```
*可以通过instanceof来准确判断一个变量是否为数组等*

##### 原型链继承 
封装DOM查询：
```
function Gelem(id){
    this.elem = document.getElementById(id);
}

Gelem.prototype.html = function (val){
    var elem = this.elem;
    if(val){
        elem.innerHTML = val;
        return this;//返回调用该函数的对象本身
    }
    else{
        return elem.innerHTML;
    }
}

Gelem.prototype.on = function(type,fn){
    var elem = this.elem;
    elem.addEventListener(type,fn);
    return this;//返回调用该函数的对象本身
}

var oDiv = new Gelem('id');
document.write(oDiv.html());

ODiv.html('<p>hello world!</p>');
oDiv.on('click',function(){
    alert('clicked');
})

//通过return this可实现链式操作
ODiv.html("<p>hello world!</p>").on('click',function(){
    alert('clicked');
}).html("<p>hello JS!</p>");
```