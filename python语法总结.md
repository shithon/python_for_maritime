# python基本语法总结知识清单（简化版）

**程序 = 算法 + 数据结构**

## 基本语法

- 常量，变量，变量的命名规范
  变量的命名规范：一般企业进去后有个手册规范，不能随便乱取变量名，python通常用下划线连连接（也即“下划线命名法”--c语言采用的也是这个命名方法），当然还有来自perl语言的驼峰命名法比如studentScoreTotal = 200；还有微软自创的“匈牙利命名法”，但是不一般不常用，基本就是下划线命名为主。
  变量的命名不能有内置的关键词，比如while；有大小写区分，Name跟name是两个不同的变量名；不能数字开头，001name的命名会报错；命名要直接，也即“顾名思义”，不要太含糊或不明所以--比如sum表示求和，userName就是表示用户名等等;不能用 a b c或者1 2 3来命名，这是大忌。

- 字符串
  单引号,双引号的区别；可以切片（通过index来切片）；

```
shipInfo ="the ship's age is 15 years old."
print(shipInfo) 

shipInfo ='the ship\'s age is 15 years old.'
```

```python
# 一些常用的方法
strip; lstrip; rstrip ==>取出空格
startswith; endswith ==>判断是否以某个字符串开始或者结尾

#格式化
shipName = "MARITIME BRAVE"
shipInfo = f"hello, the vessel is {shipName}"
print(shipInfo)

#分隔符
shipList = "Bulker,Container,Tanker"
shipList.split(",")
==>['Bulker','Container','Tanker']

#连接符
print（'hello!' + shipName）
print(shipName * 2)


#特殊字符
print('hello!\nmaritime brave!')
print(r'hello\nmaritime brave!')
说明：前面加上r就是表示原始字符串，不会转义。也即结果是-->hello\nmaritime brave!
```

- 数据类型：
  int-整数；float-浮点数；string-字符串（可以切片）；boolean-布尔型

- 运算

算术运算：加减乘除,求余求整，以及四舍五入（round方法）当然对于数学和数字模块，可参见math-数学函数

比较运算：大于 等于 不等于

赋值运算： +=；-=；*=；/=；%=；**=；//=

位运算：& ; |;  ~;  ^;  <<;  >>

逻辑运算：and or not

成员运算： in  not in

身份运算： is  isnot

运算优先级

```python
int(x [,base])
将x转换为一个整数

float(x)
将x转换到一个浮点数

complex(real [,imag])
创建一个复数

str(x)
将对象 x 转换为字符串

repr(x)
将对象 x 转换为表达式字符串

eval(str)
用来计算在字符串中的有效Python表达式,并返回一个对象

tuple(s)
将序列 s 转换为一个元组

list(s)
将序列 s 转换为一个列表

set(s)
转换为可变集合

dict(d)
创建一个字典。d 必须是一个 (key, value)元组序列。

frozenset(s)
转换为不可变集合

chr(x)
将一个整数转换为一个字符

ord(x)
将一个字符转换为它的整数值

hex(x)
将一个整数转换为一个十六进制字符串

oct(x)
将一个整数转换为一个八进制字符串
```

- print函数
  print(objects, sep=' ', end='\n', file=sys.stdout, flush=False)
  objects -- 复数，表示可以一次输出多个对象。输出多个对象时，需要用 , 分隔。
  sep -- 用来间隔多个对象，默认值是一个空格。
  end -- 用来设定以什么结尾。默认值是换行符 \n，我们可以换成其他字符串。
  file -- 要写入的文件对象。
  flush -- 输出是否被缓存通常决定于 file，但如果 flush 关键字参数为 True，流会被强制刷新

- 格式化

1.%格式化；2.format格式化；3.f-string格式化

```python
# %格式化
print("maritime brave is a %s and she built in %d" %('bulker carrier',2022))
%s-表示字符串；%d-表示整数；%f-表示浮点数，其他参考表格

# format格式化
format 格式化函数:格式化字符串的函数 str.format()
"{} {}".format('hello', 'maritime brave')--这是不指定
"{0} {1}".format("hello", "maritime brave")--这是指定的
"{1} {0} {1}".format("hello", "maritime brave")

print("{} is a {} year-old bulker carrier".format('maritime brave', 10))

print("name：{name}, website {url}".format(name="iforyuan", url="www.iforyuan.top"))

当然也可以通过字典和列表来设置参数
site = {"name": "iforyuan", "url": "www.iforyuan.top"}
print("网站名：{name}, 地址 {url}".format(site))

my_list = ['iforyuan', 'www.iforyuan.top']
print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))

#python3.6以上才支持的
shipName = 'maritime brave'
age = 10
print(f"{shipName} is a {age} year-old bulker carrier")
```

## 数据结构

- 列表

