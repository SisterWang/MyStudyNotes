# Bootstrap基础学习（四）
## 其他内置组件
### 缩略图
缩略图在网站中最常用的地方就是产品列表页面，一行显示几张图片，有的在图片底下（左侧或右侧）带有标题、描述等信息。Bootstrap框架将这一部独立成一个模块组件。并通过“thumbnail”样式配合bootstrap的网格系统来实现。
```html
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="#" style="height: 180px; width: 100%; display: block;" alt="">
            </a>
        </div>
    …
    </div>
</div>
```

还可以让缩略图配合标题、描述内容，按钮等。在仅有缩略图的基础上，添加了一个div名为“caption“的容器，在这个容器中放置其他内容，比如说标题，文本描述，按钮等：  
```html
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="#" style="height: 180px; width: 100%; display: block;" alt="">
            </a>
            <div class="caption">
                <h3>标题</h3>
                <p>描述</p>
                <p>
                    <a href="##" class="btn btn-primary">按钮1</a>
                    <a href="##" class="btn btn-info">按钮2</a>
                </p>
            </div>
        </div>
    …
    </div>
</div>
```
### 警示框
#### 一般警示框
在网站中，网页总是需要和用户一起做沟通与交流。特别是当用户操作上下文为用户提供一些有效的警示框，比如说告诉用户操作成功、操作错误、提示或者警告等。

- 成功警示框：告诉用用户操作成功，在“alert”样式基础上追加“alert-success”样式，具体呈现的是背景、边框和文本都是绿色；
- 信息警示框：给用户提供提示信息，在“alert”样式基础上追加“alert-info”样式，具体呈现的是背景、边框和文本都是浅蓝色；
- 警告警示框：提示用户小心操作（提供警告信息），在“alert”样式基础上追加“alert-warning”样式，具体呈现的是背景、边框、文本都是浅黄色；
- 错误警示框：提示用户操作错误，在“alert”样式基础上追加“alert-danger”样式，具体呈现的是背景、边框和文本都是浅红色。

可以在类名为“alert”的div容器里放置提示信息。实现不同类型警示框，只需要在“alert”基础上追加对应的类名，如下：
```html
<div class="alert alert-success" role="alert">恭喜您操作成功！</div>
<div class="alert alert-info" role="alert">请输入正确的密码</div>
<div class="alert alert-warning" role="alert">您已操作失败两次，还有最后一次机会</div>
<div class="alert alert-danger" role="alert">对不起，您输入的密码有误</div>
```
#### 可关闭的警示框
只需要在默认的警示框里面添加一个关闭按钮。然后进行三个步骤：
1. 需要在基本警示框“alert”的基础上添加“alert-dismissable”样式。
2. 在button标签中加入class="close"类，实现警示框关闭按钮的样式。
3. 要确保关闭按钮元素上设置了自定义属性：“data-dismiss="alert"”（因为可关闭警示框需要借助于Javascript来检测该属性，从而控制警示框的关闭）。
```html
<div class="alert alert-success alert-dismissable" role="alert">
    <button class="close" type="button" data-dismiss="alert">&times;</button>
    恭喜您操作成功！
</div>
```

#### 警示框的链接
在Bootstrap框架中对警示框里的链接样式做了一个高亮显示处理。为不同类型的警示框内的链接进行了加粗处理，并且颜色相应加深。 

Bootstrap框架是通过给警示框加的链接添加一个名为“alert-link”的类名，通过“alert-link”样式给链接提供高亮显示。

```html
<div class="alert alert-success" role="alert">
    <strong>Well done!</strong> 
    You successfully read 
    <a href="#" class="alert-link">this important alert message</a>
</div>
```

### 进度条
#### 基本进度条
Bootstrap框架中提供了两个容器，外容器使用“progress”样式，子容器使用“progress-bar”样式。其中progress用来设置进度条的容器样式，而progress-bar用于限制进度条的进度。
```html
<div class="progress">
       <div class="progress-bar" style="width:40%"></div>
</div>
```

#### 彩色进度条
只需要在基础的进度上增加对应的类名。

