

## Chapter 2.3: R Package & Tidyverse

在上一章节中，我们讲解了对于vector的常见的批量式操作，比如求平均数，中位数，或者数个数等等。在这一章节中，我们将讲解更高级，也是实际操作中，非常常用的一套组合拳，tidyverse。他能够解决95%以上对于数据计算的需求



------



在这一小节里，我们先来以一个问题开始。

我们有iris这个数据, 我们知道iris里有150个兰花的数据，其中species有三种，setosa，versicolor和virginica各有50个，现在请问你每种Species的兰花，平均的Sepal.Width是多少？



```R
#展示数据前六行，function叫head
#Input
head(iris)

#Output
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
#Input
#（此处这个code暂时还没讲到，别慌，只是吓大家一下）
mean(iris$Sepal.Width[iris$Species=="setosa"])

#Output
[1] 3.428
```

> 首先我们需要选中iris$Sepal.Width, 也就是我们需要求平均数的column。
>
> 但是我们又不能计算所有150个width的平均数。根据要求，我们必须得选中符合条件的兰花，比如setosa，所以就需要用到[]这个function，事情一下子就变得复杂许多.



在上述的code里，一行code，可以求一个种类兰花的平均数。这里我们知道兰花有三种，所以最多写三行code就能搞定，但是如果数据中种类更多的话，可能几十行code都没有办法写完，那有没有什么自动的方法呢？ Tidyverse，这个大神写的补丁包，就能在这上面祝我们一臂之力。



R语言的一个非常大的优势就是它的补丁包。我们首先需要安装一下tidyverse，请大家在console中输入

```R
install.packages("tidyverse", dependencies = T)
```



install.packages是安装补丁包的function名字，tidyverse是补丁包的名字，dependencies = T的意思是如果tidyverse这个补丁包是基于其他补丁包的，那就一起把其他的补丁包安装了。这是一个相对比较保险的做法。



如果一切顺利的话，最后会看到这样一行字

```R
The downloaded binary packages are in
	/你电脑上什么奇怪的位置
```



看到这个，这就证明安装成功了。这也是安装绝大多数R语言补丁包的办法。



安装完Package之后，我们需要调用它，方法非常简单，只需要写library(package名字)就好

```R
#Input
library(tidyverse)

#Output
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



首先呢，在开始用tidyverse之前，我们需要学习使用一个小工具叫script。

在刚刚的几节内容中，我们做的都是在console中，输入command获取output的格式，也就是一行code一个结果。有些时候，一行code不够用，需要两行或者以上才行，这个时候console的弱点就展现出来了：对于多行code支持不够理想。

另外，console的结果和code都不会被保存下来。换而言之，你今天开开心心打的code，电脑一关机就都没了。Script就是应对这个情况最好的解决办法，script相当于一个储存着你code的文档，可以随时保存，方便调用。在R studio里，我们随时都可以新建一个script，在左上角有一个白纸和绿色加号的按钮：

​    ![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script1.png)



单击之后，我们就可以看到一个下拉菜单：

   ![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script2.png)



在下拉菜单中选择R script就可以了。在操作完成后，Rstudio的布局会稍有变化：

   ![image](https://github.com/Yuz13001/Rtutorial/blob/master/Pics/script3.png)

整个界面从原有的三分天下，变成了田字格。左上角的新方块，就是script的页面，这里我们需要记住两点：



1. 在script里我们打的code，可以被保存下来，方便以后使用。

2. 在script中输入的code，按control + enter就可以运行了！



------



现在万事俱备只欠东风了，让我们来在script里庄重的打上刚刚我们学到的一行code

```R
#Load library
library(tidyverse)
```



这行code的目的刚刚讲过，是为了导入补丁包。R每次关闭之后，补丁包也会随之关闭，所以在script的一开始，load library是一个非常好的习惯。

接下来我们来学习一下tidyverse中最重要的两个function，summarize和group_by。



先来看Summarize，让我们在script里输入

```R
#Input
iris %>%
  summarize(mean(Sepal.Width))

#你会得到这个结果
  mean(Sepal.Width)
          3.057333
```



让我们来看一下这个美丽的code：

1. iris是数据的名字，打在最前边

2. %>% 这个符号叫pipe，意思是把数据传递到后续的code中

3. summarize是一个function，自己没有实际意义，它做什么，取决于summarize括号中放什么function

4. mean(Sepal.Width) 用来计算sepal.width的平均数

   

聪明的你一定发现了，这个code这么复杂实际上就干了一件事儿，叫求iris里sepal.width的平均数。我们之前也讲过，这不就是mean(iris$Sepal.Length)吗？ 那让我们再看一个用法

```R
#Input
iris %>%
  summarize(avg.sepal.length = mean(Sepal.Width))

#你会得到这个结果
   avg.sepal.length
         3.057333
```



让我们来对比一下两个code，和两个输出的结果。我们发现实际上两者的差别在summarize的括号里，和output的上方。在summarize中，你可以指定输出的时候，展示的名字，这样output看起来会更好看一些。那让我们再来看一个用法：



```R
 #Input
 iris %>%
   summarize(mean(Sepal.Width), sd(Sepal.Width))
 
 #你会得到这个结果
   mean(Sepal.Width) sd(Sepal.Width)
          3.057333       0.4358663
```



如果在summarize中，放上两个function，那实际上summarize就会同时计算这两个function。到目前为止，我相信你肯定还没有被tidyverse折服，没关系，让我们来看看下一个function，叫group_by

```R
 #Input
 iris %>%
   group_by(Species)
```



group_by 当中可以调填入任何的categorical variable，他的作用是根据category，把数据分为小组。如果仅仅使用group_by，实际上没有什么作用，他就像团战里的辅助需要和别人连用才可以。让我们看看一个联用的例子。

```R
 #Input
 iris %>%
     group_by(Species) %>%
     summarize(mean(Sepal.Width))
     
 #你会得到这个结果
# A tibble: 3 x 2
  Species    `mean(Sepal.Width)`
  <fct>                    <dbl>
1 setosa                    3.43
2 versicolor                2.77
3 virginica                 2.97
```



在上述的code中，我们先放一个group by，让数据分为三个小组，然后summarize就可以求三个小组的平均数了。怎么样？是不是非常方便，不仅如此，summarize的”大坑“特性，也可以让这个code同时计算多组数，并且输出更美观，比如：

```R
#Input
iris %>%
  group_by(Species) %>%
  summarize(avg.sw = mean(Sepal.Width), sd.sw = sd(Sepal.Width), 
  max.sw = max(Sepal.Width))
  
#你会得到这个结果
# A tibble: 3 x 4
  Species    avg.sw sd.sw max.sw
  <fct>       <dbl> <dbl>  <dbl>
1 setosa       3.43 0.379    4.4
2 versicolor   2.77 0.314    3.4
3 virginica    2.97 0.322    3.8
```



怎么样，这下在这章一开始的问题，是不是就非常简单，迎刃而解了？