OO 面向对象
OOA 面向对象的分析
OOD 面向对象的设计
OOI 面向对象的实现
OOP 面向对象的程序开发
OOA->OOD->OOI 面向对象的实现过程

##类和对象的关系
>类是由对象抽象总结而来的，
由对象总结出类的过程，称之为抽象化
对象是由类具体实施或者实现而来
由类制作出对象的过程，称之为实例化

- 用于表示事物特征相关的内容，称之为成员属性（变量）

- 用于表示事物功能相关的内容，称之为成员方法（函数）

##类文件命名采用驼峰名法：

- 保证每个单词的首字母都要大写
例如： MyCar 类      Image类    DoYourSister类

- 其他变量命名规范：
my_sister,my_girl.....

##声明一个类
1.声明类必须使用class关键字
2.类中内容由2部分组成：成员属性和成员方法，其他内容禁止在类中出现，比如流程控制，循环语句等操作，语法没错，但是破坏了类的结构。
3.定义成员属性使用变量赋值操作即可，如果某个成员没有值，需要使用None来赋值
4.定义成员方法使用函数声明规则即可。

##实例化类
变量 = 类名（）  #实例化了一个对象

##类和对象的成员分析
1.类和对象都可以存储成员。成员可以归类所有，也可以归对象所有
2.类存储成员时使用的是与类关联的一个类对象
3.对象存储成员时就是存储在当前对象当中
4.在对象中访问一个成员时，如果对象中没有该成员，尝试访问类中的同名成员，如果对象中有该成员呢，一定使用对象中的成员。
5.创建对象时，类中的成员不会进入对象当中，而是得到一个空的对象，没有成员。
6.通过对象对类中成员重新赋值或者通过对象添加成员时，对应成员会保存在对象中，而不会修改类成员

关于self
1.self的英文意思就是自己
2.self在对象的方法中表示当前对象本身，如果通过对象调用一个方法，那么该对象会自动传入到当前方法的第一个参数中。
3.self单词并不是关键字，只是一个用于接收对象的普通形参名称，所以可以使用任何变量名代替
4.方法中有self形参（并且设定为接收对象使用的参数）的方法称之为非绑定类的方法，可以通过对象访问，没有self的就是绑定类的方法，只可以通过类来访问
5.使用类访问绑定类的方法时，如果类方法中需要访问当前类的成员（无论属性还是方法），可以通过__class__.成员名 来访问类中其他成员（对象对应的是self.成员名）

>注意：一个方法是不是绑定类的方法不取决于方法本身的结构，而是取决于如何调用该方法，将该方法的形参当作接收什么值的形参使用

    class Demo:
        def test(self):
            pass

    当作绑定类的方法
    Demo.test(随意参数)
    
    当作非绑定类的方法
    demo = Demo()
    demo.test()