```python
# 主要是增删改查
#(1)查询
shipList = ['bulker','container','tanker','roro','cruise']
shipList[0]
==>'bulker'
shipList.index('container')
==>1

shipList.count('container') #查看列表中这个值有多少个

# 内置函数len()
len(shipList)


#（2）新增-主要方法有append\insert\extend

shipList.append('general cargo') #从尾巴处添加
shipList.insert(1,'roro-passenger')
new_ships = ['live stock','ferry']
shipList.extend(new_ships)

#(3)修改 list[x]=new_item

#(4)删除元素-主要方法pop\remove\clear\del
shipList.remove('roro')
shipList.pop()
del shipList[:] #清除全部的
del shipList[1:3] #清除第二个到第四个元素
shipList.clear()

#(4)反转
shipList.reverse() #改变了shipList
#或者
shipList[::-1] #不改变原来的shipList

#（5）排序
shipList.sort()
sorted(shipList)

#(6)拼接、嵌套
len(shipList)
['container','bulker'] + ['tanker']
['container']*4
container in shipList #True
s = [ship for ship in shipList]

[['bulker','container','tanker'],[100,10,0]]

#(7)内置的函数
len()；max()；min()；list(seq)；list.copy()
```

- 元组

```python
#(1)创建
# 如果是一个元素的时候，后面一定要加一个，
unit_tuple = (1,)
#（2）不允许修改和删除元素
#（3）可与列表互相转换，其他的内置性质跟列表差不多
```

- 字典

```python
#（1）创建
ship_dict = {'name':'maritime brave','type':'bulker','dwt':56800}
ship_dict = dict(name='maritime brave',type='bulker',dwt=56800)
ship_dict = dict[('name','maritime brave'),('type','bulker'),('dwt',56800)]

#(2)查看-dict[key]
#(3)新增-dict[key]=value
#(4)修改-dict[key]=new_value
#(5)删除-pop();del;
pop(key[,default]) #删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值
#(6)内置的函数
dict.fromkeys() #创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值
dict.get(key,default=None) #返回指定键的值，如果键不在字典中返回 default 设置的默认值
dict.items() #以列表返回一个视图对象
dict.keys() #返回一个视图对象
dict.values() #返回一个视图对象
dict.setdefault(key, default=None) #如果键不存在于字典中，将会添加键并将值设为default
dict.update(dict2) #把字典dict2的键/值对更新到dict里
```

- 集合

```python
#(1)添加元素
ship_set = set()
ship_set.add('bulker')

ship_set.update({'container'}) #update后面可以接列表、元组、字典、集合

#（2）删除元素-remove\discard,discard不会报错\pop-随机删除\clear

#(3)不能修改

#（4）union会提出重复的元素

#（5）差集difference
ship_set1={'container','bulker'}
ship_set2={'bulker','tanker'}
ship_set1.difference(ship_set2) #返回的是第一个集合的元素，这个元素在第二个集合里面是没有的

#（6）求交集intersection\intersection_update\&
ship_set1.intersection(ship_set2)

#(7)不重复的元素symmetric_difference

#(8)判断 isdisjoint-是否有相同的元素；issubset-是否是子集
```

## 迭代器和生成器

**迭代器Iterator** 区别于 **可迭代对象Iterable**

- 凡是可作用于`for`循环的对象都是`Iterable`类型；
- 凡是可作用于`next()`函数的对象都是`Iterator`类型，它们表示一个惰性计算的序列；
- 集合数据类型如`list`、`dict`、`str`等是`Iterable`但不是`Iterator`，不过可以通过`iter()`函数获得一个`Iterator`对象

