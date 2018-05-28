# Bootstrap基础学习（二）
## 表单
### 基础表单
对于基础表单，Bootstrap并未对其做太多的定制性效果设计，仅仅对表单内的fieldset、legend、label标签进行了定制。使用了类名“**form-control**”  
- 宽度变成了100%
- 设置了一个浅灰色（#ccc）的边框
- 具有4px的圆角
- 设置阴影效果，并且元素得到焦点之时，阴影和边框效果会有所变化
- 设置了placeholder的颜色为#999

### 水平表单
在Bootstrap框架中要实现水平表单效果，必须满足以下两个条件：
1. 在< form>元素是使用类名“**form-horizontal**”。
2. 配合Bootstrap框架的网格系统。  

### 内联表单
有时候我们需要将表单的控件都在一行内显示，只需要在< form>元素中添加类名“**form-inline**”即可。  

如果你要在input前面添加一个label标签时，会导致input换行显示。如果你必须添加这样的一个label标签，并且不想让input换行，你需要将label标签也放在容器“form-group”中。  

```
<form class="form-inline" role="form">
<div class="form-group">
  <label class="sr-only" for="exampleInputEmail2">邮箱</label>
  <input type="email" class="form-control" id="exampleInputEmail2" placeholder="请输入你的邮箱地址">
</div>
<div class="form-group">
  <label class="sr-only" for="exampleInputPassword2">密码</label>
  <input type="password" class="form-control" id="exampleInputPassword2" placeholder="请输入你的邮箱密码">
</div>
<div class="checkbox">
<label>
   <input type="checkbox">记住密码
</label>
</div>
<button type="submit" class="btnbtn-default">进入邮箱</button>
</form>
```
### 表单控件
每一个表单都是由表单控件组成。离开了控件，表单就失去了意义。
#### 输入框input
单行输入框，常见的文本输入框，也就是input的type属性值为text。在Bootstrap中使用input时也必须添加type类型，如果没有指定type类型，将无法得到正确的样式，因为Bootstrap框架都是通过input[type=“?”](其中?号代表type类型，比如说text类型，对应的是input[type=“text”])的形式来定义样式的。  

为了让控件在各种表单风格中样式不出错，需要添加类名“form-control”
```
<form role="form">
<div class="form-group">
<input type="email" class="form-control" placeholder="Enter email">
</div>
</form>
```

#### 下拉选择框select
Bootstrap框架中的下拉选择框使用和原始的一致，**多行选择**设置**multiple属性的值为multiple**。  


需要添加类名“form-control”
```
<form role="form">
<div class="form-group">
  <select class="form-control">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
    <option>5</option>
  </select>
  </div>
  <div class="form-group">
  <select multiple class="form-control">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
    <option>5</option>
  </select>
</div>
</form>
```

#### 文本域textarea
文本域和原始使用方法一样，设置rows可定义其高度，设置cols可以设置其宽度。但如果textarea元素中添加了类名“form-control”类名，则无需设置cols属性。因为Bootstrap框架中的“form-control”样式的表单控件宽度为100%或auto。
```
<form role="form">
  <div class="form-group">
    <textarea class="form-control" rows="3"></textarea>
  </div>
</form>
```

