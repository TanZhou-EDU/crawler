- 类的\__iter\__和\__next__方法都实现了，那么这个类实例化对象是一个迭代器,构造了一个迭代容器对象
- 判断某个值是 迭代器 还是迭代容器 :iter(obj) is iter(obj) 等于FALSE是迭代容器，true为迭代器
- 生成器就是一个迭代器，迭代器不一定是生成器



##可迭代对象
- 字符串，列表list, 元组tuple，字典dict, 集合set都是可迭代(iterable)的对象，但不是迭代器
- from collections import Iterable 可以检测对象是否可迭代


##生成器 generator对象
>生成器是在函数内使用yield表达式的函数，该函数是实现了一个生成器，生成器是一个迭代器

检测一个对象是否是生成器：
    
    import inspect
        def mygenerator():
            yield 1
            yield ....

    print(inspect.isgenerator(mygenerator()))
    print(inspect.isgeneratorfunction(mygenerator))

###类实现的生成器: \__iter__魔术方法：
- 该方法必须返回一个迭代器(iterator)，不用显示返回，如果该方法实现了生成器(有yield表达式)，那么它就是一个迭代器
- 触发时机：iter(这个类的实例化对象), 循环遍历这个类的实例化对象的时候
- \__iter__内部如果使用了yield表达式,则是一个生成器，调用该方法生成器并不会运行，而是调用了迭代器，迭代器会调用内置的next函数，next函数会把生成器推进到下一个yield表达式那里。生成器传给yield的每一个值，都会由迭代器返回给调用者。

        class Mygenerator:
            def __iter__(self):
                for i in range(10):
                    yield i

        #for循环Mygenerator,这个对象会自动调用__iter__
        #因为__iter__实现了生成器，它是一个迭代器，所以可迭代的
        for gent in Mygenerator(): 
            print(gent)

###函数实现的生成器
定义生成器的函数，在函数内部使用yield，该函数自动返回一个迭代器
注意：该迭代器是有状态，只能迭代一次
解决办法:
    - list复制生成器数据
    - 通过lambda返回这个函数，每次调用都会返回一个新的迭代器
    
    def mygenrator():
        for i in range(10):
            yield i
    mygen = mygenrator()
    
    for gent in mygen:
        print(gent)
    for gent in mygen:  #这个循环不会执行
        print(gent)
        
    #list 解决有弊端，会把生成器所有数据都读取出来，失去了生成器原来作用
    list_data = mygen
    for gent in list_data:
        print(gent)
    for gent in list_data:
        print(gent)

###查看生成器当前状态
    
    import inspect
    inspect.getgeneratorstate(生成器对象)

- GEN_CREATED 生成器等待第一次执行
- GEN_RUNNING 生成器正在运行
- GEN_SUSPENDED 等待被next()调用唤醒
- GEN_CLOSED  生成器执行完毕
        



##迭代器
>迭代器协议:如果把迭代器对象传给内置的iter函数,那么此函数会把该迭代器返回,如果传给iter函数的是个容器类型对象,那么iter函数每次都会返回新的迭代器对象

- 序列，字符串，类方法\__iter__实现的生成器对象都是容器类型
- iter(iterable) 返回一个迭代器，iter必须接收一个iterable对象
-  检测对象是否为一个迭代器
    
        from collections import Iterator    print(isinstance(iter([]), Iterator))


