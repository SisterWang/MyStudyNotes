# Bootstrap基础学习（三）

## 菜单、按钮及导航

### 下拉菜单
在Bootstrap框架中的下拉菜单组件是一个独立的组件。

在使用Bootstrap框架的下拉菜单时，必须调用Bootstrap框架提供的bootstrap.js文件。当然，如果你使用的是未编译版本，在js文件夹下你能找到一个名为“dropdown.js”的文件，也可以调用这个js文件。
```html
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>
```

在使用Bootstrap框架中的下拉菜单组件时，其结构运用的正确与否非常的重要，如果结构和类名未使用正确，直接影响组件是否能正常运用。
```html
<div class="dropdown">
<button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
下拉菜单
<span class="caret"></span>
</button>
<ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
   <li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
   …
   <li role="presentation" class="divider"></li>
   <li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
</ul>
</div>
```

- 使用一个名为“dropdown”的容器包裹了整个下拉菜单元素
- 使用了一个<button>按钮做为父菜单，并且定义类名“dropdown-toggle”和自定义“data-toggle”属性，且值必须和最外容器类名一致
- 下拉菜单项使用一个ul列表，并且定义一个类名为“dropdown-menu”

#### 下拉分割线
在Bootstrap框架中的下拉菜单还提供了下拉分隔线，假设下拉菜单有两个组，那么组与组之间可以通过添加一个空的< li>，并且给这个< li>添加类名“divider”来实现添加下拉分隔线的功能。

```html
<button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
    食物
    <span class="caret"></span>
  </button>
  <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">苹果</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">香蕉</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">梨</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">桃</a></li>
    <li role="presentation" class="divider"></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">芹菜</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">萝卜</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">茄子</a></li>
    <li role="presentation" class="divider"></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">米饭</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">馒头</a></li>
    <li role="presentation"><a role="menuitem" tabindex="-1" href="#">面条</a></li>
  </ul>
```

#### 菜单标题
上一小节讲解通过添加“divider”可以将下拉菜单分组，为了让这个分组更明显，还可以给每个组添加一个头部（标题）。

通过给li标签添加“.dropdown-header”类来实现：
```html
<div class="dropdown">
<button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
下拉菜单
<span class="caret"></span>
</button>
<ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
<li role="presentation" class="dropdown-header">第一部分菜单头部</li>
<li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
…
<li role="presentation" class="divider"></li>
<li role="presentation" class="dropdown-header">第二部分菜单头部</li>
…
<li role="presentation"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
</ul>
</div>
```

#### 对齐方式
Bootstrap框架中下拉菜单默认是**左对齐**，如果你想让下拉菜单相对于父容器**右对齐**时，可以在“dropdown-menu”上添加一个“pull-right”或者“dropdown-menu-right”类名

```html
<div class="dropdown">
  <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
  下拉菜单
  <span class="caret"></span>
  </button>
  <ul class="dropdown-menu pull-right" role="menu" aria-labelledby="dropdownMenu1">
   …
  </ul>
</div>
```

#### 菜单项状态
下拉菜单项的默认的状态（不用设置）有悬浮状态（:hover）和焦点状态（:focus）

下拉菜单项除了上面两种状态，还有**当前状态（.active）和禁用状态（.disabled）**。这两种状态使用方法只需要在对应的菜单项上添加对应的类名：
```
<div class="dropdown">
  <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown">
  下拉菜单
  <span class="caret"></span>
  </button>
  <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenu1">
    <li role="presentation" class="active"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
    ….
    <li role="presentation" class="disabled"><a role="menuitem" tabindex="-1" href="#">下拉菜单项</a></li>
  </ul>
</div>
```

### 按钮
按钮组和下拉菜单组件一样，需要依赖于button.js插件才能正常运行。不过我们同样可以直接只调用bootstrap.js文件。因为这个文件已集成了button.js插件功能。

