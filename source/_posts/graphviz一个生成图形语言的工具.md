title: graphviz一个生成图形语言的工具
date: 2015-11-16 00:06:40
tags:
---
'graphviz'一个可以快速生成图片的“高级”工具。

不得不说，看见个这个鬼东西的时候，是从大师的博客中看见的。怪不得大家都评论大师的文章，十分有深度，十分有内涵。现在我不得不承认了。棒棒的。看看这么一个工具，大师都要说的这么清楚，都要个大家介绍一下，感觉认识大师就是人生的最大的幸运了。

---

##### 我还是先说说这个东西有什么作用
###### 一个“高端”的画图工具


1、对于程序员来说，它可以简单、快速的生成一个的图片。

2、对于程序员来说，只需要简单的写几行代码，设置一点颜色，高清你所要表示的逻辑即可。

3、它所支持的导出格式还是蛮多的（常用图片格式、svg、png等）


官方给出了这个样一句话：
>Graphviz has many useful features for concrete diagrams, such as options for colors, fonts, tabular node layouts, line styles, hyperlinks, and custom shapes.

这就是它所“存在”的意义了吧。

##### graphviz中的布局器

1.dot 默认布局方式，主要用于有向图

2.neato 基于spring-model(又称force-based)算法

3.twopi 径向布局

4.circo 圆环布局

5.fdp 用于无向图

##### 安装
如果你的电脑有安装`brew`的话，你可以直接使用`brew install graphviz`进行安装，如果没有的话，你也并不需要担心，因为我们有用~~高端~~、~~大气~~、~~上档次~~网络，只需要简单的搜索，即可找到安装方法，难道还要我给你副附上网址吗？

好吧，看在我这么~~帅气~~老实的份上，给你们网址吧。直接可以下载的。

<http://www.graphviz.org/>  [点我哦](http://www.graphviz.org/)

##### 操作
你只需要拥有一个简单的文本编辑器即可，来~~哥哥~~推荐几个不错的

首先一个是`atom`是我喜欢而且第一个接触的文本编辑器~~仅仅是针对于`linux`系统和`mac`电脑而言哦~~。其次就是`subline text`了，这个我也没有用过。

好了，其实，我个人觉得，只要能编写语言，存东西的文本都可以使用。都是挺不错。

~~毕竟我也刚刚起步，说不定某一天就用上高大上的编译器了。~~

最后就是要告诉你们的是，这个文件存储成什么样子的后缀我还是没有研究透彻的。

```
特在此处留一块空地，为解决上面的问题。麻烦大家不要太建议了。哈哈
```

后期我会更新之一不得的。

`注意`：转出方式，

`dot [需转出文件名] –T [转出文件格式] –o [转出文件名]`

例：
`dot example1.dot –T png –o example1.png`

##### 制作实力

**1、有向图**

```
digraph test_one {
  a -> b;
  b -> c;
  c -> a;
}
```
生成图片

![有向图](/images/test_one.png)


**1、有向图**

```
digraph test_one {
  a -> b;
  b -> c;
  c -> a;
}
```
生成图片

![有向图](/images/test_one.png)


**2、无向图**

其实这个无向图也是很简单的，只需用将箭头去掉就好了。。

```
graph test_two {
  a -- b;
  b -- c;
  c -- d;
}
```
生成图片

![有向图](/images/test_two.png)

**在此声明一个事情，注意代码中声明变量前缀，本吊，在编译的时候才发现有这个区别的。**


**3、拥有特殊样式的图片**

```
digraph test_three {
  a -> b;
  b -> c;
  c -> a;

  a [shape=box, label="我是a", fillcolor="#7DAE77", style=filled]
  b [shape=triangle, label="我是b", fillcolor="#00A9E8", style=filled]
  c [shape=circle, label="我是c", fillcolor="#ABF0E6",style=filled]
}
```

这个大家都应该能看懂吧，就不在这里一一介绍了。

生成图片

![有向图](/images/test_three.png)

**4、拥有子图的**

```
graph test_four{
 "hmc01" -- "test520"
    "test520" -- "lpar2"
    "test520" -- "lpar3"
 "hmc01" -- "test570"
    "test570" -- "aixtest01"
    "test570" -- "aixtest02"
    "test570" -- "aixtest03"
 "hmc01" -- "test510"
    "test510" -- "lpar1"
}
```

这个大家都应该能看懂吧，就不在这里一一介绍了。
后面还有很多画图的方式，可以慢慢的学习，各位可以通过官网学习。

生成图片

![有向图](/images/test_four.png)