#### 复选框checkbox和单选择按钮radio
Bootstrap框架中checkbox和radio有点特殊，Bootstrap针对他们做了一些特殊化处理，主要是checkbox和radio与label标签配合使用会出现一些小问题（最头痛的是对齐问题）。使用Bootstrap框架，开发人员无需考虑太多，只需要按照下面的方法使用即可。
```
<form role="form">
<div class="checkbox">
<label>
<input type="checkbox" value="">
记住密码
</label>
</div>
<div class="radio">
<label>
<input type="radio" name="optionsRadios" id="optionsRadios1" value="love" checked>
喜欢
</label>
</div>
<div class="radio">
<label>
<input type="radio" name="optionsRadios" id="optionsRadios2" value="hate">
不喜欢
</label>
</div>
</form>
```
- 不管是checkbox还是radio都使用label包起来了
- checkbox连同label标签放置在一个名为“.checkbox”的容器内
- radio连同label标签放置在一个名为“.radio”的容器内
- 在Bootstrap框架中，主要借助“.checkbox”和“.radio”样式，来处理复选框、单选按钮与标签的对齐方式。
- 
#### 复选框和单选按钮水平排列
- 如果checkbox需要水平排列，只需要**在label标签上**添加类名“checkbox-inline”
- 如果radio需要水平排列，只需要**在label标签上**添加类名“radio-inline”
```
<form role="form">
  <div class="form-group">
    <label class="checkbox-inline">
      <input type="checkbox"  value="option1">游戏
    </label>
    <label class="checkbox-inline">
      <input type="checkbox"  value="option2">摄影
    </label>
    <label class="checkbox-inline">
    <input type="checkbox"  value="option3">旅游
    </label>
  </div>
  <div class="form-group">
    <label class="radio-inline">
      <input type="radio"  value="option1" name="sex">男性
    </label>
    <label class="radio-inline">
      <input type="radio"  value="option2" name="sex">女性
    </label>
    <label class="radio-inline">
      <input type="radio"  value="option3" name="sex">中性
    </label>
  </div>
</form>
```
#### 按钮
在Bootstrap框架中的按钮都是采用< button>来实现。

### 表单控件大小
可以通过设置控件的height，line-height，padding和font-size等属性来实现控件的高度设置。不过Bootstrap框架还提供了两个不同的类名，用来控制表单控件的高度。这两个类名是：  
1. input-sm:让控件比正常大小更小
2. input-lg:让控件比正常大小更大

```html
<input class="form-control input-lg" type="text" placeholder="添加.input-lg，控件变大">
<input class="form-control" type="text" placeholder="正常大小">
<input class="form-control input-sm" type="text" placeholder="添加.input-sm，控件变小">
```

### 表单控件状态
每一种状态都能给用户传递不同的信息，比如表单有焦点的状态可以告诉用户可以输入或选择东西，禁用状态可以告诉用户不可以输入或选择东西，还有就是表单控件验证状态，可以告诉用户的操作是否正确等。那么在Bootstrap框架中的表单控件也具备这些状态。
#### 焦点状态
焦点状态是通过伪类“:focus”来实现。Bootstrap框架中表单控件的焦点状态删除了outline的默认样式，重新添加阴影效果。
#### 禁用状态
Bootstrap框架的表单控件的禁用状态和普通的表单禁用状态实现方法是一样的，在相应的表单控件上添加属性“disabled”。
```html
<input class="form-control" type="text" placeholder="表单已禁用，不能输入" disabled>
```
在Bootstrap框架中，如果fieldset设置了disabled属性，整个域都将处于被禁用状态。  
对于整个禁用的域中，如果legend中有输入框的话，这个输入框是无法被禁用的。
```html
<form role="form">
<fieldset disabled>
<legend><input type="text" class="form-control" placeholder="显然我颜色变灰了，但是我没被禁用" /></legend>
    …
</fieldset>
</form>
```

#### 验证状态
在制作表单时，不免要做表单验证。同样也需要提供验证状态样式，在Bootstrap框架中同样提供这几种效果。
- .has-warning:警告状态（黄色）
- .has-error：错误状态（红色）
- .has-success：成功状态（绿色）
使用的时候只需要在form-group容器上对应添加状态类名。

很多时候，在表单验证的时候，不同的状态会提供不同的 icon，比如成功是一个对号（√），错误是一个叉号（×）等。在Bootstrap框中也提供了这样的效果。如果你想让表单在对应的状态下显示 icon 出来，只需要在对应的状态下添加类名“**has-feedback**”。请注意，**此类名要与“has-error”、“has-warning”和“has-success”在一起**

```html
<form role="form">
<div class="form-group has-success has-feedback">
  <label class="control-label" for="inputSuccess1">成功状态</label>
  <input type="text" class="form-control" id="inputSuccess1" placeholder="成功状态" >
  <span class="glyphiconglyphicon-ok form-control-feedback"></span>
</div>
<div class="form-group has-warning has-feedback">
  ......
</div>
<div class="form-group has-error has-feedback">
  ......
</div>
</form>
```