#### 按钮组
使用一个名为“btn-group”的容器，把多个按钮放到这个容器中。  

除了可以使用< button>元素之外，还可以使用其他标签元素，比如< a>标签。唯一要保证的是：不管使用什么标签，**“.btn-group”容器里的标签元素需要带有类名“.btn”**。

#### 按钮工具栏
在富文本编辑器中，将按钮组分组排列在一起，比如说复制、剪切和粘贴一组；左对齐、中间对齐、右对齐和两端对齐一组。Bootstrap框架按钮工具栏也提供了这样的制作方法，你只需要**将按钮组“btn-group”按组放在一个大的容器“btn-toolbar”中**。
```
<div class="btn-toolbar">
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
  <div class="btn-group">
    …
  </div>
</div>
```

**按钮组大小设置**
- .btn-group-lg:大按钮组
- .btn-group-sm:小按钮组
- .btn-group-xs:超小按钮组


#### 嵌套分组
很多时候，我们常把下拉菜单和普通的按钮组排列在一起，实现类似于导航菜单的效果。

使用的时候，只需要**把当初制作下拉菜单的“dropdown”的容器换成“btn-group”，并且和普通的按钮放在同一级**。

```html
<div class="btn-group">
<button class="btnbtn-default" type="button">首页</button>
<button class="btnbtn-default" type="button">产品展示</button>
<button class="btnbtn-default" type="button">案例分析</button>
<button class="btnbtn-default" type="button">联系我们</button>
<div class="btn-group">
   <button class="btnbtn-default dropdown-toggle" data-toggle="dropdown" type="button">关于我们<span class="caret"></span></button>
   <ul class="dropdown-menu">
         <li><a href="##">公司简介</a></li>
         <li><a href="##">企业文化</a></li>
         <li><a href="##">组织结构</a></li>
         <li><a href="##">客服服务</a></li>
    </ul>
</div>
</div>
```

#### 垂直分组
我们只需要把水平分组的“btn-group”类名换成“btn-group-vertical”即可。

#### 等分按钮
等分按钮的效果在移动端上特别的实用。整个按钮组宽度是容器的100%，而按钮组里面的每个按钮平分整个容器宽度。例如，如果你按钮组里面有五个按钮，那么每个按钮是20%的宽度，如果有四个按钮，那么每个按钮是25%宽度，以此类推。
**
等分按钮也常被称为是自适应分组按钮，其实现方法也非常的简单，**只需要在按钮组“btn-group”上追加一个“btn-group-justified”类名**

```html
<div class="btn-wrap">
<div class="btn-group btn-group-justified">
  <a class="btnbtn-default" href="#">首页</a>
  <a class="btnbtn-default" href="#">产品展示</a>
  <a class="btnbtn-default" href="#">案例分析</a>
  <a class="btnbtn-default" href="#">联系我们</a>
</div>
</div>
```

#### 按钮下拉菜单
按钮下拉菜单仅从外观上看和上一节介绍的下拉菜单效果基本上是一样的。不同的是在普通的下拉菜单的基础上封装了按钮（.btn）样式效果。简单点说就是点击一个按钮，会显示隐藏的下拉菜单。

按钮下拉菜单其实就是普通的下拉菜单，只不过把“< a>”标签元素换成了“< button>”标签元素。唯一不同的是外部容器“div.dropdown”换成了“div.btn-group”。如下所示：
```html
<div class="btn-group">
      <button class="btn btn-default dropdown-toggle" data-toggle="dropdown" type="button">按钮下拉菜单<span class="caret"></span></button>
      <ul class="dropdown-menu">
          <li><a href="##">按钮下拉菜单项</a></li>
          <li><a href="##">按钮下拉菜单项</a></li>
          <li><a href="##">按钮下拉菜单项</a></li>
          <li><a href="##">按钮下拉菜单项</a></li>
      </ul>
</div>
```