- progress-bar-info：表示信息进度条，进度条颜色为蓝色
- progress-bar-success：表示成功进度条，进度条颜色为绿色
- progress-bar-warning：表示警告进度条，进度条颜色为黄色
- progress-bar-danger：表示错误进度条，进度条颜色为红色

```html
<div class="progress">
    <div class="progress-bar progress-bar-success" style="width:40%"></div>
</div>
```

#### 条纹进度条
使用Bootstrap框架中的条纹进度条只需要在进度条的容器“progress”基础上增加类名“progress-striped”，当然，如果你要让你的进度条条纹像彩色进度一样，具有彩色效果，你只需要在进度条上增加相应的颜色类名。
```html
<div class="progress progress-striped">
    <div class="progress-bar progress-bar-success" style="width:40%"></div>
</div>
```

#### 动态条纹进度条
在进度条“progress progress-striped”两个类的基础上再加入“active”类名。
```html
<div class="progress progress-striped active">
    <div class="progress-bar progress-bar-success" style="width:40%"></div>
</div>
```

#### 层叠进度条
Bootstrap框架除了提供上述几种进度条之外，还提供了一种层叠进度条，层叠进度条，可以将不同状态的进度条放置在一起，按水平方式排列。具体使用如下：  
```html
<div class="progress">
    <div class="progress-bar progress-bar-success" style="width:20%"></div>
    <div class="progress-bar progress-bar-info" style="width:10%"></div>
    <div class="progress-bar progress-bar-warning" style="width:30%"></div>
    <div class="progress-bar progress-bar-danger" style="width:15%"></div>
</div>
```

#### 带Label的进度条
只需要在进度条中添加你需要的值
```html
<div class="progress">
    <div class="progress-bar progress-bar-success"
    role="progressbar" aria-valuenow="20" aria-valuemin="0" aria-valuemax="100"
    style="width:20%">20%</div>
</div>
```
有一种特殊情形，当进度条处于开始位置，也就是进度条的值为0%时:
```html
<div class="progress">
    <div class="progress-bar" aria-valuenow="0">0%</div>
</div>
```

### 媒体对象
#### 默认媒体对象
媒体对象一般是成组出现，而一组媒体对象常常包括以下几个部分：

1. 媒体对像的容器：常使用“media”类名表示，用来容纳媒体对象的所有内容
2. 媒体对像的对象：常使用“media-object”表示，就是媒体对象中的对象，常常是图片
3. 媒体对象的主体：常使用“media-body”表示，就是媒体对像中的主体内容，可以是任何元素，常常是图片侧边内容
4. 媒体对象的标题：常使用“media-heading”表示，就是用来描述对象的一个标题，**此部分可选**

除了上面四个部分之外，在Bootstrap框架中还常常使用“pull-left”或者“pull-right”来控制媒体对象中的对象浮动方式。
```html
<div class="media">
    <a class="pull-left" href="#">
        <img class="media-object" src="" alt="...">
    </a>
    <div class="media-body">
        <h4 class="media-heading">标题</h4>
        <div>描述</div>
    </div>
</div>
```

#### 媒体对象的嵌套
在上一个对象主体中嵌套下一个对象：
```html
<div class="media">
    <a class="pull-left" href="#">
        <img class="media-object" src="…" alt="...">
    </a>
    <div class="media-body">
        <h4 class="media-heading">Media Heading</h4>
        <div>…</div>
        <div class="media">
            <a class="pull-left" href="#">
                <img class="media-object" src="…" alt="...">
            </a>
            <div class="media-body">
                <h4 class="media-heading">Media Heading</h4>
                <div>…</div>
                <div class="media">
                    <a class="pull-left" href="#">
                        <img class="media-object" src="…" alt="...">
                    </a>
                    <div class="media-body">
                        <h4 class="media-heading">Media Heading</h4>
                        <div>...</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
```

#### 媒体对象列表
在写结构的时候可以使用ul，并且在ul上添加类名“media-list”，而在li上使用“media”:
```html
<ul class="media-list">
    <li class="media">
        <a class="pull-left" href="#">
            <img class="media-object" src=" " alt="...">
        </a>
        <div class="media-body">
            <h4 class="media-heading">Media Header</h4>
            <div>…</div>
        </div>
    </li>
    <li class="media">…</li>
    <li class="media">…</li>
</ul>
```

