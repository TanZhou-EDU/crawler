#pip是一款非常方便的python包管理工具，本文主要介绍在windows 10下安装pip方法。
1. 下载pip安装包，地址：
https://pypi.python.org/pypi/pip#downloads
注意选择tar.gz包，目前最新版本为：
pip-8.1.2.tar.gz (md5, pgp)
2. 解压安装包（如解压至系统D盘），打开Windows CMD，运行如下命令进入解压后的pip目录
cd D:\pip-8.1.2
3. 使用如下命令进行安装
python setup.py install
4. 添加windows系统环境变量，与安装python时添加的方法一样
如我的python目录是
F:\Python27\;
则添加如下2个目录到系统环境变量里：
F:\Python27\;F:\Python27\Scripts;
5. 进入CMD运行pip，如下图所示即表示已安装成功
![](/assets/1499429337165_9.png)
#pip常用命令
###安装包 
**pip install xxx**
###升级包，可以使用-U 或者 --upgrade 
**pip install -U xxx**
###卸载包 
**pip uninstall xxx** 
###列出已安装的包 
**pip list**