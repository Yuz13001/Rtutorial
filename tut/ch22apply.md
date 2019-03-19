

## Chapter 2.2: 批量式计算

在上一章节中，我们讲解了对于vector的常见的操作，比如求平均数，中位数，或者数个数等等。在这一章节中，我们将讲解如何批量式来完成这一操作，这能极大的提升我们的操作效率。提到批量式计算，有过编程基础的朋友可能第一反应就是for loop或者while loop，但是在R语言里，因为R的速度相对较慢，loop在很多时候不是首选的选择，而且learning curve比较陡峭。我的R语言启蒙教授说过这样一句话，**在R里，90%的情况下，如果你要写for loop，你就错了。** **这里我们给大家着重推荐R语言中的apply()，简单上手，而且非常好用。**



------



#### apply类函数

在开始之前，让我们来回顾一下我们之前用的一个数据叫mtcars

```R
> mtcars
                     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
```

通过Ch1 我们知道，mtcars是data frame, 那么其中的每一列就是vector。现在如果让你求mtcars中每一列的平均数，你要怎么算呢？最直接的方法就是，利用data frame的splicing，一个一个去找。假设数据有5列，那么我就要写5次。

```R
mean(mtcars[,1])
mean(mtcars[,2])
mean(mtcars[,3])
mean(mtcars[,4])
mean(mtcars[,5])
```

对于小数据来说，这个还相对现实，那么对于大型数据来说，比如一个1000列的数据，显然不可能这样完成，这个就是apply函数大展身手的时候了。我们来先看使用方式：

```R
sapply(mtcars, mean)
```

sapply是function的名字，在括号中，第一个填入的是数据名字，第二个填入的是需要完成的操作的名字。而输出的结果，就是每一列的mean了，非常的方便快捷。

那么掌握了这个工具之后，我们来做一个小练习，请说出下面每一行code的意义：

```R
sapply(mtcars, median)
sapply(mtcars, max)
sapply(mtcars, min)
sapply(mtcars, IQR)
```



------



### 无敌Function: summary

我们之前讲过，summary这个function

> 这些function的名字相对都比较好记，只要多用几次，就能迅速掌握。如果大家对这些function感觉，太多不好记，这里教大家一个无敌function：summary()
>
> ```
> summary(height)
>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
>     150     160     170     170     180     190 
> ```
>
> 只要输入summary(height)，那么height的最小值，1st quartile，中位数，平均数，3rd Q和最大值就展现出来了。这样就能快速的了解一个数组的分布情况

其实summary不仅对vector有用，对于data frame也有奇效：

```R
> summary(iris)
  Sepal.Length    Sepal.Width     Petal.Length    Petal.Width          Species  
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100   setosa    :50  
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300   versicolor:50  
 Median :5.800   Median :3.000   Median :4.350   Median :1.300   virginica :50  
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199                  
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800                  
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500                 
```

