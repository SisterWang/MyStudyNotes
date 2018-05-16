# JavaScript面试复习（一）

## JS基础知识

### 变量类型和计算

#### 值类型
值类型之间不会相互影响
```
var a = 100;
var b = a;
a = 200;
alert(b);//100
```

#### 引用类型
引用类型为变量用指针指向存储空间。当有多个变量指针指向同一个引用类型存储空间时，它们将会互相影响。  
以上两用类型采用不同的存储方式，即：  
**JS按存储方式区分变量类型**
```
var a = {age:20};
var b = a;
b.age = 25;
alert(a.age);//25
```

#### typeof运算符
typeof运算符共可区分6种不同类型，其中4种值类型，2种引用类型。

##### 值类型
- undefined
- number
- boolean
- string

##### 引用类型
- object
- function

##### 代码实例
```
typeof undefined;//undefined
typeof 3;//number
typeof 'abc';//string
typeof ture;//boolean
typeof [];//object
typeof {};//object
typeof null;//object
typeof alert;//function
```
typeof只能区分函数和非函数两种信引用类型。其中null为特殊的引用类型，返回值为object。undefined为值类型，返回值为undefined。

#### 隐式强制类型转换

##### 字符串拼接
```
var a = 100 + 10;//110
var b = 100 + "10"//"10010"
```
##### ==符号
双等号会试图将两端的值转换成相等的布尔值。如100可以转换为ture,"100"也可以转换为ture,故100=="100"返回ture(相等)。
```
100 == "100";//ture
null == undefined;//ture
0 == "";//ture
```

##### if语句
if语句会试图将其条件语句转换为布尔值。如if(100)中的100会被转换成ture。

##### 逻辑运算
逻辑运算中也会试图将两端的值转换为布尔类型，其判断依据和if语句一致。
```
100 && 0//0
"" || "abc"//"abc"
!100 //false
!!100//ture
```
可以利用!!来将一个其他类型的值转换成布尔类型。

#### 何时使用双等和三等
参考jQuery源码中的内容，只在以下情况下使用==。
```
if(obj.a == null){
    /*以上条件相当于
      obj.a === null || obj.a ===undefined
      只在这种情况下，使用==
    */
}
```
#### JS的内置函数
JS有一下九种内置函数：
- Object
- Array
- Boolean
- Number
- String
- Function
- Date
- RegExp
- Error

#### 如何理解JSON
JSON只不过是一个JS对象。（也是一种数据格式）  
常用API：
```
JSON.stringify({a:10,b:20});//把对象变成字符串
JSON.parse('{"a":10,"b":20}');//把字符串变成对象
```
