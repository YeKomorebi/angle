# Python 

## 环境配置

### Anaconda

Anaconda指的是一个开源的[Python](https://baike.baidu.com/item/Python)发行版本，其包括Conda、Python以及一大堆安装好的工具包，比如：[numpy](https://baike.baidu.com/item/numpy/5678437)、[pandas](https://baike.baidu.com/item/pandas/17209606)等

**一、Anaconda 的安装**

Anaconda 安装包可以到 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/ 下载。双击开始安装，记住安装的位置。

**二、Anaconda 替换下载源**

由于Anaconda默认的下载源在国外，下载速度较慢，可以换成国内的下载源，如阿里源、清华源等。

显示用户目录下的`.condarc`文件

```sh
conda config --set show_channel_urls yes
```
按下`windows`键+`R`键，输入`cmd`按下回车打开终端。在终端中输入：

```sh
.condarc
```

复制以下内容替换到打开的文件中：

```sh
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

保存并关闭`.condarc`文件，继续在终端中输入：
```sh
conda clean -i	# 清除索引缓存
```

**三、安装Python**

继续在终端中操作，执行下列命令创建Python环境，将your_env_name改为自己的环境名：

```sh
conda create --name your_env_name python=3.8
```

当命令行显示如下信息表示安装完成：

```sh
done
#
# To activate this environment, use
#
#     $ conda activate test
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

**四、编辑器的安装**

在安装好Python的包管理软件后，需要为编写Python的环境再安装一个编辑器，也可以直接使用Anaconda中的Spyder作为编辑器。

通常有两种选择：`VS Code` 与 `PyCharm`。

其中 `VS Code` 只是单纯的文本编辑器，通过安装各类插件来丰富其功能。

而 `Pycharm` 则是一种Python IDE（Integrated Development Environment，集成开发环境），可以替代Anaconda的作用。

### Visual Studio Code + Anaconda

Visual Studio Code（简称“VS Code”  ）是Microsoft开发的一个运行于 Mac OS X、Windows和 Linux 之上的，针对于编写现代Web和云应用的跨平台**源代码编辑器**

VS Code官网下载链接：https://code.visualstudio.com/

安装完 `VS Code` 后打开进入，按下`shift`+`ctrl`+`X`打开扩展安装界面，输入Python进行搜索，选择`Python Extension Pack`安装。

安装好后配置Anaconda，按下`ctrl`+`,`进入设置界面，在上方搜索栏输入`interpreter`搜索。找到 Python: Default Interpreter Path 项设置默认的Python解释器路径，修改为：

```sh
$(Anaconda的安装路径)\envs\(环境名)\python.exe
```

### PyCharm + Anaconda

PyCharm是由JetBrains打造的一款Python IDE，带有一整套可以帮助用户在使用Python语言开发时提高其效率的工具。

PyCharm 官网下载链接（选择 Community 版本，Professional 版本可在通过学生认证后下载）：https://www.jetbrains.com/pycharm/download/#section=windows

安装后双击打开 PyCharm -- New Project -- Pure Python -- Python Interpreter: ... -- Previsouly configured interpreter -- Interpreter 项修改为对应的Python解释器路径：

```sh
$(Anaconda的安装路径)\envs\(环境名)\python.exe
```

再点击 create 即可，项目路径可自由修改。

## Python 中的变量与数据结构

### 数字型变量

要声明一个整型变量只需要像下面一样：

```python
a = 12
```

在Python中可以不指定变量类型，而是由字面量来确定，但使用Python变量前必须给它赋值。故可用下列代码声明一个浮点型变量：

```python
b = 3.1415
c = 1e-3 # Python 同时还支持科学计数法
```

### 运算符号

```python
>>> 2 + 2
4
>>> 1 / 2
0.5
>>> 1 / 1
1.0
>>> 1 // 1
1
>>> 5.0 // 2.4
2.0
>>> 1 % 2
1
>>> 3 ** 2
9
```

### 列表、元组与字典

在Python中，最基本的数据结构为序列（sequence）。序列中的每个元素都有编号，即其位置或索引，其中第一个元素的索引为0，第二个元素的索引为1，依此类推。

Python内置了多种序列，列表和元组便是其中之二。列表和元组的主要不同在于，列表是可以修改的，而元组不可以。

```python
>>> edward = ['Edward Gumby', 42]
['Edward Gumby', 42]
>>> database = [['John Smith', 50], edward]
[['John Smith', 50], ['Edward Gumby', 42]]
```

#### 通用的序列操作

有几种操作适用于所有序列，包括索引、切片、相加、相乘和成员资格检查。另外，Python还提供了一些内置函数，可用于确定序列的长度以及找出序列中最大和最小的元素。

> 索引

```python
>>> greeting = "Hello"
>>> greeting[0]
'H'
>>> greeting[-1]
'o'
```

> 切片

除使用索引来访问单个元素外，还可使用切片（slicing）来访问特定范围内的元素。

```python
>>> tag = '<a href="http://www.python.org">Python web site</a>'
>>> tag[9:30]
'http://www.python.org'
>>> tag[32:-4]
'Python web site'
>>> numbers = [1, 2, 3, 4, 5, 6]
>>> numbers[3:]
[4, 5, 6]
>>> numbers[:2]
[1, 2]
```

> 序列相加

```python
>>> [1, 2, 3] + [3, 4, 5]
[1, 2, 3, 3, 4, 5]
>>> "Hello" + "World"
"Hello World"
```

> 乘法

将序列与数x相乘时，将重复这个序列x次来创建一个新序列：

```python
>>> 'python' * 5
'pythonpythonpythonpythonpython'
>>> [42] * 10
[42, 42, 42, 42, 42, 42, 42, 42, 42, 42]
```

> 成员资格

要检查特定的值是否包含在序列中，可使用运算符in：

```python
>>> permissions = 'rw'
>>> 'w' in permissions
True
>>> 'x' in permissions
False
>>> users = ['mlh', 'foo', 'bar']
>>> 'mlh' in users
True
```

> 长度、最小值和最大值

内置函数len、min和max很有用，其中函数len返回序列包含的元素个数，而min和max分别返回序列中最小和最大的元素：

```python
>>> numbers = [100, 34, 678]
>>> len(numbers)
3
>>> max(numbers)
678
>>> min(numbers)
34
```

#### 列表

函数`list()`，可用于创建列表，该函数将输入的参数转化为列表：

```python
>>> list('Hello')
['H', 'e', 'l', 'l', 'o']
```

**列表方法**

方法是与**对象**联系紧密的函数，通常可像下面这样调用方法：

```python
object.method(arguments)
```

> append() 将对象附加到列表末尾

```python
>>> lst = [1, 2, 3]
>>> lst.append(4)
>>> lst
[1, 2, 3, 4]
```

> clear() 清空列表

```python
>>> lst = [1, 2, 3]
>>> lst.clear()
>>> lst
[]
```

> copy() 复制列表

```python
>>> a = [1, 2, 3]
>>> b = a.copy()
>>> b[1] = 4
>>> a 
[1, 2, 3]
>>> b
[1, 4, 3]
```

> count() 计算指定元素在列表中出现的次数

```python
>>> x = [[1, 2], 1, 1, [2, 1, [1, 2]]]
>> x.count(1)
2
>>> x.count([1, 2])
1
```

> extend() 扩展列表

```python
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> a.extend(b)
>>> a
[1, 2, 3, 4, 5, 6]
```

> index() 查找指定值第一次出现的索引

```python
>>> knights = ['we', 'are', 'the', 'knights']
>>> knights.index('we')
0
>>> knights.index('who')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'who' is not in list
```

> pop() 删除元素

```python
>>> x = [1, 2, 3]
>>> x.pop()
3
>>> x
[1, 2]
>>> x.pop(0)
1
>>> x
[2]
```

> reverse() 反序列表

```python
>>> x = [1, 2, 3]
>>> x.reverse()
>>> x
[3, 2, 1]
```

> sort() 排序

```python
>>> x = [4, 6, 2, 1, 7, 9]
>>> x.sort()
>>> x
[1, 2, 4, 6, 7, 9]
```

#### 元组

与列表一样，元组也是序列，唯一的差别在于元组是不能修改的。

```python
>>> 1, 2, 3
(1, 2, 3)
>>> (1, 2, 3)
(1, 2, 3)
>>> 3 * (42,)
(42, 42, 42)
>>> tuple('abc')
('a', 'b', 'c')
```

#### 字典

字典是通过名字来引用值的数据结构,并且把这种数据结构称为映射,字典中的值没有特殊的顺序,都存储在一个特定的键(key)下,键可以是数字、字符串甚至元组。

```python
phonebook = {'Alice':'2341', 'Beth':'9102', 'Cecil':'3258'}
people = {  
 'Alice': { 
 'phone': '2341', 
 'addr': 'Foo drive 23' 
   }, 
   'Beth': { 
 'phone': '9102', 
 'addr': 'Bar street 42' 
   }
}
```

> fromkeys

```python
>>> {}.fromkeys(['name', 'age'])
{'age':None, 'name':None}
```

> get

```python
>>> d = {}
>>> d['name']
Traceback (most recent call last): 
  File "<stdin>", line 1, in ? 
KeyError: 'name'
>>> d.get('name')
None
>>> d.get('name', 'N/A')
'N/A'
```

> items

```python
>>> d = {'title':'Python Web', 'url':'http://www.python.org'}
>>> d.items()
dict_items([('url', 'http://www.python.org'), ('title', 'Python Web')])
```

> keys

```python
>>> d = {'title':'Python Web', 'url':'http://www.python.org'}
>>> d.keys()
dict_keys(['title', 'url'])
```

> setdefault

```python
>>> d = {}
>>> d.setdefault('name', 'N/A')
'N/A'
>> d
{'name': 'N/A'}
```

> values

```python
>>> d = {'title':'Python Web', 'url':'http://www.python.org'}
>>> d.values()
dict_values([1, 2, 3, 1])
```

#### 字符串

> 设置字符串的格式

```python
>>> "{}, {} and {}".format("first", "second", "third") 
'first, second and third' 
>>> "{0}, {1} and {2}".format("first", "second", "third") 
'first, second and third
>>> "{3} {0} {2} {1} {3} {0}".format("be", "not", "or", "to") 
'to be or not to b
# 使用命名子段
>>> from math import pi 
>>> "{name} is approximately {value:.2f}.".format(value=pi, name="π") 
'π is approximately 3.14
# 格式化字符串
>>> "{pi:10.2f}".format(pi=pi) 
'      3.14'
```

> find

方法 find 在字符串中查找子串。如果找到，就返回子串的第一个字符的索引，否则返回-1。 
```python
>>> 'With a moo-moo here, and a moo-moo there'.find('moo') 
7 
>>> title = "Monty Python's Flying Circus" 
>>> title.find('Monty') 
0 
>>> title.find('Zirquss')
-1
```

> join

```python
>>> seq = ['1', '2', '3', '4', '5'] 
>>> '+'.join(seq) # 合并一个`字符串`列表 
'1+2+3+4+5' 
>>> dirs = '', 'usr', 'bin', 'e
```

> split

其作用与join相反，用于将字符串拆分为序列。

```python
>>> '1+2+3+4+5'.split('+') 
['1', '2', '3', '4', '5'] 
>>> '/usr/bin/env'.split('/') 
['', 'usr', 'bin', 'env'] 
>>> 'Using the default'.split() 
['Using', 'the', 'default'] 
```

### 程序结构

#### 分支结构

用作布尔表达式时，以下的值都被解释器视为假：

```python
False None 0 "" () [] {}
```

> if 语句

```python
name = input('What is your name?')
if name.endswith('Gumby'):
    print('Hello, Mr.Gumby')
else:
    print('Hello, stranger')
```

这就是 if 语句，让你能够有条件地执行代码。这意味着如果条件（if和冒号之间的表达式）为前面定义的真，就执行后续代码。

> elif 子句

```python
num = int(input('Enter a number: ')) 
if num > 0:  
    print('The number is positive') 
elif num < 0: 
    print('The number is negative') 
else: 
 	print('The number is zero')
```

![image-20210822102509833](C:\Users\fetchniche\AppData\Roaming\Typora\typora-user-images\image-20210822102509833.png)

#### 循环结构

> while 循环

```python
x = 1 
while x <= 100:  
   print(x) 
   x += 1
```

> for 循环

```python
words = ['this', 'is', 'an', 'ex', 'parrot'] 
for word in words:  
   print(word) 
```

下面的程序打印数1～100： 

```python
for number in range(1,101):  
   print(number)
```

> 迭代字典

```python
d = {'x': 1, 'y': 2, 'z': 3} 
for key in d:  
   print(key, 'corresponds to', d[key])
```

> 跳出循环

```python
from math import sqrt 
for n in range(99, 0, -1): 
   	root = sqrt(n) 
   	if root == int(root): 
 		print(n) 
 		break
```

### 函数

函数犹如小型程序，用来执行特定的任务。

```python
>>> 2 ** 3
8
>>> pow(2, 3)
8
```

像`pow(2, 3)`这样使用函数就称为调用函数：你可以向它提供实参（这里是2，3），而它返回一个值。因此它也可以理解为一个数值。

```python
>>> 10 + pow(2, 3 * 5) / 3.0
10932.666666666666
>>> abs(-10)
10
>>> round(2/3)
1.0
```

> 函数定义

```python
def fibs(num): 
	result = [0, 1]  
	for i in range(num-2): 
  		result.append(result[-2] + result[-1]) 
 	return result
```

> 默认参数

```python
def resize(x, scale = 2)
	return x*scale
```

### 序列解包与参数收集

> 序列解包

```python
>>> x, y, z = 1, 2, 3 
>>> print(x, y, z) 
1 2 3
```

这样可以实现在一个语句给多个变量赋值，使用这种方式还可交换多个变量的值：

```python
>>> x, y = y, x 
>>> print(x, y, z) 
2 1 3
```



### Python 中的注释与文档

### 面向对象

用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。

> 创建类

```python
class Employee:
    empCount = 0 # 所有对象共用
    
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.empCount += 1
   	def getCount(self):
        return Employee.empCount
```

> 创建类的实例

```python
>>> John = Empolyee('John', 20000)
>>> John.getCount()
1
```

> 继承

```python
class Filter:  
   	def __init__(self): 
    	self.blocked = [] 
   	def filter(self, sequence): 
 		return [x for x in sequence if x not in self.blocked] 
class SPAMFilter(Filter): # SPAMFilter是Filter的子类 
   	def __init__(self): # 重写超类Filter的方法init 
 	self.blocked = ['SPAM']
if __name__ == '__main__':
    f = Filter()
    sf = SPAMFilter()
    print(f.(['SPAM', 'FETCH', 'DMM']))
    # ['SPAM', 'FETCH', 'DMM']
   	print(sf.(['SPAM', 'FETCH', 'DMM']))
    # ['FETCH', 'DMM']
```



