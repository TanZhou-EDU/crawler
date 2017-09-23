
装饰器是可调用的对象，其参数是另一个函数（被装饰的函数)

装饰器可能会处理被装饰的函数，然后把它返回，或者将其替换成另一个函数或可调用对象。

###装饰器特性：
- 会把被装饰的函数(通过参数传进来的函数)替换成其他函数，返回的函数不是原来那个函数了
- 装饰器在加载模块时立即执行
- 装饰器通常在一个模块中集中定义，然后应用到其他模块中的函数上
- 装饰器函数通常用来作为收集函数的函数，可以把被装饰的函数批量处理

###被装饰器修饰过的函数，\__name__,\__doc__会指向装饰器函数，functools.wraps(func)可以修复被装饰的函数\__name__ &nbsp; \__doc__属性
    import functools
    def deco(func):
        functools.wraps(func)
        def _demo():
            pass
        return _demo
    def demo():
        pass

###可存储函数返回值的装饰器:**functools.lru_cache**
lru_cache装饰器可以把耗时的函数结果缓存起来，避免传入相同参数时重复计算
    参数：
    **maxsize=128** #存储函数128个调用结果，为了得到最大性能，最好设为2的倍数
    **typed = False**  设为True,把不同参数类型得到的的结果区分开，如(1.0 和 1)
    
    @functools.lru_cache
    def demo():
        pass
###**functools.singledispatch** 装饰器
>functools.singledispatch 装饰器实现函数，方法的重载，比一个函数里使用一长串 if/elif/
elif/elif 块要更好
它可以把整体方案拆分成多个模块，甚
至可以为你无法修改的类提供专门的函数。使用 @singledispatch 装饰的普通函数会变成
泛函数（generic function）：根据第一个参数的类型，以不同方式执行相同操作的一组函数
@singledispath 的优点是支持模块化扩展：各个模块可以为它支持的各个类型注册一个专门函数。

    from functools import singledispatch
    from collections import abc
    import numbers
    import html
    
    @singledispatch
    def htmlize(obj):
    	content = html.escape(repr(obj))
    	return '<pre>{}</pre>'.format(content)
    	
    @htmlize.register(str)
    def _(text):
    	content = html.escape(text).replace('\n', '<br>\n')
    	return '<p>{0}</p>'.format(content)
    
    @htmlize.register(numbers.Integral)
    def _(n):
    	return '<pre>{0} (0x{0:x})</pre>'.format(n)
    
    @htmlize.register(tuple)
    @htmlize.register(abc.MutableSequence)
    def _(seq):
    	inner = '</li>\n<li>'.join(htmlize(item) for item in seq)
    	return '<ul>\n<li>' + inner + '</li>\n</ul>'
    
    print(htmlize(('aa','bb','ccc')))


    
    
    


