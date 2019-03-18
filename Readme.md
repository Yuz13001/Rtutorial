R语言新手教程
================
![](https://img.shields.io/badge/language-R-blue.svg)

![](https://img.shields.io/badge/license-MIT-000000.svg)

Lance Zhang, 2019/03/12



欢迎大家来到R的世界
-------------------

很多人都说21世纪是编程的世纪，掌握一门编程语言非常重要。作为一门立足于统计分析的语言, R语言是一个非常适合新手上手学习的编程工具。在这份教程中，我们会从零基础开始，手把手带你走进R语言的世界。



安装
----

一般情况下，使用R语言的时候，需要安装两个部分：Base R, 及Rstudio。前者是R语言的核心，后者能够更好地帮助我们来使用和管理R。

第一步需要先安装Base R。在R的官网上，找到离你最近的服务器，<https://cran.r-project.org/mirrors.html> 根据你的操作系统，下载安装R的package即可。命名方式一般为R-3.5.2.pkg (macOS) 或者 R 3.5.2.exe (Windows)

第二步，需要移步到Rstudio官网，<https://www.rstudio.com/products/rstudio/download/#download> 同样还是根据你的操作系统，下载安装即可。

需要注意的是，现在的R语言版本不支持一些比较老的操作系统，如OS X Yosemite。操作系统比较老的小伙伴们，需要更新到相对比较新的操作系统。



## 初识R语言

让我们来打开Rstuido，如果安装无误，应该长成这个样子：

![Rstudio](https://raw.githubusercontent.com/Yuz13001/Rtutorial/master/Pics/Rstudio.png)

如上展示的的Rstudio分为三个区块，左边是Console，大家可以把它理解为计算器，输入一个公式给出一个结果。右上角是Environment，简单来说就是R现在记住了什么数据。右下角是一个多功能区，可以展示图像，和安装的“补丁包”。同学们不妨在Console中输入

```R
1+1
```

并按下Enter（Return/ 回车）键，（如果太阳没有从西边出来），你应该会得到：

```
[1] 2
```

如果小伙伴们能得到这个答案，也就证明R语言的安装成功了 :)

现在就让我们从R语言中的数据格式开始，踏上R语言的学习征程吧。



- [Chapter 1: 数据结构](https://github.com/Yuz13001/Rtutorial/blob/master/tut/ch1structure.md)

- [Chapter 2: 基本操作](https://github.com/Yuz13001/Rtutorial/blob/master/tut/ch2structure.md)