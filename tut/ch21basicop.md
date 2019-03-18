

## Chapter 2.1: 对于Vector的基础运算

R的大部分运算都是base on vector的，在本节内容中，我们将讲解对于vector来说，最基础也是最常用的几种运算。



#### 判断Vector类型

对于初学者来说，判断vector中element的类型是非常重要的，我们这里笼统的把vector分为两类，数字和文字。比如我们新建两个vector, weight和name

```R
weight <- 100:110
name <- c("lancy", "cylan", "dylan")
```

根据我们Chapter 1的内容，我们知道weight是一个数字类型的vector，name是一个文字类型的vector（因为element带引号）。那如果给你一个现成的vector，我们怎么来判断类型呢？这个时候就需要str()这个function

```R
str(weight)

 int [1:11] 100 101 102 103 104 105 106 107 108 109 ...

str(name)

 chr [1:3] "lancy" "cylan" "dylan"
```

我们重点看每次str output中的前三个字母 （这里的int和chr）。让我们来记住一个宇宙真理：

**<u>如果str告诉我们，这个vector是int，dbl，num的话，那么这个vector就属于数字类型，可以互相加减乘除。如果显示的是chr，fct，ord的话，那么这个vector就属于文字类型，不能加减乘除。</u>**



#### 对于数字类型的Vector

在开始之前，让我们来新建一个叫做height的vector，其中填入从150到190的自然数。

```R
height <- 150:190
```

对于数字类型的vector，如果要用一个数字来形容他，首先大家会想到的就是平均数，在R里是这样来计算的

```R
mean(height)

[1] 170
```

输出的结果也就是170。不仅如此，对于中位数，IQR这类summary stats，R也都有对应的function

```R
#计算中位数，IQR, standard deviation，variance，值域，最小值，最大值

median(height)
[1] 170

IQR(height)
[1] 20

sd(height)
[1] 11.97915

var(height)
[1] 143.5

range(height)
[1] 150 190

min(height)
[1] 150

max(height)
[1] 190
```

这些function的名字相对都比较好记，只要多用几次，就能迅速掌握。如果大家对这些function感觉，太多不好记，这里教大家一个无敌function：summary()

```R
summary(height)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    150     160     170     170     180     190 
```

只要输入summary(height)，那么height的最小值，1st quartile，中位数，平均数，3rd Q和最大值就展现出来了。这样就能快速的了解一个数组的分布情况。

学习完上一章之后，我们知道了一个重要的概念，**dataframe中每一列都是一个vector，所以所有对于vector的操作，data frame中的某一列也都可以完成。比如：**

```R
mean(iris$Sepal.Length)
[1] 5.843333

summary(iris$Sepal.Length)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  4.300   5.100   5.800   5.843   6.400   7.900
```

这样我们就能快速了解iris数据中，这些兰花的sepal.length的分布了



### 对于“文字”类型的Vector

对于数字类型的vector，求平均数合情合理。但是对于文字类型的vector，我们怎么下手呢？一般情况下，如果文字类型的vector中，element代表类别的话，我们可以做数数的处理。比如性别是一个vector，长度为100。我们就可以数一下，其中有多少位女同学，多少位男同学，多少位transgender同学等等等等。这里我们以iris中的Species来举例：

```R
iris$Species
```

Species长度为150，其中包含了150株兰花的种类，我们可以用table这个function来完成数数的工作：

```R
table(iris$Species)

    setosa versicolor  virginica 
        50         50         50 
```

这个output的意思就是说，setosa这种兰花有50个，versicolor有50个，virginica也有50个。



