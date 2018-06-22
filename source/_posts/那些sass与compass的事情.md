title: 那些sass与compass的事情
date: 2015-11-29 00:31:41
tags: sass compass
---

对于一个刚接触有两个月的前端“嫩肉”来说，还是有点收获的，就单单最近我所做的项目上，就有很多让人不懂的东西，真的是“不做前端，不懂前端的苦呀。”简直就是“博大精深”呀。刚开始本屌以为就是改改样式什么鬼的，其不然，里面发生的事情还是多的让人难以想象的。

本屌，今天就在这里简单的介绍一下前段`sass`和`compass`所使用的注意事项了，感觉也不是什么注意事项，严格来说就是一部分的简介，加少许的实用吧。在这片文章中，本屌会主要对sass的使用进行说明，而这个compass我不会有太多的说明和讲解，会有简单的安装和基本的使用。

---
>“没有锤子，钉子就没有什么用，没有钉子，锤子存在就空虚了。”

对于Sass和Compass来说，它们的关系就是这样的，Sass就相当于是钉子，而这个Compass就相当于锤子。它们两个就是相辅相成的，感觉谁也离不开谁一样。

# Sass
这个[Sass](http://sass-lang.com/)是快速编写CSS样式的~~编程~~语言（原理和java类似，需用变异后方可引用的html文件中），在官网上被评价为是世界上最为好用的css书写语言，真心不想吐槽，世界上有这样绝对的事情吗，简直不像说什么，它到时支持一些`参数的定义`，`变量的引用`，`支持嵌套`等方式书写css，因此，总体来说还是可以的。

---

当你打开官方的网站的时候，你会发现它的页面是如此的~~酷炫~~，真心觉得像是‘小女生’的感觉，各种粉红色，对于我这个屌丝级别的人物来说还是有那么一点不好意思细看的，不知道的还以为进入了什么不该进入的网站，简直是会被**羞红脸**的网站呀。

官方给出了这样一句定义，我就原封不动的贴过来给你们看看吧，看看说的是有多霸气的。

>Sass is the most mature, stable, and powerful professional grade CSS extension language in the world.

是不是觉得很**叼**的样子。哈哈，我们就看看即可，不要太过于纠结这个了，可能人家真的很好用呀。所有我们就不在这个过多的评价人家了。

## 工作流程

来我们看看它的工作流程吧，就是这样的

![工作流程](/images/sass_work.png)

css学习地址【[点解我](http://www.w3schools.com/css/default.asp)】

* 编写以.sass或.scss为后缀的文件，那么有人问我这个文件里面怎么写了，你就按照css的写法写就好了（如何你不知道怎么写的话），要是还有人问我压根就不会写css，那我建议你还是先学一下css吧。

* 使用Sass的编译器，编译成.css的文件。

* 将编译后的.css文件引用到html文件中即可。

---
看到这里，大家一定有疑问，为什么这个`鬼东西`会有两种后缀呀，这就是人家为什么会流行的原因了，人家可是有两种方案的人哦，所以我们还是乖乖的学习人家的东西吧。

首先来说一下这个`.scss`是3.0以后的版本推出的，在3.0以前都是使用`.sass`为后缀的，当然Sass到现在是支持这两种的后缀的。

其次来说一下，这个`.sass`于`.scss`的区别。

sass 是基于ruby开发的，因此，是一种类`ruby`和`python`的语言，而这个`.sass`跟像`python`原因那个的书写格式，拥有严格的缩进需求，对于有严重强迫症的人来说，感觉这个应该是比较合适的。而`.scss`是拥有花括弧结尾的书写格式，本屌觉得，这个种东西还是应个人需求选择，如何项目是ruby或者其他语言的话，建议还是使用`.scss`格式，如果项目是以python的话，统一期间，可以使用`.sass`格式。（不过我想说，本屌所做的项目就是使用python的，但是我们还是使用了`.scss`格式，所以这个东西，都是应人而异的，不用过于纠结，你喜欢什么样式，就用什么样式的好即可。）

## Sass安装
在对Sass进行简单说明之后，我不得不说来说说这个东西的安装了。

1、由于Sass是基于`ruby`语言编制而成，因此，我们首先要保证自己的电脑里安装的有`ruby`，不管是几点几的版本都可以，只要你有即可，要是没有，你也不用担心，[点击这里](https://www.ruby-lang.org/en/)，里面有教你如何安装`ruby`的。（对于`ruby`的安装，我给大家推荐两个安装的方式，

一个是：

```
brew install ruby
```
另一个是：

```
rbenv install 2.2.0
```
这两种都可以安装`ruby`的，不过我个人比较推荐使用第二种，因为它是ruby的版本管理工具。

2、当安装完成`ruby`后，就可以使用以下命令安装sass了

```
gem install sass
```

是不是安装特别简单呀，简直就是简单到不想说什么了。

---

关于编译的方式是这样的，命令行中输入以下命令即可：


```
sass [要编译的.sass/.scss文件] [输出的.css文件]
```


也可以使用以下命令进行编译，这个就是即时监听，只要改变就变异一次。命令如下：

```
sass --watch [编译的.sass/.scss文件]:[输出的.css文件] 
```


**注意**一定要注意中间的`冒号`。

当我们想讲写好的`.sass`文件转换成`.scss`文件的话，只需用使用以下命令，即可转变。

```
sass-convert xxx.sass xxx.scss
```

---

#### 关于.sass / .scss / .css转化

书写一个`.sass`文件

```
body
  color: blue
  font-size: 14px
  h4
    font-size: 25px
```



编译为`.scss`文件

```html
body {
  color: blue;
  font-size: 14px;

  h4 {
    font-size: 25px;
  }
}
```




编译成`.css`文件

```
body {
  color: blue;
  font-size: 14px; }
  body h4 {
    font-size: 25px; }
```

**注**：

在编译的时候，会产生一个以`.map`结尾的文件，该文件是sass编译后产生的，将`.css`与`.sass/.scss`进行关联的信息。

---
### Compass

官方给出了这样的解释：

>Compass is an open-source CSS Authoring Framework.

它就是一个开源的css编写框架。

是不是感觉很简答，它就是一个框架。~~悄悄的在这里说一句，由于它在使用的时候编译速度并不是怎么快，而且我们自己也可以配置，所以，建议不要太多使用它。感觉应该会被“to stamp out”~~

[点击我](http://compass-style.org/)查看compass，我就不在这里详细介绍了。

#### Compass安装

由于它还是用ruby开发的，因此，还是使用`gem`进行安装，执行下面代码：

```
gem install compass
```


生成一个新的项目，执行下面代码：


```
compass create xxxx
```

*<font color=red>在这里，我要着重说明一下，当creatr后，一定要看看这个命令行中的提示文字，是有一定帮助作用的。千万不要忘记了</font>*

---

**刚刚插入一个小插曲，我们还是回来继续我们的`Sass`学习**

### Sass的约定

当我们想按照每个功能进行样式的编写的话，都会给每个功能建立一个文件；或者是，当我们有很多相同变量存在的话，我们会专门抽取一个文件来存贮这些变量。当这些文件都建立好后，我们将其应用到一个固定的文件中，所有，我要在这里说说，我们要如何引用这些文件，如何创建这些文件名字，这个`sass`又是如何定义的。

* 文件名是已*下划线*开始，例如：`_test.scss`
* 在引入文件中，使用`@import`进行引入的。例如：`@import "test"`.

---

这里就会用人问，为毛这个可以不加后缀，要是加了的话，会是什么情况。

* 首先加后缀是可以的，不过对于一个程序员来说，愿意少打点就少打点，所以很正常。
* 其次，由于sass会自行加上`.sass`或`.scss`的后缀，然后进行查找，因此不用加，但是注意一点的是<font color=#334B62>不可以有文件重名的，不如这个就会产生，找不到什么鬼的。</font>

---

这时，一定有人问，“我可是记得，原生的`css`中，也是拥有`@import`的功能的，那我如何才能引用到原生的哪？”

其实特别简单，只要记住以下几点即可：
* 引用`.css`的文件，就是使用原生的了。
* 后跟部分属性。
* 引用以及`http://`开头的文件。如：http://www.sass.hk/css/css.css。
* 名字是`css`的url()值。

来给大脚一个例子，这样，就知道我说的这是什么鬼东西了。。

```
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
```

<font color="red">这样大家就懂了，不过还是要注意哦，一定要注意，要是想引用原生的`@import`的话，一定要这样写。</font>

#### 注释
这一部分还是忙重要的，几个以前有这样的说法，“好的编程，是要拥有详细的注释的。”可是，等我上班了，又是这样说的“好的代码是不需用注释就可以读懂的。”···正是因为这样的两种说法，搞得我现在，也不是知道要遵循哪一条了，后来，就自生了一派，可以让别人快速懂得，就不许用注释，有部分问题就拥有注释。可是时间一长，反而会觉得，不加注释好看多了，至少干净。因此现在就没有写过注释，不过这些都是根据自己的需求来设定了，所以大家就不要就绝太多了，自己看着办哦，因此在这里说一下注释的问题。···

它提供两种注释方式，

* 一种为：`//xxxxx`

* 一种为：`/* xxxxxx */`

第一种在编译后是部分生成的，第二种在编译后是会生成的。

例：

```
/* This comment is test */
body { color: black; }
// These comments are only one line long each.
a { color: green; }
```

生成代码：

```
/* This comment is test */
body {
  color: black; }
a {
  color: green; }
```

### Sass部分语法

#### 变量声明

```
$width: 20px
body {
	width: $width;
}
```

编译后结果：

```
body{
	width: 20px;
}
```

#### 代码块声明

可以去除重复的代码，保证‘clear code’，这个一定要重要，不要写重复的代码。

```
$mixin font {
	font-size: 20px;
	font-weight: 600;
}
body {
	font-size: 15px;
	p {
		@include font;
	}
}
```

编译后结果：

```
body {
	font-size: 15px;
	p {
		font-size: 20px;
		font-weight: 600;
	}
}
```

**其实这个`@mixin`的功能不只是那么简单的，还有很多~~不为人知~~的事情。希望大家下来慢慢查找哦。**

<font color=red>注意：</font>这个还可进行参数的传达，大家可以看看文档。

一定要看api, <font size=4>一定要看api</font>, <font size=5>一定要看api.</font>(重要的事情说三遍哦)
[点击我查看api](http://sass-lang.com/documentation/file.SASS_REFERENCE.html) 
#### 运算

它可以做简单的运算，简直就是好玩的极致了。

```
p {
  font: 10px/8px;
  $width: 1000px;
  width: $width/2;
  width: round(1.5)/2;
  height: (500px/2);
  margin-left: 5px + 8px/2px;
  font: (italic bold 10px/8px);
}
```

编译后：

```
p {
  font: 10px/8px;
  width: 500px;
  height: 250px;
  margin-left: 9px; 
}
```
<font color=red>注意：</font>也是拥有颜色变量的加减哦。
```
p {color: #010203 * 2;}
编译后：
p {color: #020406; }
```

**使用变量**

```
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```
编译后：
```
p {
  font: 12px/30px; 
}
```

**#{}使用**

```
$name: foo;
$attr: border;
p.#{$name} {
  #{$attr}-color: blue;
}
```
编译后：
```
p.foo {
  border-color: blue; }
```

---

<font size=4>关于变量的那点事情：</font>

变量操作，分为两种

* 直接操作变量，即变量表达式。

* 通过函数操作
	* 跟代码块无关的，多为内置函数，称function
	* 可复用的代码快，称mixin（用`@include`和`@extend`引用。）
	
**关于这个function的声明：**

```
@mixin name(params) {}
这个在前面说过了，再说一遍显示一下它的重要性。
```

---
#### @media使用

```
.sidebar {
  width: 300px;
  @media screen and (orientation: landscape) {
    width: 500px;
  }
}
```

编译后：

```
.sidebar {
  width: 300px; }
  @media screen and (orientation: landscape) {
    .sidebar {
      width: 500px; } }
```

### 后言

简直就是醉了，写个这个也是快谢了一个星期才弄好，前前后后准备了好多，不好大家也不要见怪哦，毕竟人家也是用心去做的嘛。我会加油好好写好美丽，易懂的文章。

我亲爱的buddy说，比较一下这个[stylus](http://learnboost.github.io/stylus/) 和 [less](http://lesscss.org/) 和 [sass](http://sass-lang.com/)之间的区别，我也不多说了，大家可以自己查查吧.

不过我要在这里说明一下，这个`stylus`和`less`都是基于javaScript，而`sass`是基于ruby的，个人觉得，要是没有在编译速度上`stylus`和`less`要快于`sass`。

大家根据自己的选择选取，反正就是，学会一门，其他都通，毕竟都是为了写好`css`而存在的。







