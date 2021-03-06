在Python中，如果我们想修改列表中所有元素的值，可以使用 for 循环语句来实现。

例如，将一个列表中的每个元素都替换为它的平方：

    L = [ 1 , 2 , 3 , 4 , 5 ]
    for i in range(len(L)):
        L[i] = L[i] ** 2 
    L
    [ 1 , 4 , 9 , 16 , 25 ]
另一种优雅的实现方式就是使用列表推导式（List Comprehensions):

    L = [ 1 , 2 , 3 , 4 , 5 ]
    L = [x ** 2 for x in L]
    L
    [ 1 , 4 , 9 , 16 , 25 ]
2. 基本语法

我们具体来分析上面给出的例子

    L = [x ** 2  for x in L]

我们将列表推导式写在一个方括号内，因为它最终构建的是一个列表。

列表推导式主要由两部分构成：
循环变量表达式（ x ** 2 ）
for 循环头部（ for x in L ）

3. 工作原理

>Python在执行列表推导式时，会对可迭代对象 L 进行迭代，将每一次迭代的值赋给循环变量 x ，然后收集变量表达式 x ** 2 的计算结果，最终由这些结果构成了新的列表，也就是列表推导式所返回的值。

>只要支持 for 循环进行迭代的对象，都可以对它使用列表推导式。

例如，我们将一个字符串进行移位处理：

    S = 'abcde' 
    S = '' .join([chr(ord(c)+ 1 ) for c in S])
    S
    'bcdef'

4. 高级语法

>除了像上面介绍的 [x ** 2 for x in L] 这种基本语法之外，列表推导式还有一些高级的扩展。

4.1. 带有if语句

>我们可以在 for 语句后面跟上一个 if 判断语句，用于过滤掉那些不满足条件的结果项。

例如，我想去除列表中所有的偶数项，保留奇数项，可以这么写:

    L = [ 1 , 2 , 3 , 4 , 5 , 6 ]
    L = [x for x in L if x % 2 != 0 ]
    L
    [ 1 , 3 , 5 ]
4.2. 带有for嵌套

在复杂一点的列表推导式中，可以嵌套有多个 for 语句。按照从左至右的顺序，分别是外层循环到内层循环。

例如：

    [x + y for x in  'ab'  for y in  'jk' ]
    [ 'aj' , 'ak' , 'bj' , 'bk' ]
4.3. 既有if语句又有for嵌套

列表推导式可以带任意数量的嵌套 for 循环，并且每一个 for 循环后面都有可选的 if 语句。

通用语法：

    [ expression for x in X [ if condition]
              for y in Y [ if condition]
              ... 
             for n in N [ if condition] ]
例如，下面的代码输出了0~4之间的偶数和奇数的组合。

    [(x, y) for x in  range ( 5 ) if x % 2 == 0  for y in  range ( 5 ) if y % 2 == 1 ]
    [( 0 , 1 ), ( 0 , 3 ), ( 2 , 1 ), ( 2 , 3 ), ( 4 , 1 ), ( 4 , 3 )]

等价于下面的一般 for 循环：

    L = []
    for x in range( 5 ):
        if x % 2 == 0 :
            for y in range( 5 ):
                if y % 2 == 1 :
                    L.append((x, y))

    [( 0 , 1 ), ( 0 , 3 ), ( 2 , 1 ), ( 2 , 3 ), ( 4 , 1 ), ( 4 , 3 )]

4.4. 列表推导式生成矩阵

>生成矩阵的方式有多种，例如手动赋值、一般for循环，还有就是列表推导式。如果我们要用列表推导式生成下面的矩阵，可以怎么写？

    M = [[1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]]

一种方法是：

    M = [[x, x+1, x+2] for x in [1, 4, 7]]
    M
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]


矩阵的列数少时可以使用这种方法。

>如果矩阵的列数较多，我们可以使用另外一种方式：在循环变量的表达式中使用列表推导式。

具体代码如下：

    M = [[y for y in range(x, x+3)] for x in [1, 4, 7]]
    M
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

与之前带 for 嵌套的语法不同，这个例子中，实际使用的是最基本的 [expression for x in L] 语法，只有一个 for 语句。

复杂的地方在于前面的变量表达式 expression 不再是简单的变量运算，而是一个列表推导式，在这个例子中就是 [y for y in range(x, x+3)] 。内层的列表推导式返回一个行向量，而这些行向量经由外层的列表推导式，最终形成一个二维列表，也就是我们想要的矩阵。

当然，在实际的应用中不能单纯追求代码的简洁，还要考虑到代码的可读性和维护成本。如果代码变得过于复杂，不易于理解，我们宁可多写几行代码来增加它的可读性。

5. 生成器表达式

生成器表达式与列表推导式的语法相同，区别在于生成器表达式的外面使用圆括号，而列表推导式使用方括号。

有关生成器的介绍，请参考这篇文章： 《Python高级编程之初识生成器》

6. 集合推导式和字典推导式

注意：集合推导式和字典推导式只有在Python2.7以及之后的版本中才有，Python2.7之前的版本不支持这两种推导式。

集合推导式的语法与列表推导式相同，只需要把外面的方括号改成花括号即可。

例如，我们可以通过以下方式来生成一个集合：

    {x ** 2  for x in [ 1 , 2 , 2 ]}
    { 1 , 4 }
字典推导式的外面也是使用花括号，不过花括号的内部需要包含键值两部分。

在值不重复的情况下，我们可以通过字典推导式快速交换键值对：

    D = { 'a' : 1 , 'b' : 2 , 'c' : 3 }
    D = { value: key for key, value in D.items()}
    D
    { 1 : 'a' , 2 : 'b' , 3 : 'c' }