#### 向上、向下三角形
按钮的向下三角形，我们是通过在<button>标签中添加一个“<span>”标签元素，并且命名为“caret”
```html
<button class="btn btn-default dropdown-toggle" data-toggle="dropdown" type="button">按钮下拉菜单<span class="caret"></span></button>
```
有的时候我们的下拉菜单会向上弹起（接下来一个小节会介绍），这个时候我们的三角方向需要朝上显示，实现方法：需要**在“.btn-group”类上追加“dropup”类名**
```html
<div class="btn-group dropup">
  <button class="btn btn-default dropdown-toggle" data-toggle="dropdown" type="button">按钮下拉菜单<span class="caret"></span></button>
  <ul class="dropdown-menu">
        <li><a href="##">按钮下拉菜单项</a></li>
        <li><a href="##">按钮下拉菜单项</a></li>
        <li><a href="##">按钮下拉菜单项</a></li>
        <li><a href="##">按钮下拉菜单项</a></li>
  </ul>
</div>
```
### 导航
Bootstrap框架中制作导航条主要通过“.nav”样式。默认的“.nav”样式不提供默认的导航样式，必须附加另外一个样式才会有效，比如“nav-tabs”、“nav-pills”之类。
```html
<ul class="nav nav-tabs">
    <li><a href="##">Home</a></li>
    <li><a href="##">CSS3</a></li>
 	<li><a href="##">Sass</a></li>
 	<li><a href="##">jQuery</a></li>
 	<li><a href="##">Responsive</a></li>
</ul>
```

#### 标签型tab导航
标签形导航，也称为选项卡导航。特别是在很多内容分块显示的时，使用这种选项卡来分组十分适合。

标签形导航是通过“nav-tabs”样式来实现。在制作标签形导航时需要在原导航“nav”上追加此类名
```html
<ul class="nav nav-tabs">
     <li><a href="##">Home</a></li>
     <li><a href="##">CSS3</a></li>
     <li><a href="##">Sass</a></li>
     <li><a href="##">jQuery</a></li>
     <li><a href="##">Responsive</a></li>
</ul>
```
一般情况之下，选项卡教会有一个当前选中项。其实在Bootstrap框架也相应提供了。假设我们想让“Home”项为当前选中项，只需要在其标签上添加类名“class="active"”即可
```html
<ul class="nav nav-tabs">
    <li class="active"><a href="##">Home</a></li>
    …
</ul>
```
除了当前项之外，有的选项卡还带有禁用状态，实现这样的效果，只需要在标签项上添加“class="disabled"”即可
```html
<ul class="nav nav-tabs">
     <li class="active"><a href="##">Home</a></li>
     …
     <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```

#### 胶囊形(pills)导航
其实现方法和“nav-tabs”类似，同样的结构，只需要把类名“nav-tabs”换成“nav-pills”
```html
<ul class="nav nav-pills">
      <li class="active"><a href="##">Home</a></li>
      <li><a href="##">CSS3</a></li>
      <li><a href="##">Sass</a></li>
      <li><a href="##">jQuery</a></li>
      <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```

#### 垂直堆叠的导航
制作垂直堆叠导航只需要在“nav-pills”的基础上添加一个“nav-stacked”类名即可
```html
<ul class="nav nav-pills nav-stacked">
     <li class="active"><a href="##">Home</a></li>
     <li><a href="##">CSS3</a></li>
     <li><a href="##">Sass</a></li>
     <li><a href="##">jQuery</a></li>
     <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```
在下拉菜单一节中，下拉菜单组与组之间有一个分隔线。其实在垂直堆叠导航也具有这样的效果，只需要添加在导航项之间添加“< li class=”nav-divider”>< /li>”即可
```html
<ul class="nav nav-pills nav-stacked">
    <li class="active"><a href="##">Home</a></li>
    <li><a href="##">CSS3</a></li>
    <li><a href="##">Sass</a></li>
    <li><a href="##">jQuery</a></li>
   <li class="nav-divider"></li>
    <li class="disabled"><a href="##">Responsive</a></li>
</ul>
```

