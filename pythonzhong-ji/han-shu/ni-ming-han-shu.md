##python闭包(Closure):内层函数引用了外层函数的变量(包括它的参数),然后返回内层函数的情况,这就是闭包.

返回函数千万不要引用任何一个循环变量,或者在之后会发生改变的变量.

    # 希望一次返回3个函数，分别计算1x1,2x2,3x3:  
    def count():  
        fs = []  
        for i in range(1, 4):  
            def f():  
                 return i*i  
            fs.append(f)  
        return fs  
      
    f1, f2, f3 = count()  
      
    print f1(), f2(), f3() 
    
###用闭包解决
    #coding:utf-8  
    __author__ = 'chad'  
    #希望一次返回3个函数，分别计算1x1,2x2,3x3:  
    def count():  
        fs = []  
        for i in range(1, 4):  
            def f(j):  
                def g():  
                    return j*j  
                return g  
            fs.append(f(i))  
        return fs  
      
    f1, f2, f3 = count()  
      
    print f1(), f2(), f3()  