### 列表组
列表组是Bootstrap框架新增的一个组件，可以用来制作列表清单、垂直导航等效果，也可以配合其他的组件制作出更漂亮的组件。

#### 基础列表组
基础列表组，看上去就是去掉了列表符号的列表项，并且配上一些特定的样式。在Bootstrap框架中的基础列表组主要包括两个部分：

- 列表组容器，常用的是ul元素，当然也可以是ol或者div元素
- list-group-item：列表项，常用的是li元素，当然也可以是div元素

```html
<ul class="list-group">
    <li class="list-group-item">1</li>
    <li class="list-group-item">2</li>
    <li class="list-group-item">3</li>
    <li class="list-group-item">4</li>
    <li class="list-group-item">5</li>
</ul>
```

#### 带徽章的列表组
带徽章的列表组其实就是将Bootstrap框架中的徽章组件和基础列表组结合在一起的一个效果。具体做法很简单，只需要在“list-group-item”中添加徽章组件“badge”：
```html
<ul class="list-group">
    <li class="list-group-item">
        <span class="badge">13</span>1
    </li>
    <li class="list-group-item">
        <span class="badge">456</span>2
    </li>
    <li class="list-group-item">
        <span class="badge">892</span>3
    </li>
    <li class="list-group-item">
        <span class="badge">90</span>4
    </li>
    <li class="list-group-item">
        <span class="badge">1290</span>5
    </li>
</ul>
```

#### 带链接的列表组
在列表项的任何区域都具备可点击:在a标签中添加 ".list-group-item"
```html
<div class="list-group">
    <a href="##" class="list-group-item">1</a>
    <a href="##" class="list-group-item"><span class="badge">220</span>2</a>
    <a href="##" class="list-group-item">3</a>
</div>
```

#### 自定义列表组
Bootstrap框加在链接列表组的基础上新增了两个样式：
- list-group-item-heading：用来定义列表项头部样式
- list-group-item-text：用来定义列表项主要内容

这两个样式最大的作用就是用来帮助开发者可以自定义列表项里的内容，如下面的示例：
```html
<div class="list-group">
    <a href="##" class="list-group-item">
        <h4 class="list-group-item-heading">1</h4>
        <p class="list-group-item-text">...</p>
    </a>
    <a href="##" class="list-group-item">
        <h4 class="list-group-item-heading">2</h4>
        <p class="list-group-item-text">...</p>
    </a>
</div>
```

#### 列表项的状态设置
Bootstrap框架也给组合列表项提供了状态效果，特别是链接列表组。比如常见状态和禁用状态等。实现方法和前面介绍的组件类似，在列表组中只需要在对应的列表项中添加类名：
- active:表示当前状态
- disabled:表示禁用状态

#### 多彩列表组
列表组组件和警告组件一样，Bootstrap为不同的状态提供了不同的背景颜色和文本色，可以使用这几个类名定义不同背景色的列表项：
- list-group-item-success：成功，背景色绿色
- list-group-item-info：信息，背景色蓝色
- list-group-item-warning：警告，背景色为黄色
- list-group-item-danger：错误，背景色为红色

### 面板
面板（Panels）是Bootstrap框架新增的一个组件，其主要作用就是用来处理一些其他组件无法完成的功能。

#### 基础面板
基础面板非常简单，就是一个div容器运用了“panel”样式，产生一个具有边框的文本显示块。由于“panel”不控制主题颜色，所以在“panel”的基础上增加一个控制颜色的主题“panel-default”，另外在里面添加了一个“div.panel-body”来放置面板主体内容：
```html
<div class="panel panel-default">
    <div class="panel-body">我是一个基础面板，带有默认主题样式风格</div>
</div>
```

#### 带有头和尾的面板
基础面板看上去太简单了，Bootstrap为了丰富面板的功能，特意为面板增加“面板头部”和“页面尾部”的效果：
- panel-heading：用来设置面板头部样式
- panel-footer：用来设置面板尾部样式