#### 自适应导航
自适应导航指的是导航占据容器全部宽度，而且菜单项可以像表格的单元格一样自适应宽度。自适应导航和前面使用“btn-group-justified”制作的自适应按钮组是一样的。只不过在制作自适应导航时更换了**另一个类名“nav-justified”。当然他需要和“nav-tabs”或者“nav-pills”配合在一起使用**。
```html
<ul class="nav nav-tabs nav-justified">
     <li class="active"><a href="##">Home</a></li>
     <li><a href="##">CSS3</a></li>
     <li><a href="##">Sass</a></li>
     <li><a href="##">jQuery</a></li>
     <li><a href="##">Responsive</a></li>
</ul>
```

#### 二级导航
只需要将li当作父容器，使用类名“dropdown”，同时在li中嵌套另一个列表ul，使用前面介绍下拉菜单的方法就可以
```html
<ul class="nav nav-pills">
     <li class="active"><a href="##">首页</a></li>
     <li class="dropdown">
        <a href="##" class="dropdown-toggle" data-toggle="dropdown">教程<span class="caret"></span></a>
        <ul class="dropdown-menu">
            <li><a href="##">CSS3</a></li>
            …
       </ul>
     </li>
     <li><a href="##">关于我们</a></li>
</ul>
```
只需要添加“< li class=”nav-divider”>< /li>”就可以实现分割线效果

#### 面包屑式导航
面包屑(Breadcrumb)一般用于导航，主要是起的作用是告诉用户现在所处页面的位置（当前位置）。

使用方式就很简单，为ol加入breadcrumb类：
```html
<ol class="breadcrumb">
  <li><a href="#">首页</a></li>
  <li><a href="#">我的书</a></li>
  <li class="active">《图解CSS3》</li>
</ol>
```

## 导航条、分页导航
### 导航条
导航条（navbar）和上一节介绍的导航（nav），就相差一个字，多了一个“条”字。其实在Bootstrap框架中他们还是明显的区别。在导航条(navbar)中有一个背景色、而且导航条可以是纯链接（类似导航），也可以是表单，还有就是表单和导航一起结合等多种形式。

#### 基础导航条
在制作一个基础导航条时，主要分以下几步：  

1. 首先在制作导航的列表(< ul class=”nav”>)基础上添加类名“navbar-nav”  
2. 在列表外部添加一个容器（div），并且使用类名“navbar”和“navbar-default”  

```html
<div class="navbar navbar-default" role="navigation">
     <ul class="nav navbar-nav">
	 	<li class="active"><a href="##">网站首页</a></li>
        <li><a href="##">系列教程</a></li>
        <li><a href="##">名师介绍</a></li>
        <li><a href="##">成功案例</a></li>
        <li><a href="##">关于我们</a></li>
	 </ul>
</div>
```
#### 为导航条添加标题、二级菜单及状态
在Web页面制作中，常常在菜单前面都会有一个标题（文字字号比其它文字稍大一些），其实在Bootstrap框架也为大家做了这方面考虑，其**通过“navbar-header”和“navbar-brand”来实现**
```html
<div class="navbar navbar-default" role="navigation">
  　<div class="navbar-header">
  　    <a href="##" class="navbar-brand">慕课网</a>
  　</div>
    <ul class="nav navbar-nav">
	   <li class="active"><a href="##">网站首页</a></li>
       <li><a href="##">系列教程</a></li>
       <li><a href="##">名师介绍</a></li>
       <li><a href="##">成功案例</a></li>
       <li><a href="##">关于我们</a></li>
	 </ul>
</div>
```
也可以带有**二级菜单**的导航条
```html
<div class="navbar navbar-default" role="navigation">
  　<div class="navbar-header">
  　    <a href="##" class="navbar-brand">慕课网</a>
  　</div>
	<ul class="nav navbar-nav">
	 	<li class="active"><a href="##">网站首页</a></li>
        <li class="dropdown">
          <a href="##" data-toggle="dropdown" class="dropdown-toggle">系列教程<span class="caret"></span></a>
          <ul class="dropdown-menu">
        	<li><a href="##">CSS3</a></li>
        	<li><a href="##">JavaScript</a></li>
        	<li class="disabled"><a href="##">PHP</a></li>
          </ul>
       </li>
       <li><a href="##">名师介绍</a></li>
       <li><a href="##">成功案例</a></li>
       <li><a href="##">关于我们</a></li>
	</ul>
</div>
```

