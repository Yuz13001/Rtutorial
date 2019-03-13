## Chapter 1.3: Data Frame

讲过了最核心的Vector, 讲过了matrix，让我们来看看一个R语言使用者一定会天天见的数据格式：Data Frame



首先给一个定义，在R语言里，Data Frame 是Vecor 竖直拼接的结果。

在R当中，自带了几个data frame，其中一个使用的比较多的叫做iris，我们在console里输入一下：

```R
iris
```

Output会长成这个样子：

```R
> iris
    Sepal.Length Sepal.Width Petal.Length Petal.Width    Species 
1            5.1         3.5          1.4         0.2     setosa     
2            4.9         3.0          1.4         0.2     setosa     
3            4.7         3.2          1.3         0.2     setosa     
4            4.6         3.1          1.5         0.2     setosa     
5            5.0         3.6          1.4         0.2     setosa     
6            5.4         3.9          1.7         0.4     setosa     
7            4.6         3.4          1.4         0.3     setosa     
8            5.0         3.4          1.5         0.2     setosa     

```



这个就是R当中的Data frame 格式啦，其中每一列都是一个vector, 然后合并起来组成了这个叫做iris的dataframe。所以我们能够得到另外一个推论：**对于data frame而言，每一列都是一个vector，所以其中的数据都是同类型的。**



### Operations for a data frame, data frame的常规操作

对于data frame自然也有splicing的方法。之前的vector里，因为是一列数，所以只需要知道排第几个就好了。在data frame里，因为有行有列，所以就需要定义行number和列number(这里方法和matrix一样)。公式如下

```R
df[rownumber, colnumber]
```

比如我需要iris里第一行，第二列的那个数，那么就是

```R
iris[1, 2]
```

比如我需要第三行，第一列的那个数，那么就是

```R
iris[3， 1]
```

> 很多同学记不住先行还是先列，这里教大家一个小窍门：中文的”十“，写法是先横后竖，[]的数字也是一样，先行后列，要记清哈！
>

当然只选某一行或者某一列也是ok的

```R
iris[3， ]
iris[， 1]
```

甚至是很多行，很多列

```R
iris[c(1, 3)， ]
iris[， c(1, 3)]
```

或者和vec一样，-号代表不选择

```R
iris[, -1]
```

<u>细心的同学可以发现，这些操作和Matrix都是相似的。</u>除此之外，data frame还有一个独门秘籍：用column名字来select其中某一列。比如，如果想选中iris里的第一列，除了iris[, 1]之外，我们也可以利用这列的名字Sepal.Length​来做文章。

```R
iris$Sepal.Length
```

这个code的意思就是，选中iris中，Sepal.Length这一列。很多时候这样选择column会更加方便。聪明的同学也会想到了，既然每列都是vector，那么iris$Sepal.Length的output也就是vector。这也意味着，我们可以把vector的操作，应用在data frame的column上，比如：

```R
#找到Sepal.Length这一列的第三个
iris$Sepal.Length[3]
```



#### Question Time:

R中自带的mtcars是一个dataframe，请用两种方法，找到他第二行， 第一列的数字。