```html
<div class="panel panel-default">
    <div class="panel-heading">标题</div>
    <div class="panel-body">正文</div>
    <div class="panel-footer">落款</div>
</div>
```

#### 彩色面板
- panel-primary：重点蓝
- panel-success：成功绿
- panel-info:信息蓝
- panel-warning：警告黄
- panel-danger：危险红
```html
<div class="panel panel-primary">…</div>
<div class="panel panel-success">…</div>
<div class="panel panel-info">…</div>
<div class="panel panel-warning">…</div>
<div class="panel panel-danger">…</div>
```
#### 面板中嵌套表格
一般情况下可以把面板理解为一个区域，在使用面板的时候，都会在panel-body放置需要的内容，可能是图片、表格或者列表等。
```html
<div class="panel panel-default">
    <div class="panel-heading">标题</div>
    <div class="panel-body">
    <p>描述
    </p>
    <table class="table table-bordered">
        <thead>
            <tr>
                <th>＃</th>
                <th>1</th>
                <th>2</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>d1</td>
                <td>d2</td>
            </tr>
        </tbody>
    </table>
    </div>
    <div class="panel-footer">落款</div>
</div>
```
在实际应用运中，你或许希望表格和面板边缘不需要有任何的间距。但由于panel-body设置了一个padding：15px的值，为了实现这样的效果。我们在实际使用的时候需要把table提取到panel-body外面：
```html
<div class="panel panel-default">
    <div class="panel-heading">标题</div>
    <div class="panel-body">…</div>
    <table class="table table-bordered">…</table>
    <div class="panel-footer">落款</div>
</div>
```
#### 面板中嵌套列表组
同嵌套表格


## JavaScript插件

### 导入
Bootstrap的JavaScript插件可以单独导入到页面中，也可以一次性导入到页面中。因为在Bootstrap中的JavaScript插件都是依赖于jQuery库，所以不论是单独导入还一次性导入之前必须先导入jQuery库。

#### 一次性导入
Bootstrap提供了一个单一的文件，这个文件包含了Bootstrap的所有JavaScript插件，即bootstrap.js（压缩版本：bootstrap.min.js）。  

```html
<!—导入jQuery版本库，因为Bootstrap的JavaScript插件依赖于jQuery -->
<script src="http://libs.baidu.com/jquery/1.9.0/jquery.js"></script>
<!—- 一次性导入所有Bootstrap的JavaScript插件（压缩版本） -->
<script src="js/bootstrap.min.js"></script>
```

#### 单独导入
为方便单独导入特效文件，Bootstrap V3.2中提供了12种JavaScript插件，他们分别是：

  ☑ 动画过渡（Transitions）:对应的插件文件“transition.js”

  ☑ 模态弹窗（Modal）:对应的插件文件“modal.js”

  ☑ 下拉菜单（Dropdown）：对应的插件文件“dropdown.js”

  ☑ 滚动侦测（Scrollspy）：对应的插件文件“scrollspy.js”

  ☑ 选项卡（Tab）：对应的插件文件“tab.js”

  ☑ 提示框（Tooltips）：对应的插件文件“tooltop.js”

  ☑ 弹出框（Popover）：对应的插件文件“popover.js”

  ☑ 警告框（Alert）：对应的插件文件“alert.js”

  ☑ 按钮（Buttons）：对应的插件文件“button.js”

  ☑ 折叠/手风琴（Collapse）：对应的插件文件“collapse.js”

  ☑ 图片轮播Carousel：对应的插件文件“carousel.js”

  ☑ 自动定位浮标Affix：对应的插件文件“affix.js”
  
### 动画过渡
源文件：transition.js  
transition.js文件为Bootstrap具有过渡动画效果的组件提供了动画过渡效果。不过需要注意的是，这些过渡动画都是采用CSS3来实现的，所以IE6-8浏览器是不具备这些过渡动画效果。

### 模态弹出框
源文件：modal.js。  
在 Bootstrap 框架中把模态弹出框统一称为 Modal。这种弹出框效果在大多数 Web 网站的交互中都可见。比如点击一个按钮弹出一个框，弹出的框可能是一段文件描述，也可能带有按钮操作，也有可能弹出的是一张图片。