#### 带表单的导航条
在Bootstrap框架中提供了一个“navbar-form”，使用方法很简单，在navbar容器中放置一个带有navbar-form类名的表单
```html
<form action="##" class="navbar-form navbar-left" rol="search">
   	<div class="form-group">
   	    <input type="text" class="form-control" placeholder="请输入关键词" />
   	</div>
    <button type="submit" class="btn btn-default">搜索</button>
</form>
```

#### 导航条中的按钮、文本和链接
- 导航条中的按钮navbar-btn
- 导航条中的文本navbar-text
- 导航条中的普通链接navbar-link

需要和navbar-brand、navbar-nav配合起来使用。而且对数量也有一定的限制，==一般情况在使用一到两个不会有问题，超过两个就会有问题。==

#### 固定导航条
设计师希望导航条固定在浏览器顶部或底部，这种固定式导航条的应用在移动端开发中更为常见。Bootstrap框架提供了两种固定导航条的方式
- .navbar-fixed-top：导航条固定在浏览器窗口顶部
- .navbar-fixed-bottom：导航条固定在浏览器窗口底部

为了避免固定导航条遮盖内容，我们需要在body上做一些处理：

```CSS
body {
  padding-top: 70px;/*有顶部固定导航条时设置*/
  padding-bottom: 70px;/*有底部固定导航条时设置*/
}
```
因为固定导航条默认高度是50px，我们一般设置padding-top和padding-bottom的值为70px，当然有的时候还是需要具体情况具体分析。

还可以把固定导航条都放在页面内容前面：
```html
<div class="navbar navbar-default navbar-fixed-top" role="navigation">
　…
</div>
<div class="navbar navbar-default navbar-fixed-bottom" role="navigation">
　…
</div>
<div class="content">我是内容</div>
```

#### 响应式导航条
使用方法：
1. 保证在窄屏时需要折叠的内容必须包裹在带一个div内，并且**为这个div加入collapse、navbar-collapse两个类名**。最后为这个div添加一个class类名或者id名。
2. 保证在窄屏时要显示的图标样式（固定写法）：
```html
<button class="navbar-toggle" type="button" data-toggle="collapse">
  <span class="sr-only">Toggle Navigation</span>
  <span class="icon-bar"></span>
  <span class="icon-bar"></span>
  <span class="icon-bar"></span>
</button>
```
3. 为button添加data-target=".类名/#id名"，究竞是类名还是id名呢？由需要折叠的div来决定。  

例子：
```html
<div class="navbar navbar-default" role="navigation">
  <div class="navbar-header">
     　<!-- .navbar-toggle样式用于toggle收缩的内容，即nav-collapse collapse样式所在元素 -->
       <button class="navbar-toggle" type="button" data-toggle="collapse" data-target=".navbar-responsive-collapse">
         <span class="sr-only">Toggle Navigation</span>
         <span class="icon-bar"></span>
         <span class="icon-bar"></span>
         <span class="icon-bar"></span>
       </button>
       <!-- 确保无论是宽屏还是窄屏，navbar-brand都显示 -->
       <a href="##" class="navbar-brand">啦啦</a>
  </div>
  <!-- 屏幕宽度小于768px时，div.navbar-responsive-collapse容器里的内容都会隐藏，显示icon-bar图标，当点击icon-bar图标时，再展开。屏幕大于768px时，默认显示。 -->
  <div class="collapse navbar-collapse navbar-responsive-collapse">
    	<ul class="nav navbar-nav">
      		<li class="active"><a href="##">啦啦</a></li>
      		<li><a href="##">啦啦</a></li>
      		<li><a href="##">啦啦</a></li>
      		<li><a href="##">啦啦</a></li>
      		<li><a href="##">啦啦</a></li>
	 	</ul>
  </div>
</div>
```

