title: jenv让java管理如此简单
date: 2016-03-11 10:17:26
tags: jenv, java
---

对于一个标准的程序员来说，“懒惰”是我们固有的特性，也是我们无法避免的事情，对于我来说，依然如此。我不得不说，我是“懒”到了一种境界，当我得知自己下一个项目要使用`java`的时候，我就决定先自己做个小demo练习一下这个java技能，就在我准备搭建的时候，突然一个严重的问题摆在了我的面前--__我使用的是java7 但是，下一个项目要使用java8__

最简单，而且直接的方式就是，直接装一个java8，就好了。但是，这一定不是我们程序员的做法了，我们当然希望，直接的系统拥有多种java 版本，这样以便于达到版本控制。为此，我google一下，终于发现了一种“高端”的东西，这就是[jenv](https://github.com/gcuisinier/jenv)

---

>jenv is for a equivalent of rbenv, but for Java environment. It allow to easily switch between several JDKs installations (already presents), and configure which one to use per project.

这是官方给出的说法，一看你就知道，这东西和管理ruby的版本控制器一样，但是这货，只是管理Java环境的，也好，总比没有的好吧。。

看看下一段说明，就更加清楚了。。

>jEnv is a command line tool to help you forget how to set the JAVA_HOME environment variable

毫无疑问，它就是干这个作用的，管理环境。

于是，我就按着官方的步骤开始，安装，配置。。

## 安装jenv
### 方法一

直接克隆

```
git clone https://github.com/gcuisinier/jenv.git ~/.jenv
```

### 方法二

使用[homebrew](http://brew.sh/)安装,我喜欢这个方法，简洁方便、还好用。。

```
brew install jenv
```

## 配置jenv环境变量

如果你使用的是bash的话，请这样配置。

```
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(jenv init -)"' >> ~/.bash_profile
```

如何你使用的是zsh的话，请这样配比。

```
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(jenv init -)"' >> ~/.zshrc
```

### 安装java

这一步真是**坑爹的不行，不行的**。

一定要主要，这个东西是管理java环境的，是java环境的， 是java环境的，因此要先安装你所需要的java版本，把所有需用到版本，先安装了，在来配置环境。*这个安装java我就不在这里说了，去官网上，现在所需要的版本，然后安装即可了。*

当你安装完所需的版本后，你会发现在你的`/Library/Java/JavaVirtualMachines/`目录下，会对应出现你所安装的版本。此时，你只需要在运行，一下命令，来让你的`jenv`管理你的java环境。

```
jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home/
```

**<font color=red>注意</font>** 你只要配置你所有的java版本的home即可。

当添加完成后，运行`jenv versions`即可看见你所安装了的java版本，这样就使用jenv管理器java了。

```
$ jenv versions
  system
  1.7
  1.7.0.79
  1.8
* 1.8.0.73 (set by /Users/rongliu/.jenv/version)
  oracle64-1.7.0.79
  oracle64-1.8.0.73
```

## 设置

global

```
jenv global 1.8.0.73
```

local

```
jenv local 1.7.0.79
```

使用该命令后，会在你的项目下生产一个`.java-version`的文件。

到这里就结束了，哈哈哈，剩下的命令，你可以使用`jenv -h`来帮助。

我们可以“懒惰”，但一定要懒惰的有理由，一定要知道其原理。。
