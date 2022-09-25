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