非常全面的参考资料链接：[python 生成器和迭代器有这篇就够了 - 战争热诚 - 博客园](https://www.cnblogs.com/wj-1314/p/8490822.html)

## 流程控制

```python
if-else;
for;
while;
break, continue
```

## 解析式

```python
#打印一个九九乘法表

print('\n'.join([' '.join(['%2d *%2d = %2d' % (col, row, col * row) for col in range(1, row + 1)]) for row in range(1, 10)]))
```

## 函数

- **函数的创建、返回和调用**

- **参数**

```python
（1）定义的时候
# 必选参数，这边就是shipName, shipType,也就是调用函数时，必须要指定的参数。
# 可选参数=默认参数，这个也是很多机器学习算法里面会指定一些默认的参数作为模型参数。
def func(shipName, shipType, shipAge=10, dwt=56800):
    pass

（2）调用的时候
#关键字传参
func(shipType='bulker', shipAge=10, shipName='maritime brave')
#位置传参
func('maritime brave', 'bulker')

(3)特殊-可变参数
# *args-按照位置参数的方式传进来，返回的是元组类型
# **kw-按照关键字参数传进来，返回字典类型
def fuc(*args, **kw):
    print(args)
    print(kw)

func('maritime brave',shipType='bulker')

输出结果：
('maritime brave',)
{'shipType': 'bulker'}

------------------------------------------------------------------
（4）定义函数时，必选参数一定要在可选参数前面；可变位置参数一定要在可变关键字参数前面
def func(shipAge=10,shipType): #会报错
def func(**kw,*args)： #会报错

（5）可变位置参数可以放在必选参数前面，但是在调用时，必选参数必须要指定参数名来传入，否则会报错

def demo_func(*args, b):
    print(args)
    print(b)
demo_func(1, 2, 100) #报错
demo_func(1, 2, b=100) #成功输出

（6）可变关键字参数则不一样，可变关键字参数一定得放在最后，下面三个示例中，不管关键字参数后面接位置参数，还是默认参数，还是可变参数，都会报错。
def demo_func(**kw, a)
def demo_func(**kw, a=1)
def demo_func(**kw, *args)

（7）总结一下：
def demo_func(arg1, arg2=10, *args, **kw):
    print("arg1: ", arg1)
    print("arg2: ", arg2)
    print("args: ", args)
    print("kw: ", kw)
demo_func(1,12, 100, 200, d=1000, e=2000)
```

- **匿名函数**

```python
( lambda x, y: x if x < y else y )( 1, 2 )
( lambda x: ( lambda y: ( lambda z: x + y + z  )( 1 ) )( 2 ) )( 3 )
 func = lambda n:1 if n == 0 else n * func(n-1)
```

- **匿名函数和高阶函数的一起使用**

```python
(1)map函数-第一个参数（函数对象）+另外一个参数（序列）
map(lambda x: x*2, [1,2,3,4,5])

（2）filter函数-传入两个参数：1一个是lambda,2一个是序列
filter(lambda x: x < 0, range(-5, 5))

（3）reduce函数
from functools import reduce
reduce(lambda x,y: x+y, [1,2,3,4,5])
```

- **偏函数（partial function）**

固定我们命名的某个函数的功能

```python
def power(x, n):
    s = 1
   while n > 0:
        n = n - 1
        s = s * x
    return s

from functools import partial
power_2 = partial(power, n=2)
这就将n次方固定为求平方
```

- **装饰器**

## 错误异常

异常涵盖

- 1.SyntaxError

- 2.TypeError

- 3.IndexError

- 4.KeyError

- 5.ValueError

- 6.AttributeError

- NameError

- 8.IOError

- 9.StopIteration

- 10.AssertionError

- 11.IndentationError

- 12.ImportError

```python
#example one:try--exacept
try:
    1/0
except ZeroDividionError as e:
    print("abnormal calculation, information is listed as: \n"+str(e))


# example two:try-except-else
try:
    1/0
except ZeroDividionError as e:
    print("abnormal calculation, information is listed as: \n"+str(e))
else:
print("normal running")


# example three:try-except-finally
try:
    1/0
except ZeroDividionError as e:
    print("abnormal calculation, information is listed as: \n"+str(e))
finally:
print("running end!!")
```

## 类和对象

- **创建**

```python
# 一个简单的类


class Bulker:

    def __init__(self, name):
        self.name=name

    def choose(self):
        print(f"we choose a bulker named {self.name}")


#实例化
vessel=Bulker('maritime brave') #传入一个参数

#调用
vessel.name;#查看它的属性，并不是方法，所以不能vessel.name()
vessel.choose()#调用它的方法


# 静态方法 类方法

class Bulker:

    def __init__(self, name):
        self.name=name

    def choose(self):
        print(f"we choose a bulker named {self.name}")
    
    @staticmethod #静态方法，其实是函数， 类似一个定义的普通函数
    def sailing():
        print("the vessel is running")
    
    @classmethod  #这是类的方法，cls=calss的缩写
    def loading(cls,name):
        print(f"vessel {name} is loading cargo at port.")

```



- **私有变量和私有方法、封装**

```python
"""
# 5种写法
_var
var_
__var
__var__
_

"""
（1）解释_var
class Bulker:
    def __init__(self):
        self.name="maritime brave"
        self._age=10

vessel = Bulker()
vessel.name
vessel._age #私有变量也是可以访问，但是一般不会这么去访问的，一般都是供内部使用

（2）解释__var

class Bulker:
    def __init__(self):
        self.name="maritime brave"
        self._age=10
        self.__built=2022
vessel = Bulker()
vessel.__built #会报错，是不能访问的 
#需要vessel._Bulker__built才能访问，具体可以使用dir(vessel)来查看它的属性
```

```python
#封装
class Bulker:
    def __init__(self,name,age):
        self.name = name
        self._age = age

    def is_scrap(self):
        return self._age >= 30 #判断船舶是否要进行拆解了

vessel = Bulker("maritime brave",32)
vessel.is_scrap()


```



- **继承**

```
class 子类（父类）
```



## 包与模块

模块 - 包 - 库（层级从小到大）

- 模块-包-库

.py结尾后缀的python文件就是模块，里面有很多class类（对象），然后对象里面有很多方法（函数）。模块可以导入，直接就是：import+模块名。

导入模块的时候，对下面的理解：

```python
if __name__=="__main__"


生成__pycache__文件
```

```python
__init__.py  #包的初始化
```



- 安装包的方式

（1）pip install;

（2）pipx

（3）setup.py

（4）yum

（5）pipenv
（6）poetry

（7）curl + [pipeline]



**（Loading Update.........）**






