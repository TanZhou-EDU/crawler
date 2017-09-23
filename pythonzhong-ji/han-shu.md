##函数的定义



##函数的作用域
在局部函数里存在同名的全局变量名，给同名的全局变量赋值，在赋值之前引用，会报错local variable 'foo' referenced before assignment(本地变量“foo”在赋值前被引用)

问题分析：python编译函数的定义时，它判断foo是局部变量，因为在函数中给它赋值了,python会假定在函数体内定义的变量是局部变量，在赋值前访问局部变量，发现foo没有绑定指，所以报错

    foo = 6
    def f2(a):
    	# print(a)
    	print(b)
    	foo = 10
    f2(2)
    print(b)
    
####提升局部变量为全局变量
    global 局部变量名
    
>注意：全局变量在多级嵌套函数里可以正常访问，在函数里给全局变量同名的局部变量赋值会隐士重新声明一个本地变量，改变该变量，同名的全局变量不会受到影响

####函数内的本地变量
在嵌套函数中，内层函数访问外层函数局部变量，可以正常访问，但修改会报错local variable 'foo' referenced before
给该变量加上 nonlocal 变量名 提升该变量为自由变量，可以解决此问题

####内置属性和方法
获得函数名：
    
    函数.__name__

获得函数体内的所有属性：
    
    函数.__code__

获得函数体内的所有局部变量：
    
    函数.__code__.co_varnames
    
获得函数体内的所有自由变量(自由变量是指未在本地绑定的变量)：

    函数.__code__co.freevars

    __closure__ 中的各个元素对应于 avg.__code__.co_freevars 中的一个名称,这些元素是 cell 对象，有个 cell_contents 属性
    
    函数.__closure__[0].cell_contents