#### 结构
Bootstrap框架中的模态弹出框，分别运用了“modal”、“modal-dialog”和“modal-content”样式，而弹出窗真正的内容都放置在“modal-content”中，其主要又包括三个部分：
1. 弹出框头部，一般使用“modal-header”表示，主要包括标题和关闭按钮
2. 弹出框主体，一般使用“modal-body”表示，弹出框的主要内容
3. 弹出框脚部，一般使用“modal-footer”表示，主要放置操作按钮

```html
<div class="modal" id="mymodal">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
				<button type="button" class="close" data-dismiss="modal"><span aria-hidden="true">&times;</span><span class="sr-only">Close</span></button>
				<h4 class="modal-title">模态弹出窗标题</h4>
			</div>
			<div class="modal-body">
				<p>模态弹出窗主体内容</p>
			</div>
			<div class="modal-footer">
				<button type="button" class="btn btn-default" data-dismiss="modal">关闭</button>
				<button type="button" class="btn btn-primary">保存</button>
			</div>
		</div><!-- /.modal-content -->
	</div><!-- /.modal-dialog -->
</div><!-- /.modal -->
```

**两种尺寸选择：**  

Bootstrap框架还为模态弹出窗提供了不同尺寸，一个是大尺寸样式“modal-lg”，另一个是小尺寸样式“modal-sm”。

#### 触发模态弹出窗2种方法
**方法一：**  

模态弹出窗声明，只需要自定义两个必要的属性：data-toggle和data-target（bootstrap中声明式触发方法一般依赖于这些自定义的data-xxx 属性。比如data-toggle="" 或者 data-dismiss=""）。  

1. data-toggle必须设置为modal(toggle中文翻译过来就是触发器)；
2. data-target可以设置为CSS的选择符，也可以设置为模态弹出窗的ID值，一般情况设置为模态弹出窗的ID值，因为ID值是唯一的值。  

```html
<!-- 触发模态弹出窗的元素 -->
<button type="button" data-toggle="modal" data-target="#mymodal" class="btn btn-primary">点击我会弹出模态弹出窗</button>
<!-- 模态弹出窗 -->
<div class="modal fade" id="mymodal">
    <div class="modal-dialog">
        <div class="modal-content">
        <!-- 模态弹出窗内容 -->
        </div>
    </div>
</div>
```

**方法二：**
触发模态弹出窗也可以是一个链接< a>元素，那么可以使用链接元素自带的href属性替代data-target属性

```html
<!-- 触发模态弹出窗的元素 -->
<a data-toggle="modal" href="#mymodal" class=" btn btn-primary" >点击我会弹出模态弹出窗</a>
<!-- 模态弹出窗 -->
<div class="modal fade"  id="mymodal" >
    <div class="modal-dialog" >
        <div class="modal-content" >
        <!-- 模态弹出窗内容 -->
        </div>
    </div>
</div>
```

#### 为弹出框增加过渡动画效果
可通过给“.modal”增加类名“fade”为模态弹出框增加一个过渡动画效果。  

#### 参数说明
除了通过data-toggle和data-target来控制模态弹出窗之外，Bootstrap框架针对模态弹出框还提供了其他自定义data-属性，来控制模态弹出窗。比如说:是否有灰色背景modal-backdrop，是否可以按ESC键关闭模态弹出窗。  
![image](http://img.mukewang.com/544f09480001d6c409000872.jpg)

#### 模态弹出窗的使用（JavaScript触发）
除了使用自定义属性触发模态弹出框之外，还可以通过JavaScript方法来触发模态弹出窗。通过给一个元素一个事件，来触发。比如说给一个按钮一个单击事件，然后触发模态弹出窗。
```html
$(function(){
  $(".btn").click(function(){
    $("#mymodal").modal();
  });
});
```
#### JavaScript触发时的参数设置
![image](http://img.mukewang.com/544f0bd50001b34409020384.jpg)

---

此页面为本人学习慕课网BootStrap基础篇的个人学习笔记，原地址： https://www.imooc.com/learn/141