#### 反色导航条
反色导航条其实是Bootstrap框架为大家提供的第二种风格的导航条，与默认的导航条相比，使用方法并无区别，只是将navbar-deafult类名换成navbar-inverse。其变化只是导航条的背景色和文本做了修改。

### 分页导航
在Bootstrap框架中提供了两种分页导航：
- 带页码的分页导航
- 带翻页的分页导航

#### 带页码的分页导航
在Bootstrap框架中使用的是ul>li>a这样的结构，在ul标签上加入pagination方法
```html
<ul class="pagination">
   <li><a href="#">&laquo;</a></li>
   <li><a href="#">1</a></li>
   <li><a href="#">2</a></li>
   <li><a href="#">3</a></li>
   <li><a href="#">4</a></li>
   <li><a href="#">5</a></li>
   <li><a href="#">&raquo;</a></li>
</ul>
```
大小设置：
- 通过“pagination-lg”让分页导航变大
- 通过“pagination-sm”让分页导航变小

```html
<ul class="pagination pagination-lg">
 …
</ul>
<ul class="pagination">
 …
</ul>
<ul class="pagination pagination-sm">
 …
</ul>
```

#### 带翻页的分页导航
Bootstrap框架除了提供带页码的分页导航之外还提供了翻页导航。这种分页导航常常在一些简单的网站上看到，比如说个人博客，杂志网站等。**这种分页导航是看不到具体的页码，只会提供一个“上一页”和“下一页”的按钮。**

在实际使用中，翻页分页导航和带页码的分页导航类似，为ul标签加入pager类：
```html
<ul class="pager">
   <li><a href="#">&laquo;上一页</a></li>
   <li><a href="#">下一页&raquo;</a></li>
</ul>
```
对齐样式设置：
- previous：让“上一步”按钮居左
- next：让“下一步”按钮居右

```html
<ul class="pager">
   <li class="previous"><a href="#">&laquo;上一页</a></li>
   <li class="next"><a href="#">下一页&raquo;</a></li>
</ul>
```

### 标签
在一些Web页面中常常会添加一个标签用来告诉用户一些额外的信息，比如说在导航上添加了一个新导航项，可能就会加一个“new”标签，来告诉用户。这是新添加的导航项。

在Bootstrap框架中特意将这样的效果提取出来成为一个标签组件，并且**以“.label”样式来实现**高亮显示。
```html
<h3>Example heading <span class="label label-default">New</span></h3>
```
颜色样式设置：  

和按钮元素button类似，label样式也提供了多种颜色：
- label-deafult:默认标签，深灰色
- label-primary：主要标签，深蓝色
- label-success：成功标签，绿色
- label-info：信息标签，浅蓝色
- label-warning：警告标签，橙色
- label-danger：错误标签，红色

### 徽章
从某种意义上来说，徽章效果和前面介绍的标签效果是极其的相似。也是用来做一些提示信息使用。常出现的是一些系统发出的信息，比如你登录你的twitter后，如果你信息没有看，系统会告诉你有多少信息未读

在Bootstrap框架中，把这种效果称作为徽章效果，**使用“badge”样式来实现**。
```html
<a href="#">Inbox <span class="badge">42</span></a>
```

---

此页面为本人学习慕课网Bootstrap基础教程的个人学习笔记，原地址 https://www.imooc.com/learn/141