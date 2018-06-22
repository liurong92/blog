title: 编写可读的Javascript代码
date: 2016-11-09 19:00:58
tags:
---

----
本文摘取《编写可维护的Javascript》一书的总结以及自己在开发中所遇情况的综合总结，如果大家有时间，建议大家还是阅读以下《编写可维护的Javascript》，对于一个充满热情相当一个优秀的开发的程序员们还是挺有帮助的。

-----

作为大多的程序员来说，编写出可读的代码是多么重要的一件事情呀。尤其初入社会的小青年们，代码的可读性更是至关重要的事情了。我不知道其他公司是怎么要求各位程序员的代码，但至少在我司，代码的可读性还是挺重要，毕竟我们还是那么的喜欢重构代码，clear code处处可提呀。

为了让各位可以快速的学习，秒懂我在说什么，我将以代码的形式展示这些小小的规范。

>写出优美的代码，是每位程序员的重大任务。

### 美丽缩进
每一行的层级🈶4个空格符组成

```
好的写法
function sum(argument1, argument2) {
    return argument1 + argument2;
}

不好的写法
function sum(argument1, argument2) {
return argument1 + argument2;
}
```
不要小看这点点缩进，一点点小事就成就了大事了。可能有人说，要是不缩进也没有什么大问题，毕竟你给的例子，让我不那么的信服。那么我就在举一个。

```
如果代码是这样的
function cal(argument1, argument2, argument3) {
if(argument1 > argument2) {
if(argument1 < argument3){
return argument1 + argument3;
}
return argument1 + argument2;
}
if(argument1 < argument2) {
return argument2 + argument3;
}
retuen arguemnt1 + argument2 + argument3;
}
```
如果代码是这样的话，是不是觉得缩进就如此重要了，要是你再没有个ide或是什么格式化的工具，那你就惨了。你压根不知自己改的是哪一个闭合区域的代码。要是这个if嵌套了5个，那你就是惨到家了。我知道5个if是不可能的，毕竟嵌套两个if的话，已经是一件不好的事情了。但我还是想告诉大家，缩进是一个程序员敲代码的基础，好的缩进可以让我们清晰的分清每个闭合区间。
