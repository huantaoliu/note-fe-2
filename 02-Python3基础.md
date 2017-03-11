#### **Python入门**
* [廖雪峰-Python教程](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)
```


```


* * * * *

* 安装
	* [Python下载](https://www.python.org/downloads/windows/)
    * [第三方库安装-非官方](http://www.lfd.uci.edu/~gohlke/pythonlibs/)
```

// python安装注意事项
可执行版本
for all users
add to path

// ipython notebook
在web浏览器运行  

// Sublime编辑器

// pyCharm
进入 file > Settings，
在输入框搜索 encoding。
找到 Editor > File encodings，
将 IDE Encoding 和 Project Encoding 设置为utf-8

// 安装第三方库
cd /d folder
pip install xxx.whl

pip3 freeze // 此命令显示安装过哪些
```


* [Sublime Text 3 python 配置](http://www.cnblogs.com/waising/articles/3466120.html)
	* [pylinter下载](https://github.com/biermeester/Pylinter)
    * <del>[pylinter路径问题](https://www.baidu.com/link?url=yEoP4X-gVdIPEvq6qV_qvkOpBUCcl2lFFq-Ivn4mn4vlAqmv5DtHYWbJgZG-VxY981sMt7z3Vp2pKpdulS6i7a&wd=&eqid=c46c4cf000149f3a0000000458b16c19)</del>
    * [Python编译系统配置](http://blog.csdn.net/tstbdt/article/details/44490061)
```

注意Python3需要另外配，并不兼容

// pylinter插件 
SublimeCodeIntel 插件
Python PEP8 Autoformat 插件 自动格式化 CTRL+SHIFT+R 
```


* * * * *

* 基础
```

解释型、面向对象、动态数据类型的高级程序设计语言
结合了解释性、编译性、互动性和面向对象的脚本语言

Python的最大的优势之一是丰富的库，
跨平台的，
在UNIX，Windows和Macintosh兼容很好。

如果你需要一段运行很快的关键代码，
或者是想要编写一些不愿开放的算法，
你可以使用C或C++完成那部分程序，
然后从你的Python程序中调用。

GPL(GNU General Public License)协议

// Python 3.0+
#!/usr/bin/python3
print("Hello, World!");

// Python2+ 中文编码问题
#!/usr/bin/python
# -*- coding: UTF-8 -*-
print "你好，世界";

而Python3+ 已经默认指定utf-8

// 命令执行脚本
$ python3 hello.py

// 命令行参数		
$ python -h

CTRL+C 来退出当前的无限循环

在 while … else 在条件语句为 false 时执行 else 的语句块：
```


* 日期与时间
```

转换日期格式是一个常见的功能

time 和 calendar 模块
datetime模块

时间戳单位最适于做日期运算。
但是1970年之前的日期就无法以此表示了。
太遥远的日期也不行，UNIX和Windows只支持到2038年。

时间元组

日期格式化 strftime

时间日期格式化符号
```


* 语法
```

// python保留字
import keyword
keyword.kwlist 

// 行与缩进
python最具特色的就是使用缩进来表示代码块，
不需要使用大括号({})
缩进的空格数是可变的，
但是同一个代码块的语句必须包含相同的缩进空格数

// 使用反斜杠(\)来实现多行语句
total = item_one + \
        item_two + \
        item_three

// 这种情况，不需要反斜杠
total = ['item_one', 'item_two', 'item_three',
'item_four', 'item_five']

// 空行
函数之间或类的方法之间用空行分隔，
表示一段新的代码的开始。
类和函数入口之间也用一行空行分隔，
以突出函数入口的开始。

便于日后代码的维护或重构。
空行也是程序代码的一部分。

// 等待输入
input("\n\n按下 enter 键后退出。")

// 同一行显示多条语句 
// 分号
import sys; x = 'runoob'; sys.stdout.write(x + '\n')

// 解释器

// 注释
# 这是一个注释

'''
这是多行注释
'''

// 逻辑控制
循环语句可以有 else 子句，
它在穷尽列表(以for循环)
或条件变为 false (以while循环)
导致循环终止时被执行,
但循环被break终止时不执行

Python pass是空语句，
是为了保持程序结构的完整性。
pass 不做任何事情，一般用做占位语句
```


* 数据类型
```

// Python3 中有六个标准的数据类型：
Number
String
List（列表）
Tuple（元组）
Sets（集合）
Dictionary（字典）

Number（数字）
Python3 支持 int、float、bool、complex（复数）
没有 python2 中的 Long

2 / 4  # 0.5
2 // 4 # 0
2 ** 5 # 乘方 32

混合计算时，Python会把整型转换成为浮点数

在交互模式中，最后被输出的表达式结果被赋值给变量 _
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06

// 数学函数 随机函数 三角函数 常量


// List
使用最频繁的数据类型
列表中的元素是可以改变的

for x in [1, 2, 3]: print(x);

// 嵌套列表
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'

>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> del a[:]
>>> a
[]

// Tuple（元组）
元组的元素不能修改

元组中只包含一个元素时，需要在元素后面添加逗号
tup1 = (50,);

string、list和tuple都属于sequence（序列）。

// Set（集合）
无序不重复元素
基本功能是进行成员关系测试和删除重复元素
可以使用大括号({})或者 set()函数创建集合，
注意：创建一个空集合必须用 set() 而不是 { }，
因为 { } 是用来创建一个空字典。

// Dictionary
无序
字典当中的元素是通过键来存取的，
而不是通过偏移存取。
键(key)必须使用不可变类型。
所以可以用数字，字符串或元组充当，而用列表就不行
在同一个字典中，键(key)必须是唯一的。

// 数据类型转化
```


* 字符串
```

字符串是不可变的

Python 没有单独的字符类型，
一个字符就是长度为1的字符串

python中单引号和双引号使用完全相同

// 字符串更新
#!/usr/bin/python3
var1 = 'Hello World!'
print ("已更新字符串 : ", var1[:6] + 'Runoob!')

// 字符串格式化
print ("我叫 %s 今年 %d 岁!" % ('小明', 10))

// 使用三引号('''或""")可以指定一个多行字符串
三引号让程序员从引号和特殊字符串的泥潭里面解脱出来
paragraph = """这是一个段落，
可以由多行组成"""

在Python3中，所有的字符串都是Unicode字符串。

自然字符串， 通过在字符串前加r或R。 
如 r"this is a line with \n" 则\n会显示，并不是换行

// 字符串内建函数
```


* 运算符
```

// 赋值运算符
c **= a 等效于 c = c ** a
c //= a 等效于 c = c // a

// 位运算符

// 逻辑运算符
and or not

// 成员运算符
in 
not in

// 身份运算符
is 
is not
```


* 迭代器和生成器
```

迭代是Python最强大的功能之一，
是访问集合元素的一种方式。

迭代器只能往前不会后退

iter() 和 next()。

// 生成器
使用了 yield 的函数被称为生成器
生成器就是一个迭代器
```


* 函数
```

#!/usr/bin/python3

# 计算面积函数
def area(width, height):
    return width * height
 
w = 4
h = 5
print("width =", w, " height =", h, " area =", area(w, h))

// 引用传递
在 Python 中，所有参数（变量）都是按引用传递。
如果你在函数里修改了参数，
那么在调用这个函数的函数里，
原始的参数也被改变了

// 参数
必需参数
关键字参数
默认参数
不定长参数 能处理比当初声明时更多的参数
加了星号（*）的变量名会存放所有未命名的变量参数。
如果在函数调用时没有指定参数，
它就是一个空元组。
我们也可以不向函数传递未命名的变量

// 匿名函数
python 使用 lambda 来创建匿名函数。
虽然lambda函数看起来只能写一行，
却不等同于C或C++的内联函数，
后者的目的是调用小函数时不占用栈内存从而增加运行效率。

sum = lambda arg1, arg2: arg1 + arg2;

# 调用sum函数
print("相加后的值为 : ", sum(10, 20))
print("相加后的值为 : ", sum(20, 20))
```


* 错误与异常
```

语法错误和异常

用户中断的信息会引发一个 
KeyboardInterrupt 异常

try except 语句还有一个可选的else子句，
如果使用这个子句，
那么必须放在所有的except子句之后。
这个子句将在try子句没有发生任何异常的时候执行

异常处理并不仅仅处理那些直接发生在try子句中的异常，
而且还能处理子句中调用的函数（甚至间接调用的函数）里抛出的异常

使用 raise 语句抛出一个指定的异常
raise NameError('HiThere')

// 自定义异常类

大多数的异常的名字都以"Error"结尾，就跟标准的异常命名一样

// 定义清理行为

以上例子不管try子句里面有没有发生异常，finally子句都会执行。
如果一个异常在 try 子句里（或者在 except 和 else 子句里）被抛出，
而又没有任何的 except 把它截住，
那么这个异常会在 finally 子句执行后再次被抛出。

// 预定清理行为
with语句
```


* 输入输出
	* [runoob-输入输出](http://www.runoob.com/python3/python3-inputoutput.html)
```

表达式语句和 print() 函数
文件对象的 write() 方法
str.format() // 推荐
将输出的值转成字符串，
可以使用 repr() 或 str() 函数来实现

// 旧式字符串格式化

调用 f.close() 来关闭文件并释放系统的资源，
如果尝试再调用该文件，则会抛出异常

如果要改变文件当前的位置, 
可以使用 f.seek(offset, from_what) 函数。
from_what 的值, 
如果是 0 表示开头, 如果是 1 表示当前位置, 2 表示文件的结尾

pickle 模块
```


* 文件
```

os 模块提供了非常丰富的方法用来处理文件和目录
```

