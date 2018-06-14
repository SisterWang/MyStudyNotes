# JSON与Ajax
## JSON
JSON是JS的一个严格的子集，利用了JS中的一些模式来表示结构化的数据。
### 语法
JSON可以表示三种类型的值：  
- 简单值
- 对象
- 数组

#### 简单值
采用和JS；同样的语法，，可以在JSON中表示字符串、数值、布尔值和null。**不支持undefined**
```js
//数值
5
//字符串：必须使用双引号
"HelloWorld"
//布尔值
false
//null
null
```
#### 对象
JSON中的对象要求为属性名加上双引号，且不用声明变量（JSON中没有变量的概念），句子末尾也不用加上分号。
```js
{
    "name":"张三",
    "age":"20",
    //嵌入对象
    "school":{
        //由于是不同的对象，可以使用相同的属性名“name”
        "name":"清华池",
        "location":"小胡同"
    }
}
```
#### 数组
JSON中的数组同样不需要声明变量与添加分号：
```js
[a,"hello",true]
```
将数组和对象组合起来：
```js
[
    {
        "name":"张三",
        "age":"20",
        "school":{
            "name":"清华池",
            "location":"小胡同"
        }
    },
    {
        "name":"李四",
        "age":"21",
        "someting"：["校园卡管理系统","电路元件绘制软件"],
        "school":{
            "name":"南昌航空大学",
            "location":"南昌"
        }
    }
]
```
对象或数组一般是JSON对象的最外层形式。
### 解析与序列化
在JSON对象解析成JS对象后，可以简单地通过类似以下代码来获取想要的信息：
```js
people[1].age
```
而非在DOM中使用的复杂语句:
```js
doc.getElementsByTagName("people")[1].getAttribute("age")
```

#### eval()与JSON对象
在早期，都使用eval()来解析JSON，但**eval()方法不会过滤或检查JSON语句**，因此当JSON语句中含有恶意代码时将会对程序带来很大的危害。

ECMA5定义了全局对象JSON来解析JSON。其有两个方法：  
- stringify()：将Js对象序列化为JSON字符串
- parse()：将JSON字符串解析为JS值

```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ]
}
var jsonText = JSON.stringify(people);
var jsonCopy = JSON.parse(jsonText);
```
如果给JSON.parse()的字符串不是有效的JSON，该方法会报错。  
默认情况下，stringify()输出的JSON字符串不包含缩进或空格等：  

```js
//jsonText中的字符串
{name:"张三",age:30,something:["校园卡管理系统","电子仪器绘制软件"]}
```

#### 序列化选项
JSON.stringify()除了要序列化的JS对象以外，还可以接收两个参数：  
- 第一个参数是过滤器，可以是一个数组或一个函数。  
- 第二个参数是一个选项，表示是否在JSON字符串中保留缩进。

如果**过滤器是数组**，那么JSON.stringify()的结果将只包含数组中列出的属性：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ]
}
//第二个参数为过滤器
var jsonText = JSON.stringify(people,["name","age"]);

//jsonText中的字符串
{name:"张三",age:30}
```
如果**过滤器是函数**，则传入的函数接收两个参数，属性名和属性值。函数的返回值就是相应属性的属性值，若返回undefined，则该属性会被忽略：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    say:"姑娘好"
}
//第二个参数为过滤器
var jsonText = JSON.stringify(people,function(key,value){
    switch(key){
        case "name":
            return "老王";
        case "age":
            return 40;
        case "something":
            return value.join(",");
        case "say":
            //略过该属性
            return undefined;
        default:
            return value;
    }
});
```
**第三个参数**用于控制结果中的缩进和空白符。**若这个参数是一个数值**，则表示每个级别缩进的空格数：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    say:"姑娘好"
}
//第三个参数为数字，表示缩进的空格数
var jsonText = JSON.stringify(people,null,4);

//jsonText中的字符串
{
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    say:"姑娘好"
}
```
**若第三个参数是一个字符串**，则会使用字符串来代替缩进字符：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    say:"姑娘好"
}
//第三个参数为字符串，表示替换缩进符
var jsonText = JSON.stringify(people,null,"-");

//jsonText中的字符串
{
-name:"张三",
-age:30,
-something:[
--"校园卡管理系统",
--"电子仪器绘制软件"
-],
-say:"姑娘好"
}
```
若还不能满足自定义序列化的需求，可以给对象定义toJSON()方法：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    toJSON:function(){
        return this.name;
    }
}
var jsonText = JSON.stringify(people);
```

执行顺序：
1. 如果存在toJSON()方法且能获得有效的值，则调用该方法。否则返回对象本身。
2. 如果提供第二个参数，则应用该过滤器得值对第1步的值进行过滤。
3. 对第2步的返回值进行相应序列化。
4. 如果提供了第三个参数，执行相应的格式化。

#### 解析选项
JSON.parse()也可以接收另一个参数，该参数是一个函数，在每个键值对上调用，其同样接收两个参数：属性名和属性值：
```js
var people = {
    name:"张三",
    age:30,
    something:[
        "校园卡管理系统",
        "电子仪器绘制软件"
    ],
    //一个日期对象
    bornDate:new Date(1997,6,9)
}
//转换为JSON字符串
var jsonText = JSON.stringify(people);
//转换为JS对象
var peopleCopy = JSON.parse(jsonText,function(key,value){
    if(key == "bornDate"){
        //将日期字符串替换为日期对象
        return new Date(value);
    }
    else{
        return value;
    }
})
//输出Date对象的年份
alert(peopleCopy.bornDate.getFullYear());
```
## Ajax
待续，，