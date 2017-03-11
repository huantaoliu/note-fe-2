#### **Python基础2**
* 模块
```

sys.path 
包含了一个 Python 解释器自动查找所需模块的路径的列表

一个模块只会被导入一次，
不管你执行了多少次import。
这样可以防止导入模块被一遍又一遍地执行。

从模块中导入一个指定的部分
>>> from fibo import fib, fib2
from modname import *
划线（_）开头的名字不在此例

dir() 可以找到模块内定义的所有名称

// 包
不同的作者都可以提供 NumPy 模块，
或者是 Python 图形库。

目录只有包含一个叫做 __init__.py 的文件
才会被认作是一个包

import sound.effects.echo
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)

from sound.effects import echo
echo.echofilter(input, output, delay=0.7, atten=4)

// 从一个包中导入*
__all__ = ["echo", "surround", "reverse"]
这表示当你使用from sound.effects import *这种用法时，
你只会导入包里面这三个子模块。
```


* 标准库
```

import os

>>> import shutil
>>> shutil.copyfile('data.db', 'archive.db')
>>> shutil.move('/build/executables', 'installdir')

// 从目录通配符搜索中生成文件列表
>>> import glob
>>> glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']

>>> import sys
>>> print(sys.argv)
['demo.py', 'one', 'two', 'three']
sys 还有 stdin，stdout 和 stderr 属性

// 字符串正则匹配
>>> import re
>>> re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')
['foot', 'fell', 'fastest']
>>> re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
'cat in the hat'

>>> import math
>>> math.cos(math.pi / 4)
0.70710678118654757
>>> math.log(1024, 2)
10.0

>>> import random
>>> random.choice(['apple', 'pear', 'banana'])
'apple'
>>> random.sample(range(100), 10)   # sampling without replacement
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
>>> random.random()    # random float
0.17970987693706186
>>> random.randrange(6)    # random integer chosen from range(6)
4

// 访问 互联网

// 日期时间

// 数据压缩

// 性能度量
timeit

// 测试模块
doctest
```


* 面向对象
```

类的继承机制允许多个基类，
派生类可以覆盖基类中的任何方法，
方法中可以调用基类中的同名方法。

// 构造方法
def __init__(self):
    self.data = []
    
self代表类的实例，而非类，代表当前对象的地址，
而 self.class 则指向类

类的方法与普通的函数只有一个特别的区别——
它们必须有一个额外的第一个参数名称, 
按照惯例它的名称是 self。

若是父类中有相同的方法名，
而在子类使用时未指定，
python从左至右搜索 即方法在子类中未找到时，
从左到右查找父类中是否包含方法。

两个下划线开头，声明该属性为私有
self.__private_attrs。

// 类的专有方法
__init__ : 构造函数，在生成对象时调用
__del__ : 析构函数，释放对象时使用
__repr__ : 打印，转换
__setitem__ : 按照索引赋值
__getitem__: 按照索引获取值
__len__: 获得长度
__cmp__: 比较运算
__call__: 函数调用
__add__: 加运算
__sub__: 减运算
__mul__: 乘运算
__div__: 除运算
__mod__: 求余运算
__pow__: 称方

```


* 正则表达式
```

// match与search的区别
re.match只匹配字符串的开始，
如果字符串开始不符合正则表达式，则匹配失败，函数返回None；
而re.search匹配整个字符串，直到找到一个匹配。

re.sub用于替换字符串中的匹配项

// 正则表达式修饰符
re.I	 使匹配对大小写不敏感
re.L	做本地化识别（locale-aware）匹配
re.M   多行匹配，影响 ^ 和 $
re.S	使 . 匹配包括换行在内的所有字符
re.U  
re.X

// 正则表达式模式
标点符号只有被转义时才匹配自身，否则它们表示特殊的含义

// 实例
[Pp]ython	匹配 "Python" 或 "python"
rub[ye]	匹配 "ruby" 或 "rube"
[aeiou]	匹配中括号内的任意一个字母
[0-9]	匹配任何数字。类似于 [0123456789]
[a-z]	匹配任何小写字母
[A-Z]	匹配任何大写字母
[a-zA-Z0-9]	匹配任何字母及数字
[^aeiou]	除了aeiou字母以外的所有字符
[^0-9]	匹配除了数字外的字符
```


* 多线程
```

使用线程可以把占据长时间的程序中的任务放到后台去处理

线程可以被抢占（中断）

线程可以分为:
内核线程：由操作系统内核创建和撤销。
用户线程：不需要内核支持而在用户程序中实现的线程。

Python3 线程中常用的两个模块为：
_thread
threading(推荐使用)

在 Python3 中不能再使用"thread" 模块。
为了兼容性，Python3 将 thread 重命名为 "_thread"

run()
start()
join([time]): 等待至线程中止。这阻塞调用线程直至线程的join() 方法被调用中止-正常退出或者抛出未处理的异常-或者是可选的超时发生。
isAlive()
getName()
setName()

// 线程同步
如果多个线程共同对某个数据修改，则可能出现不可预料的结果
使用 Thread 对象的 Lock 和 Rlock 可以实现简单的线程同步
acquire 方法和 release 方法

// 锁

// 线程优先级队列
Queue 模块中提供了同步的、线程安全的队列类，包括FIFO（先入先出)队列Queue，LIFO（后入先出）队列LifoQueue，和优先级队列 PriorityQueue。
```


* CGI编程
```

Apache 支持CGI 配置

修改文件权限为 755

// CGI环境变量

// get和post方法

// CGI中使用Cookie

// 文件上传实例
```



* 网络编程
```

两个级别访问的网络服务
低级别的网络服务支持基本的 Socket，
它提供了标准的 BSD Sockets API，
可以访问底层操作系统Socket接口的全部方法。

高级别的网络服务模块 SocketServer， 
它提供了服务器中心类，
可以简化网络服务器的开发

Socket 
向网络发出请求或者应答网络请求，
使主机间或者一台计算机上的进程间可以通讯。

// Python Internet 模块
HTTP	网页访问	80	httplib, urllib, xmlrpclib
NNTP	阅读和张贴新闻文章，俗称为"帖子"	119	nntplib
FTP	文件传输	20	ftplib, urllib
SMTP	发送邮件	25	smtplib
POP3	接收邮件	110	poplib
IMAP4	获取邮件	143	imaplib
Telnet	命令行	23	telnetlib
Gopher	信息查找	70	gopherlib, urllib

// SMTP发送邮件
SMTP（Simple Mail Transfer Protocol）

// 使用Python发送HTML格式的邮件
// Python 发送带附件的邮件
// 在 HTML 文本中添加图片
```


* XML解析与JSON
```

python有三种方法解析XML，
SAX，DOM，以及ElementTree:

SAX用事件驱动模型，
通过在解析XML的过程中触发一个个的事件
并调用用户定义的回调函数来处理XML文件。

```

