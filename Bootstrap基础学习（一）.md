# Bootstrap基础学习（一）

## 准备工作
参考 https://getbootstrap.com/  
### bootstrap模板  
```
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css" integrity="sha384-WskhaSGFgHYWDcbwN70/dfYBj47jz9qbsMId/iRN3ewGhXQFZCSftd1LZCfmhktB" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js" integrity="sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T" crossorigin="anonymous"></script>
  </body>
</html>
```

## 排版

### 标题（一）
  
Bootstrap和普通的HTML页面一样，定义标题都是使用标签< h1 >到< h6 >,只不过Bootstrap覆盖了其默认的样式，使用其在所有浏览器下显示的效果一样，具体定义的规则可以如下表所示：  
![image](http://img.mukewang.com/53acce330001429807730337.jpg)  

在Bootstrap中为了让非标题元素和标题使用相同的样式，还特意定义了.h1~.h6六个类名。  
```
<!--Bootstrap中的标题-->
<h1>Bootstrap标题一</h1>
<h2>Bootstrap标题二</h2>
<h3>Bootstrap标题三</h3>
<h4>Bootstrap标题四</h4>
<h5>Bootstrap标题五</h5>
<h6>Bootstrap标题六</h6>
```

```
<!--通过css样式和类名固定了样式，只需要输入对应的类明就可以调用样式，这里我把DIV换成了P效果也是一样的-->
<p class="h1">Bootstrap标题一</p>
<p class="h2">Bootstrap标题二</p>
<p class="h3">Bootstrap标题三</p>
<p class="h4">Bootstrap标题四</p>
<p class="h5">Bootstrap标题五</p>
<p class="h6">Bootstrap标题六</p>
```

### 标题（二）
在Bootstrap中，使用了< small >标签来制作副标题。  
- 行高都是1，而且font-weight设置了normal变成了常规效果（不加粗），同时颜色被设置为灰色（#999）。
- 由于< small >内的文本字体在h1 到h3内，其大小都设置为当前字号的65%；而在h4~h6内的字号都设置为当前字号的75%；
```
<h1>Bootstrap标题一<small >副标题</small></h1>
```  

### 段落（正文文本） 

在Bootstrap中为文本设置了一个全局的文本样式
- 全局文本字号为14px(font-size)。  
- 行高为1.42857143（line-height），大约是20px(大家看到一串的小数或许会有疑惑，其实他是通过LESS编译器计算出来的，当然Sass也有这样的功能)。
- 颜色为深灰色（#333）；
- 字体为"Helvetica Neue", Helvetica, Arial, sans-serif;（font-family），或许这样的字体对我们中文并不太合适，但在实际项目中，大家可以根据自己的需求进行重置，在此我们不做过多阐述，我们回到这里。该设置都定义在<body>元素上，由于这几个属性都是继承属性，所以Web页面中文本（包括段落p元素）如无重置都会具有这些样式效果。
- 另外在Bootstrap中，为了让段落p元素之间具有一定的间距，便于用户阅读文本，特意设置了p元素的margin值（默认情况之下，p元素具有一个上下外边距，并且保持一个行高的高度）：

### 强调内容
如果想让一个段落p突出显示，可以通过添加类名“.lead”实现，其作用就是增大文本字号，加粗文本，而且对行高和margin也做相应的处理。  
```
<p>我是普通文本。</p>
<p class="lead">我是特意要突出的文本。</p>
```

### 粗体
粗体就是给文本加粗，在普通的元素中我们一般通过font-weight设置为bold关键词给文本加粗。在Bootstrap中，可以使用< b >和< strong >标签让文本直接加粗。  
```
<p>我在学习<strong>Bootstrap</strong>，我要掌握<strong>Bootstrap</strong>的所有知识。</p>
```  

### 斜体
斜体类似于加粗一样，除了可以给元素设置样式font-style值为italic实现之外，在Bootstrap中还可以通过使用标签< em >或< i >来实现。  
```
<p>我在学习<i>Bootstrap</i>，我要掌握<em>Bootstrap</em>的所有知识。</p>
``` 

### 强调相关的类  
Bootstrap还定义了一套类名，这里称其为强调类名（类似前面说的“.lead”）,这些强调类都是通过颜色来表示强调，具本说明如下：  
- .text-muted：提示，使用浅灰色（#999）
- .text-primary：主要，使用蓝色（#428bca）
- .text-success：成功，使用浅绿色(#3c763d)
- .text-info：通知信息，使用浅蓝色（#31708f）
- .text-warning：警告，使用黄色（#8a6d3b）
- .text-danger：危险，使用褐色（#a94442）  

### 文本对齐风格
在排版中离不开文本的对齐方式。在**CSS中**常常使用text-align来实现文本的对齐风格的设置。其中主要有四种风格：  
- 左对齐，取值left
- 居中对齐，取值center
- 右对齐，取值right
- 两端对齐，取值justify

为了简化操作，方便使用，**Bootstrap**通过定义四个类名来控制文本的对齐风格：  
- .text-left：左对齐
- .text-center：居中对齐
- .text-right：右对齐
- .text-justify：两端对齐

```
<p class="text-left">我居左</p>
<p class="text-center">我居中</p>
<p class="text-right">我居右</p>
<p class="text-justify">我两端对齐</p>
```  

### 列表
Bootstrap根据平时的使用情形提供了六种形式的列表：  
1. 普通列表
2. 有序列表
3. 去点列表
4. 内联列表
5. 描述列表
6. 水平描述列表  

#### 无序列表、有序列表
无序列表和有序列表使用方式和我们平时使用的一样（无序列表使用ul，有序列表使用ol标签），在样式方面，Bootstrap只是在此基础上做了一些细微的优化。

#### 去点列表
通过给无序列表添加一个类名“.list-unstyled”,这样就可以去除默认的列表样式的风格。  

#### 内联列表
Bootstrap像去点列表一样，通过添加类名“.list-inline”来实现内联列表，简单点说就是把垂直列表换成水平列表，而且去掉项目符号（编号），保持水平显示。也可以说内联列表就是为制作水平导航而生。
```
<ul class="list-inline">
    <li>W3cplus</li>
    <li>Blog</li>
    <li>CSS3</li>
    <li>jQuery</li>
    <li>PHP</li>
</ul>
```

#### 定义列表
对于定义列表而言，Bootstrap并没有做太多的调整，只是调整了行间距，外边距和字体加粗效果。与我们以前的使用定义列表的方法是相同的。  
```
<dl>
    <dt>W3cplus</dt>
    <dd>一个致力于推广国内前端行业的技术博客</dd>
</dl>
```

#### 水平定义列表
水平定义列表就像内联列表一样，Bootstrap可以给< dl >添加类名“.dl-horizontal”给定义列表实现水平显示效果。  
**只有屏幕大于768px的时候，添加类名“.dl-horizontal”才具有水平定义列表效果。**
- 将dt设置了一个左浮动，并且设置了一个宽度为160px
- 将dd设置一个margin-left的值为180px，达到水平的效果
- 当标题宽度超过160px时，将会显示三个省略号

```
<dl class="dl-horizontal">
    <dt>W3cplus</dt>
    <dd>一个致力于推广国内前端行业的技术博客。它以探索为己任，不断活跃在行业技术最前沿，努力提供高质量前端技术博文</dd>
    <dt>我来测试一个标题，我来测试一个标题</dt>
    <dd>我在写一个水平定义列表的效果，我在写一个水平定义列表的效果</dd>
</dl>
```

### 代码（一）
用于显示代码的风格。在Bootstrap主要提供了三种代码风格：
1. 使用< code >< /code >来显示单行内联代码
2. 使用< pre >< /pre >来显示多行块代码
3. 使用< kbd >< /kbd >来显示用户输入代码

code风格：
```
<div>Bootstrap的代码风格有三种：
  <code>&lt;code&gt;</code>
  <code>&lt;pre&gt;</code>
  <code>&lt;kbd&gt;</code>
</div>
```

pre风格：
```
<div>
<pre>
&lt;ul&gt;
&lt;li&gt;...&lt;/li&gt;
&lt;li&gt;...&lt;/li&gt;
&lt;li&gt;...&lt;/li&gt;
&lt;/ul&gt;
</pre>
</div>
```

kbd风格：
```
<div>请输入<kbd>ctrl+c</kbd>来复制代码，然后使用<kbd>ctrl+v</kbd>来粘贴代码</div>
```

### 代码（二）
你只需要在pre标签上添加类名“.pre-scrollable”，就可以控制代码块区域最大高度为340px，一旦超出这个高度，就会在Y轴出现滚动条。  

### 表格
Bootstrap为表格提供了**1种基础样式**和**4种附加样式**以及**1个支持响应式的表格**。
1. .table：基础表格
2. .table-striped：斑马线表格
3. .table-bordered：带边框的表格
4. .table-hover：鼠标悬停高亮的表格
5. .table-condensed：紧凑型表格
6. .table-responsive：响应式表格

#### 表格行的类
Bootstrap还为表格的行元素< tr >提供了五种不同的类名，每种类名控制了行的不同背景颜色  
![image](http://img.mukewang.com/53ad213f0001b08807340508.jpg)

#### 基础表格
在Bootstrap中，对于基础表格是通过类名“.table”来控制。如果在< table >元素中不添加任何类名，表格是无任何样式效果的。想得到基础表格，我们只需要在< table >元素上添加“.table”类名，就可以得到Bootstrap的基础表格  
```
<table class="table">
…
</table>
```

#### 斑马线表格
在Bootstrap中实现这种表格效果并不困难，只需要在< table class="table" >的基础上增加类名“.table-striped”即可  
```
<table class="table table-striped">
…
</table>
```

#### 带边框的表格
只需要在基础表格< table class="table" >基础上添加一个“.table-bordered”类名即可  
```
<table  class="table table-bordered">
  …
</table>
```

#### 鼠标悬浮高亮的表格
仅需要< table class="table" >元素上添加类名“table-hover”即可  
```
<table class="table table-hover">
…
</table>
```

#### 紧凑型表格
紧凑型表格的运用，也只是需要在< table class="table" >基础上添加类名“table-condensed”  
```
<table class="table table-condensed">
…
</table>
```

#### 响应式表格
Bootstrap提供了一个容器，并且此容器设置类名“.table-responsive”,此容器就具有响应式效果，然后将< table class="table">置于这个容器当中，这样表格也就具有响应式效果。  

Bootstrap中响应式表格效果表现为：当你的浏览器可视区域小于768px时，表格底部会出现水平滚动条。当你的浏览器可视区域大于768px时，表格底部水平滚动条就会消失。  
```
<div class="table-responsive">
<table class="table table-bordered">
   …
</table>
</div>
```

---

次页面为本人学习慕课网Bootstrap基础的个人学习笔记，原地址为 https://www.imooc.com/learn/141