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
    