### 表单提示信息
使用了一个"help-block"样式，将提示信息以块状显示，并且显示在控件底部。
```html
<form role="form">
<div class="form-group has-success has-feedback">
  <label class="control-label" for="inputSuccess1">成功状态</label>
  <input type="text" class="form-control" id="inputSuccess1" placeholder="成功状态" >
  <span class="help-block">你输入的信息是正确的</span>
  <span class="glyphiconglyphicon-ok form-control-feedback"></span>
</div>
  …
</form>
```

### 按钮
#### 基本按钮
通过类名“btn”来实现。
```html
<button class="btn" type="button">我是一个基本按钮</button>
```

#### 默认按钮
Bootstrap框架首先通过基础类名“.btn”定义了一个基础的按钮风格，然后通过“.btn-default”定义了一个默认的按钮风格。默认按钮的风格就是在基础按钮的风格的基础上修改了按钮的背景颜色、边框颜色和文本颜色。
```html
<button class="btn btn-default" type="button">默认按钮</button>
```
#### 多标签支持

一般制作按钮除了使用< button>标签元素之外，还可以使用< input type="submit">和< a>标签等。同样，在Bootstrap框架中制作按钮时，除了刚才所说的这些标签元素之外，还可以使用在其他的标签元素上，唯一需要注意的是，要在制作按钮的标签元素上添加类名“btn”。如果不添加是不会有任何按钮效果。

