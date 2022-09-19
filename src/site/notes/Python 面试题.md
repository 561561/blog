---
{"dg-publish":true,"permalink":"/python/","tags":"gardenEntry","dgHomeLink":true,"dgPassFrontmatter":false}
---


# 1. 一行代码实现 0-100 的和

```python
sum(range(1, 101))
```

# 2. 如何在函数内部修改全局变量

`global` 关键字

[[全局变量与局部变量|全局变量与局部变量]]

```python
str = 'global'

def func1():
	global str
	str = 'local'
	return str

print(func1())
print(str)
```

# 3. 列出 5 个 Python 标准库

os：提供了不少与操作系统相关联的函数
sys: 通常用于命令行参数
re: 正则匹配
math: 数学运算
datetime:处理日期时间

# 4. 字典如何删除键和合并两个字典

```python
dic = {'name': '张三', 'age': 19}
del dic['name']

dic2 = {'name': '李四'}
dic.update(dic2)
```

# 5. 谈下 Python 的 GIL

[[GIL|GIL]]

# 6. Python 列表去重

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

# 7. func(\*args, \*\*kwargs)中的 \*args, \*\*kwargs 什么意思

[\*args, \*\*kwargs]([Python中的*args和**kwargs - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/50804195))

`*args` arguments 可变数量参数列表
`**kwargs` keyword arguments 不定长度键值对

# 8. python 2 和 python 3 的 range() 的区别

Python 2 返回列表，Python 3 返回迭代器

# 9、一句话解释什么样的语言能够用装饰器?

函数可以作为参数传递的语言，可以使用[[装饰器|装饰器]]
