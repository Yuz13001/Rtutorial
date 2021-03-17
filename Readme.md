R语言新手教程
================
![](https://img.shields.io/badge/language-R-blue.svg)  ![](https://img.shields.io/badge/license-CC--BY--NC--SA-green.svg)




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



## Chapter 0: Before we start

首先在任何计算机语言中，最基础的都是赋值。比如玛丽苏的主角们，可能有个很长的名字，像"七彩琉璃五色小马长发飘飘玛丽苏"，"英俊潇洒风流倜傥点秋香的唐伯虎"，对于这样的内容，我们没法每次都一一输入，所以需要把他们存到一个空间中方便以后调用，这个操作就叫做赋值。

我们来在console中输入这个code，并按下enter/ return (Win/ MacOS)。

```R
marysue <- "qicailiuliwusexiaomachangfapiaopiaomalisu"
```

这个code完成的实际上就是赋值的操作。

其中：

- marysue是变量名
- <-是赋值符号
- "qicailiuliwusexiaomachangfapiaopiaomalisu"是存进去的内容

当我们以后再试图打marysue的时候，就会出现玛丽苏的身影，比如：

(在console中打入marysue，并按enter/ return)

```R
marysue
[1] "qicailiuliwusexiaomachangfapiaopiaomalisu"
```

这就是一个成功的赋值操作，看似简单但是这里我们需要注意三点。

1. 注意赋值符号的方向，**R语言的优美从这里开始，<-，代表了把右边的东西存到左边。**
2. <- 符号的前后注意加空格，使得R语言coding变得更加美观
3. " "中包裹着的，我们初学者可以把它认同为是文字类型的数据，这个在R语言中，是一条"宇宙真理"



**能掌握这些，就说明你的实力足以应对R语言。**现在就让我们从R语言中的数据格式开始，踏上R语言的学习征程吧。

- [Chapter 1: 数据结构](https://github.com/Yuz13001/Rtutorial/blob/master/tut/ch1structure.md)
- [Chapter 2: 基本操作](https://github.com/Yuz13001/Rtutorial/blob/master/tut/ch2structure.md)
- Chapter 3: 数据分析 - 画图



(目前进度一天更新一小节，希望可以不🕊)

------

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/80x15.png" /></a>

本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">知识共享署名-非商业性使用-禁止演绎 4.0 国际许可协议</a>进行许可。
