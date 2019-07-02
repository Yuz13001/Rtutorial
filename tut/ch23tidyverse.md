

## Chapter 2.3: R Package & Tidyverse

在上一章节中，我们讲解了对于vector的常见的批量式操作，比如求平均数，中位数，或者数个数等等。在这一章节中，我们将讲解更高级，也是实际操作中，非常常用的一套组合拳，tidyverse。他能够解决95%以上对于数据计算的需求



------



在这一小节里，我们先来以一个问题开始。我们有iris这个数据, 我们知道iris里有150个兰花的数据，其中species有三种，setosa，versicolor和virginica各有50个，现在请问你每种Species的兰花，平均的Sepal.Width是多少？

```R
> head(iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

这个其实是数据分析中非常常见的一个请求，如果说用最最基本的R语言function，实际上也能够完成，只是方法比较复杂：

```R
> mean(iris$Sepal.Width[iris$Species=="setosa"])
[1] 3.428
```

首先我们需要选中iris$Sepal.Width, 也就是我们需要求平均数的column。但是我们又不能用所有150个width, 必须得选中符合条件的比如，setosa这类的兰花，所以就需要用到[]这个function，事情一下子就变得复杂许多（此处这个code暂时还没讲到，别慌，只是吓大家一下）。这里我们知道兰花有三种，所以最多写三行code就能搞定，但是如果数据中种类更多的话，可能几十行code都没有办法写完，那有没有什么自动的方法呢？ Tidyverse，这个大神写的补丁包，就能在这上面祝我们一臂之力。

R语言的一个非常大的优势就是它的补丁包。我们首先需要安装一下tidyverse，请大家在console中输入

```
install.packages("tidyverse", dependencies = T)
```

install.packages是安装补丁包的function名字，tidyverse是补丁包的名字，dependencies = T的意思是如果tidyverse这个补丁包是基于其他补丁包的，那就一起把其他的补丁包安装了。这是一个相对比较保险的做法。

如果一切顺利的话，最后会看到这样一行字

```
he downloaded binary packages are in
	/你电脑上什么奇怪的位置
```

这就证明安装成功了。这也是安装绝大多数R语言补丁包的办法。

安装完Package之后，我们需要调用它，方法非常简单，只需要写library(package名字)就好

```
> library(tidyverse)
── Attaching packages ───────────────────────── tidyverse 1.2.1 ──
✔ ggplot2 3.2.0     ✔ purrr   0.3.2
✔ tibble  2.1.3     ✔ dplyr   0.8.1
✔ tidyr   0.8.3     ✔ stringr 1.4.0
✔ readr   1.3.1     ✔ forcats 0.4.0
── Conflicts ────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
```

如果安装成功的话，应该会看到上述一些output，这些output对初学者来说不太重要，我们先暂时略过。直入主题，“论如何像兰斯一样优雅的使用tidyverse"



------



首先呢，在开始用tidyverse之前，我们需要学习使用一个小工具叫script。在刚刚的几节内容中，实际上我们做的都是在console中，输入command获取output的格式，也就是一行code一个结果。有些时候，一行code不够用，需要两行或者以上才行，这个时候console的弱点就展现出来了。另外，console的结果和code都不会被保存下来。换而言之，你今天开开心心打的code，电脑一关机就都没了。Script就是应对这个情况最好的解决办法，script相当于一个储存着你code的文档，可以随时保存，方便调用。在R studio里，我们随时都可以新建一个script，在左上角有一个白纸和绿色加号的按钮：

![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script1.png)

单击之后，我们就可以看到一个下拉菜单：

![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script2.png)

在下拉菜单中选择R script就可以了。在操作完成后，Rstudio的布局会稍有变化：

![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script3.png)

从原有的三分天下，变成了田字格。左上角的新方块，就是script的页面了，在script里我们打的code，就可以被保存下来，方便以后使用了。在script中输入的code，按control + enter就可以运行了！

