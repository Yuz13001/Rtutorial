## Chapter 1.2: Matrix

R语言中，最最核心的数据类型是刚刚提到的vector，其他大多数数据类型都是vector的变体。我们来看他的第一个变体，Matirx。

首先给一个定义，在R语言里，Matrix是Vector砍出来的结果。

比如我们来新建一个vec，其中填入1到9，再以此新建一个matrix试试

```R
vec <- 1:9
mat1 <- matrix(vec, ncol=3, nrow=3)
```

其中，matrix是用来新建matrix的function，vec是我们扔进去的vector，ncol和nrow分别定义了有多少行，有多少列。最终的Output会长成这个样子：

```R
> mat1
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9

```

可以非常明显的看出，mat1实际上就是vec被砍了两刀之后，一个一个填进去的结果。因为matrix是vector砍出来的，所以我们可以得到一个重要的推论：**既然vector中的element必须同类型，那么matrix中的element也必须同类型。**

### Operations for a matrix, matrix的常规操作

对于Matrix自然也有splicing的方法。之前的vector里，因为是一列数，所以只需要知道排第几个就好了。在Matrix里，因为有行有列，所以就需要定义行number和列number。公式如下

```R
mat1[rownumber, colnumber]
```

比如我需要第一行，第二列的那个数，那么就是

```R
mat1[1, 2]
```

比如我需要第三行，第一列的那个数，那么就是

```R
mat1[3， 1]
```

很多同学记不住先行还是先列，这里教大家一个小窍门：中文的”十“，写法是先横后竖，[]的数字也是一样，先行后列，要记清哈！

当然只选某一行或者某一列也是ok的

```R
mat1[3， ]
mat1[， 1]
```

甚至是很多行，很多列

```R
mat1[c(1, 3)， ]
mat1[， c(1, 3)]
```

或者和vec一样，-号代表不选择

```R
mat1[, -1]
```



对于初学者来说，matrix的使用频率并不算太高。但是他的特性，是一个很好的复习，承前启后，让我们来看看我们用的最多的一个数据格式：Data Frame。