#### 定制风格
在Bootstrap框架中不同的按钮风格都是通过不同的类名来实现，在使用过程中，开发者只需要选择不同的类名即可：
![image](http://img.mukewang.com/53b367d10001846a08020810.jpg)

#### 按钮大小   
在Bootstrap框架中提供了三个类名来控制按钮大小：
![image](http://img.mukewang.com/53b36a7600014af106910605.jpg)

#### 块状按钮
Bootstrap框架中提供了一个类名“btn-block”。按钮使用这个类名就可以让按钮充满整个容器，并且这个按钮不会有任何的padding和margin值。
```html
<button class="btnbtn-primary btn-lg btn-block" type="button">大型块状按钮</button>
```

#### 按钮状态
Bootstrap框架针对按钮的状态做了一些特殊处理。在Bootstrap框架中针对按钮的状态效果主要分为两种：活动状态和禁用状态。

Bootstrap按钮的活动状态主要包括按钮的悬浮状态(:hover)，点击状态(:active)和焦点状态（:focus）几种。

在Bootstrap框架中，要禁用按钮有两种实现方式：
1. 在标签中添加disabled属性
2. 在元素标签中添加类名“disabled”

区别：  
“.disabled”样式不会禁止按钮的默认行为，比如说提交和重置行为等。如果想要让这样的禁用按钮也能禁止按钮的默认行为，则需要通过JavaScript这样的语言来处理。对于< a>标签也存在类似问题，如果通过类名“.disable”来禁用按钮，其链接行为是无法禁止。而在元素标签中添加“disabled”属性的方法是可以禁止元素的默认行为的。

### 图像
图像在网页制作中也是常要用到的元素，在Bootstrap框架中对于图像的样式风格提供以下几种风格：
- img-responsive：响应式图片，主要针对于响应式设计
- img-rounded：圆角图片
- img-circle：圆形图片
- img-thumbnail：缩略图片

```html
<img  alt="140x140" src="http://placehold.it/140x140">
<img  class="img-rounded" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-circle" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-thumbnail" alt="140x140" src="http://placehold.it/140x140">
<img  class="img-responsive" alt="140x140" src="http://placehold.it/140x140">
```
**由于样式没有对图片做大小上的样式限制，所以在实际使用的时候，需要通过其他的方式来处理图片大小。比如说控制图片容器大小。（注意不可以通过css样式直接修改img图片的大小，这样操作就不响应了）**

```
<div class="col-sm-4">
    <img width="300px" class="img-circle" alt="" src="...">
    <div>圆形图片</div>
</div>
```

### 图标
在Bootstrap框架中有一个fonts的目录，这个目录中提供的字体文件就是用于制作icon的字体文件。
自定义完字体之后，需要对icon设置一个默认样式，在Bootstrap框架中是通过给元素添加“glyphicon”类名来实现，然后通过伪元素“:before”的“content”属性调取对应的icon编码。
```
<span class="glyphicon glyphicon-search"></span>
<span class="glyphicon glyphicon-asterisk"></span>
<span class="glyphicon glyphicon-plus"></span>
<span class="glyphicon glyphicon-cloud"></span>
```

## 网格系统
网格系统的实现原理非常简单，仅仅是通过定义容器大小，平分12份(也有平分成24份或32份，但12份是最常见的)，再调整内外边距，最后结合媒体查询，就制作出了强大的响应式网格系统。Bootstrap框架中的网格系统就是将容器平分成12份。

### 工作原理
- 数据行(.row)必须包含在容器（.container）中，以便为其赋予合适的对齐方式和内距(padding)。
- 在行(.row)中可以添加列(.column)，但列数之和不能超过平分的总列数，比如12。
- 具体内容应当放置在列容器（column）之内，而且只有列（column）才可以作为行容器(.row)的直接子元素
- 通过设置内距（padding）从而创建列与列之间的间距。然后通过为第一列和最后一列设置负值的外距（margin）来抵消内距(padding)的影响

![image](http://img.mukewang.com/53b0f9c000018b9305540282.jpg)

### 基本用法
```html
<div class="container">
  <div class="row">
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-8">.col-md-8</div>
  </div>
  <div class="row">
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-4">.col-md-4</div>
    <div class="col-md-4">.col-md-4</div>
  </div>
  <div class="row">
    <div class="col-md-3">.col-md-3</div>
    <div class="col-md-6">.col-md-6</div>
    <div class="col-md-3">.col-md-3</div>
 </div>
</div>
```

### 列偏移
有的时候，我们不希望相邻的两个列紧靠在一起，但又不想使用margin或者其他的技术手段来。这个时候就可以使用列偏移（offset）功能来实现。使用列偏移也非常简单，只需要在列元素上添加类名“col-md-offset-*”(其中星号代表要偏移的列组合数)，那么具有这个类名的列就会向右偏移。例如，你在列元素上添加“col-md-offset-4”，表示该列向右移动4个列的宽度。

### 列排序
列排序其实就是改变列的方向，就是改变左右浮动，并且设置浮动的距离。在Bootstrap框架的网格系统中是通过添加类名“col-md-push-*”和“col-md-pull-*” (其中星号代表移动的列组合数)。
```html
<div class="container">
  <div class="row">
    <div class="col-md-8 col-md-push-4">.col-md-4</div>
    <div class="col-md-4 col-md-pull-8">.col-md-8</div>
  </div>
</div>
```

### 列的嵌套
Bootstrap框架的网格系统还支持列的嵌套。你可以在一个列中添加一个或者多个行（row）容器，然后在这个行容器中插入列（像前面介绍的一样使用列）。但在列容器中的行容器（row），宽度为100%时，就是当前外部列的宽度。
```html
<div class="container">
    <div class="row">
        <div class="col-md-8">
        我的里面嵌套了一个网格
            <div class="row">
            <div class="col-md-6">col-md-6</div>
            <div class="col-md-6">col-md-6</div>
          </div>
        </div>
    <div class="col-md-4">col-md-4</div>
    </div>
    <div class="row">
        <div class="col-md-4">.col-md-4</div>
    <div class="col-md-8">
    我的里面嵌套了一个网格
        <div class="row">
          <div class="col-md-4">col-md-4</div>
          <div class="col-md-4">col-md-4</div>
          <div class="col-md-4">col-md-4</div>
        </div>
    </div>
    </div>
</div>
```
嵌套的列总数也需要遵循不超过12列。不然会造成末位列换行显示。


---

此页面为本人学习慕课网BootStrap基础的学习笔记，原地址为 https://www.imooc.com/learn/141