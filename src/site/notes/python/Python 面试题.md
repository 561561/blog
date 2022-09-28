---
{"dg-publish":true,"dg-permalink":"python/interview_questions","permalink":"/python/interview_questions/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Python 面试题（110 道）


## 1. 一行代码实现 0-100 的和


```python
sum(range(1, 101))
```


## 2. 如何在函数内部修改全局变量


`global` 关键字

[[python/全局变量与局部变量|全局变量与局部变量]]

```python
str = 'global'

def func1():
	global str
	str = 'local'
	return str

print(func1())
print(str)
```


## 3. 列出 5 个 Python 标准库


os：提供了不少与操作系统相关联的函数
sys: 通常用于命令行参数
re: 正则匹配
math: 数学运算
datetime:处理日期时间


## 4. 字典如何删除键和合并两个字典


```python
dic = {'name': '张三', 'age': 19}
del dic['name']

dic2 = {'name': '李四'}
dic.update(dic2)
```


## 5. 谈下 Python 的 GIL


[[python/GIL|GIL]]


## 6. Python 列表去重


> [列表去重]([Python 列表去重的4种方式及性能对比 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/364610029))

```python
from random import randrange

duplicates = [randrange(100) for _ in range(1000000)]
```

```python
# 1. 遍历数组去重
unique_1 = []
for element in duplicates:
    if element not in unique_1:
        unique_1.append(element)
```

有序

```python
# 改为用集合存储
unique_2 = set()
for element in duplicates:
    if element not in unique_2:
        unique_2.add(element)
unique_2 = list(unique_2)
```

无序

```python
# 2. 将数组转化为集合，再转化为数组
unique_3 = list(set(duplicates))
```

无序

```python
# 3. (Python 3.6 以上)保留原有数组顺序去重
unique_4 = list(dict.fromkeys(duplicates))
```

有序

```python
# python 3.6 以下
from collections import OrderedDict

unique_5 = list(OrderedDict.fromkeys(duplicates))
```


## 7. func(\*args, \*\*kwargs)中的 \*args, \*\*kwargs 什么意思


[\*args, \*\*kwargs](https://zhuanlan.zhihu.com/p/50804195)

`*args` arguments 可变数量参数列表
`**kwargs` keyword arguments 不定长度键值对


## 8. python 2 和 python 3 的 range() 的区别


Python 2 返回列表，Python 3 返回迭代器


## 9、一句话解释什么样的语言能够用装饰器?


函数可以作为参数传递的语言，可以使用[[python/装饰器|装饰器]]


## 10、Python 内建数据类型有哪些


整型--int

布尔型--bool

字符串--str

列表--list

元组--tuple

字典--dict


## 11、简述面向对象中 `__new__` 和 `__init__` 的区别


[[__new__、__init__|__new__、__init__]]


## 12、with方法打开处理文件帮我我们做了什么？


使用 `with open()`的方式打开文件进行操作，如果在读或写的过程中发生了异常，with 会帮我们close文件。如果用 `try ... except ... finally` 方式可以实现同样的效果，在 `finally` 中关闭文件。但这样写太麻烦了，不如 `with open()` 方便。


## 13、列表[1,2,3,4,5],请使用map()函数输出[1,4,9,16,25]，并使用列表推导式提取出大于10的数，最终输出[16,25]


```python
lis = [1, 2, 3, 4, 5]

def fn(x):
    return x ** 2

res = map(fn, lis)
res = [i for i in res if i > 10]
  
print(res)
```


## 14、Python 中生成随机整数、随机小数、0-1之间小数方法



```python
import random

# 生成 1 - 10 之间随机整数，包括 1,10
random.randint(1, 10)
# 生成 0 - 9 之间随机小数
random.uniform(0,9)
# 生成 0 - 1 之间随机小数
random.randint()
```


## 15、避免转义给字符串加哪个字母表示原始字符串？


`r`


## 16、`<div class="nam">中国</div>` 用正则匹配出标签里面的内容（“中国”），其中class的类名是不确定的


```python
import re


str = r'<div class="nam">中国</div>'
res = re.findall(r'<div class=".*">(.*?)</div>', str)
print(res)
# 输出
# ['中国']
```


## 17、Python 中断言方法举例


```python
>>> assert True     # 条件为 true 正常执行  
>>> assert False    # 条件为 false 触发异常  
Traceback (most recent call last):  
  File "<stdin>", line 1, in <module>  
AssertionError  
>>> assert 1==1    # 条件为 true 正常执行  
>>> assert 1==2    # 条件为 false 触发异常  
Traceback (most recent call last):  
  File "<stdin>", line 1, in <module>  
AssertionError  
  
>>> assert 1==2, '1 不等于 2'  
Traceback (most recent call last):  
  File "<stdin>", line 1, in <module>  
AssertionError: 1 不等于 2  
>>>
```


## 18、数据表 `student` 有 `id`， `name`， `score`， `city` 字段，其中 `name` 中的名字有重复，需要消除重复行，请写出 `sql` 语句


```sql
select distinct name from student
```


## 19、10个 Linux 常用命令


```
ls cd touch mkdir rm mv pwd cp cat which
```


## 20、Python 2 和 Python 3 的区别


[[python/Python2和Python3的区别|Python2和Python3的区别]]


## 21、列出python中可变数据类型和不可变数据类型，并简述原理


不可变数据类型：数值型、字符串 string 和元组 tuple

不允许变量的值发生变化，如果改变了变量的值，相当于是新建了一个对象，而对于相同的值的对象，在内存中则只有一个对象（一个地址），如下图用 id() 方法可以打印对象的 id

```python
>>> a = 1
>>> b = 1
>>> id(a)
1751018512
>>> id(b)
1751018512
>>> a = 2
>>> id(a)
1751018544
```

可变数据类型：列表 list 和字典 dict

允许变量的值发生变化，即如果对变量进行append、+=等这种操作后，只是改变了变量的值，而不会新建一个对象，变量引用的对象的地址也不会变化，不过对于相同的值的不同对象，在内存中则会存在不同的对象，即每个对象都有自己的地址，相当于内存中对于同值的对象保存了多份，这里不存在引用计数，是实实在在的对象。

```python
>>> a = [1, 2]
>>> b = [1, 2]
>>> id(a)
1527966899592
>>> id(b)
1527966899976
```

## 22、s = "ajldjlajfdljfddd"，去重并从小到大排序输出"adfjl"


```python
s = 'ajldjlajfdljfddd'
s = list(set(s))
s.sort()
res = ''.join(s)
```


## 23、用 lambda 函数实现两个数相乘


```python
>>> mul = lambda a, b: a * b
>>> mul(2, 3)
6
```


## 24、字典根据键从小到大排序


```python
numbers={'first': 1, 'second': 2, 'third': 3, 'Fourth': 4}
```

根据字典的键排序

```python
>>> sorted(numbers)
['Fourth', 'first', 'second', 'third']
```

根据字典的值排序

```python
>>> sorted(numbers.values())
[1, 2, 3, 4]
```

根据字典的值对字典的键进行排序

```python
>>> sorted(numbers, key=numbers.__getitem__)
# In order of sorted values: [1, 2, 3, 4]
['first', 'second', 'third', 'Fourth']
```

根据字典的键对字典的值进行排序

```python
>>> [value for (key, value) in sorted(numbers.items())]
[4, 1, 2, 3]
# In order of sorted keys: ['Fourth', 'first', 'second', 'third']
```

无视大小写

```python
>>> sorted(numbers, key=str.lower)
['first', 'Fourth', 'second', 'third']
```

[如何根据字典的键或值来排序_冯西的技术博客的博客-程序员宝宝_字典根据键从小到大排序 - 程序员宝宝 (cxybb.com)](https://www.cxybb.com/article/xibeichengf/52015355#:~:text=%E5%A6%82%E6%9E%9C%E6%88%91%E4%BB%AC%E6%83%B3%E6%A0%B9%E6%8D%AE%E5%AD%97%E5%85%B8%E7%9A%84%E9%94%AE%E6%9D%A5%E8%BF%9B%E8%A1%8C%E6%8E%92%E5%BA%8F%EF%BC%8C%E6%9C%80%E7%AE%80%E5%8D%95%E7%9A%84%E6%96%B9%E6%B3%95%E6%98%AF%E4%BD%BF%E7%94%A8Python%E7%9A%84%E5%86%85%E7%BD%AE%E5%87%BD%E6%95%B0sorted,%28%29%EF%BC%8C%E8%AF%A5%E5%87%BD%E6%95%B0%E6%8E%A5%E6%94%B6%E4%B8%80%E4%B8%AAiterable%EF%BC%8C%E5%B9%B6%E8%BF%94%E5%9B%9E%E5%B7%B2%E6%8E%92%E5%A5%BD%E5%BA%8F%E7%9A%84%E5%88%97%E8%A1%A8%EF%BC%88%E9%BB%98%E8%AE%A4%E6%83%85%E5%86%B5%E4%B8%8B%E6%98%AF%E4%BB%8E%E5%B0%8F%E5%88%B0%E5%A4%A7%E6%8E%92%E5%BA%8F%EF%BC%89%E3%80%82)


## 25、利用 collections 库的 Counter 方法统计字符串每个单词出现的次数"kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"


```python
from collections import Counter

a = "kjalfj;ldsjafl;hdsllfdhg;lahfbl;hl;ahlf;h"
res = Counter(a)
# Counter({'l': 9, ';': 6, 'h': 6, 'f': 5, 'a': 4, 'j': 3, 'd': 3, 's': 2, 'k': 1, 'g': 1, 'b': 1})
```


## 26、字符串 a = "not 404 found 张三 99 深圳"，每个词中间是空格，用正则过滤掉英文和数字，最终输出"张三 深圳"


```python
import re

a = "not 404 found 张三 99 深圳"
res = re.split('[0-9a-z ]+', a)
s = ' '.join(res).strip()
```

[[python/Python Re 模块|Python Re 模块]]

[[computerbasic/正则表达式|正则表达式]]


## 27、filter 方法求出列表所有奇数并构造新列表，`a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`


```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

def fn(a):
    return a % 2 == 1

newlist = list(filter(fn, a))
```


## 28、列表推导式求列表所有奇数并构造新列表，`a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`


```python
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

newlist = [i for i in a if i % 2 == 1]
```


## 29、re.complie 作用


`re.compile` 是将正则表达式编译成一个对象，加快速度，并重复使用


## 30、a=（1，）b=(1)，c=("1") 分别是什么类型的数据？


```python
>>> a = (1,)
>>> b = (1)
>>> c = ("1")
>>> type(a)
<class 'tuple'>
>>> type(b)
<class 'int'>
>>> type(c)
<class 'str'>
```


## 31、两个列表 `[1,5,7,9]` 和 `[2,2,6,8]` 合并为 `[1,2,2,3,6,7,8,9]`


```python
>>> l1 = [1, 5, 7, 9]
>>> l2 = [2, 2, 6, 8]
>>> l1.extend(l2)
>>> l1
[1, 5, 7, 9, 2, 2, 6, 8]
>>> l1.sort()
>>> l1
[1, 2, 2, 5, 6, 7, 8, 9]
```


## 32、用 python 删除文件和用 linux 命令删除文件方法


python: `os.remove('文件名')`

linux: `rm 文件名`


## 33、datetime模块打印当前时间戳


```python
import datetime

a = datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
```


## 34、数据库优化查询方法


## 35、统计图绘制的开源库


pyecharts

matplotlib


## 36、写一段自定义异常代码


```python
try:
    for i in range(5):
        if i > 2:
            raise Exception('数字大于 2 了')
except Exception as e:
    print(e)
```


## 37、正则表达式匹配中，`(.*)` 和 `(.*?)` 匹配区别？


[[computerbasic/正则表达式|正则表达式]]


## 38、简述 Django 的 orm


ORM，即 Object-Relational Mapping（对象关系映射），它的作用是在关系型数据库和业务实体对象之间作一个映射，这样，我们在具体的操作业务对象的时候，就不需要再去和复杂的SQL语句打交道，只需简单的操作对象的属性和方法。


## 39、`[[1, 2], [3, 4], [5, 6]]` 一行代码展开该列表，得到 `[1, 2, 3, 4, 5, 6]`


```python
a = [[1, 2], [3, 4], [5, 6]]
b = [j for i in a for j in i]
```


## 40、`x="abc",y="def",z=["d","e","f"]`, 分别求出`x.join(y)`和`x.join(z)`返回的结果


```pyhton
x = 'abc'
y = 'def'
z = ["d", "e", "f"]

m = x.join(y)
y = x.join(z)

# m 'dabceabcf'
# n 'dabceabcf'
```


## 41、举例说明异常模块中try except else finally的相关意义


`try...except...else` 没有捕获到异常，执行 `else` 语句

`try...except...finally` 不管是否捕获到异常，都执行 `finally` 语句


## 42、python中交换两个数值


```python
a, b = 3, 4
a, b = b, a
```


## 43、举例说明 `zip()` 函数用法


`zip()` 函数用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的列表。

如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 * 号操作符，可以将元组解压为列表。

```python
>>> a = [1,2,3]  
>>> b = [4,5,6]  
>>> c = [4,5,6,7,8]  
>>> zipped = zip(a,b)     # 返回一个对象  
>>> zipped  
<zip object at 0x103abc288>  
>>> list(zipped)  # list() 转换为列表  
[(1, 4), (2, 5), (3, 6)]  
>>> list(zip(a,c))              # 元素个数与最短的列表一致  
[(1, 4), (2, 5), (3, 6)]  
  
>>> a1, a2 = zip(*zip(a,b))          # 与 zip 相反，zip(*) 可理解为解压，返回二维矩阵式  
>>> list(a1)  
[1, 2, 3]  
>>> list(a2)  
[4, 5, 6]  
>>>
```


## 44、a="张明 98分"，用re.sub，将98替换为100


```python
import re

a = '张明 98分'
res = re.sub(r'\d+', '100', a)
print(res)

# 输出
# 张明 100分
```


## 45、写 5 条常用 sql 语句


## 46、`a="hello"` 和 `b="你好"` 编码成 bytes 类型


```python
a = 'hello'
b = '你好'

a = a.encode()
b = b.encode()

print(a)
print(b)

print(type(a))
print(type(b))

# 输出
# b'hello' 
# b'\xe4\xbd\xa0\xe5\xa5\xbd' 
# <class 'bytes'> 
# <class 'bytes'>
```


## 47、`[1, 2, 3] + [4, 5, 6]` 的结果是多少？


两个列表相加，等价于 extend

结果是 `[1, 2, 3, 4, 5, 6]`


## 48、提高 python 运行效率的方法


使用生成器，因为可以节约大量内存

循环代码优化，避免过多重复代码的执行

核心模块用 Cython PyPy 等，提高效率

多进程、多线程、协程

多个 `if elif` 条件判断，可以把最有可能先发生的条件放到前面写，这样可以减少程序判断的次数，提高效率


## 49、简述 mysql 和 redis 的区别


redis： 内存型非关系数据库，数据保存在内存中，速度快

mysql：关系型数据库，数据保存在磁盘中，检索的话，会有一定的 IO 操作，访问速度相对慢


## 50、遇到 bug 如何处理


## 51、正则匹配，匹配日期 2018-03-20


```python
import re

url = 'https://sycm.taobao.com/bda/tradinganaly/overview/get_summary.json?dateRange=2018-03-20%7C2018-03-20&dateType=recent1&device=1&token=ff25b109b&_=1521595613462'

res = re.findall(r'(\d{4})-(\d{2})-(\d{2})', url)
print(res)

# 输出
# [('2018', '03', '20'), ('2018', '03', '20')]
```


## 52、