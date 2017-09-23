
描述器作用：
    对成员属性的操作：获取值，设置/添加值，删除值
#成员描述符
python描述符是为了在类中对类中的成员属性进行相关操作而创建的一种方式，主要作用就是管理成员属性或者对成员属性进行验证等操作。
###描述符的相关操作：
>get  获取属性操作
set  修改或者添加属性操作
delete  删除属性操作

##使用类实现描述器
    class Decriptor:
    
        #初始化方法将描述其控制的成语属性添加到类中
        def __init__(self):#self 描述符对象
            self._name = ''
    
        #获取描述其控制成员属性的获取操作
        def __get__(self,obj,cls): #self 描述符对象，obj 管理成员属性的对象,cls 管理成员属性的类
            #验证或者修改等操作
            return self._name #此处修改获取值的格式
    
        #设置描述器控制的成员属性的设置操作
        def __set__(self,obj,value):#self 描述符对象，obj 管理成员属性的对象,value设置的值
            #此处可以多设置的值进行验证限制等操作
    
            self._name = value #赋值操作
    
        #设置描述器控制的成员属性的删除操作
    
        def __delete__(self,obj)：#self 描述符对象，obj 管理成员属性的对象
    
            #此处可以在删除值之前进行验证等操作
            del self._name

    #描述其操作的类
    class Email：
        #需要使用描述符控制器的成员属性
        name = Decriptor()

###使用property函数实现描述符
    #email类

    class Email:
        #邮箱用户
        #name = ''

    #-----------描述符设置--------------

    #获取name属性的描述符方法
    def fget(self):
        return self._name[:10]

    #设置name属性的描述符方法
    def fset(self,value):
        #判断是否是小写不是小写都转为小写
        if value.islower():
            self._name = value
        else:
            self._name = value.lower()

    #删除name属性的描述符方法
    def fdel(self):
        del self._name

##使用属性修饰符方法
    #邮箱类
    class Email:
    #init方法初始化成员
        def __init__(self):
            #_name是描述符操作真实name属性的对应属性名  _name可以是任意名称别用属性本身
            self._name = ''

    #用户名属性 进行控制 name
    @property #默认获取操作设置
    def name(self):
        return self._name

    @name.setter #负责设置操作
    def name(self,value):
        self._name = value

    @name.deleter #负责删除操作
    def name(self):
        del self._name

    #在类中直接设置描述符
    name = property(fget,fset,fdel)
    #---------------------------------

注意：无论哪种修饰符都是为了对成员属性进行访问相关控制

>类的方式 :适合多个类中的多个属性共用一个描述符的方式
propert方式：适合当前类中使用，可以控制一个类中多个属性
属性修饰符：适合当前类中使用,控制一个类中一个属性
