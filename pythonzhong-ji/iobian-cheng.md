#文件基本操作
###打开文件:
#####以只读方式打开
    f = open('/Users/michael/test.txt', 'r') #以只读文本模式打开
    f = open('/Users/michael/test.jpg', 'rb') #读取二进制文件,图片,视频等
    f = open('/Users/michael/gbk.txt', 'r', encoding='gbk') #读取GBK编码文件,默认读取UTF-8
    f = open('/Users/michael/gbk.txt', 'r', encoding='gbk', errors='ignore') #读取文件过程中遇到编码错误直接忽略
#####以写入方式打开
    f = open('/Users/michael/test.txt', 'w')

#####**<font size=4>with打开写入</font>**推荐使用
    用with不必调用f.close()方法,python自动调用
    with open('/path/to/file', 'r') as f:
        print(f.read())
    with open('/Users/michael/test.txt', 'w') as f:
        f.write('Hello, world!')
###读取文件内容
    f.read()
    f.read(size) 每次最多读取size个字节的内容
    f.readline() 每次读取一行内容
    f.readlines() 一次读取所有内容并按行返回list
###关闭文件
    f.close()
###异常处理
    try:
        f = open('/path/to/file', 'r')
        print(f.read())
    finally:
        if f:
        f.close()
###文件缓冲区buffering
>将文件内容写入到硬盘设备时，使用系统调用，这类I/O操作的时间很长，为了减少I/O操作的次数，文件通常使用缓冲区（有足够多的数据才进行系统调用），文件的缓存行为，分为全缓冲、行缓存、无缓冲。
如何设置Python中文件对象的缓冲行文？
解决方案
####全缓冲： open 函数的 buffering 设置为大于1的整数n，n为缓冲区大小

    f = open('demo2.txt', 'w', buffering=2048)
    f.write('+' * 1024)
    f.write('+' * 1023)
    # 大于2048的时候就写入文件
    f.write('-' * 2)
    f.close()
####行缓冲： open 函数的 buffering 设置为1

    f = open('demo3.txt', 'w', buffering=1)
    f.write('abcd')
    f.write('1234')
    # 只要加上\n就写入文件中
    f.write('\n')
    f.close()
####无缓冲： open 函数的 buffering 设置为0

    f = open('demo4.txt', 'w', buffering=0)
    f.write('a')
    f.write('b')
    f.close()








##import os 操作系统接口函数
###<strong>os.name</strong>  返回操作系统类型:
- nt : window
- posix : liunx unix mac os
    - os.uname linux操作系统详细信息

###<strong>获取操作系统环境变量</strong>
####在操作系统中定义的环境变量，全部保存在os.environ这个变量中
- os.environ.get(key)
    - os.environ.get('PATH') 环境变量
    - os.environ.get('x', 'default')

###<strong>操作文件和目录</strong>
####<strong>查看当前文件的绝对路径</strong>
- os.path.abspath('.')
- os.getcwd()
####把两个路径合成一个时，不要直接拼字符串，而要通过os.path.join()函数，这样可以正确处理不同操作系统的路径分隔符,拆分路径(同理) os.path.split('path')
-  os.path.join('/Users/michael', 'testdir')
    - 在window下output : /Users/michael\testdir
    - 在Linux 下outpu  : /Users/michael/testdir
- os.path.split('/Users/michael/testdir/file.txt')
    拆分路径
- os.path.splitext('/path/to/file.txt')
    - ('/path/to/file', '.txt')
    获取文件扩展名
####<strong>创建目录dir</strong>
- os.mkdir('/Users/michael/testdir') 创建testdir
- os.makedirs(('/Users/michael/testdir')) 批量顺序创建User,michael,testdir

        
        not os.path.exists('e:\\python\\aadir') and os.makedirs('./aadir/testdir/bdir/cdir/')

#####<strong>删除目录文件</strong>
- os.rmdir('dir')  删除一个目录
- os.remove('file') || os.unlink('file')  删除一个文件

#####<strong>获取目录下的所有目录和文件</strong>
- os.listdir('dirname')
        
        [x for x in os.listdir('.') if os.path.isdir(x)] 获取当前目录下所有dir
    
        [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1] == 'py' ]
        获取当前目录下所有py文件

####os函数
- os.listdir()
- os.path.isdir()
- os.path.isfile()
- os.path.split()
- os.path.splitext()
    