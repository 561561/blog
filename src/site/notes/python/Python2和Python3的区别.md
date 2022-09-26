---
{"dg-publish":true,"dg-permalink":"python/python23dif","permalink":"/python/python23dif/","dgHomeLink":true,"dgPassFrontmatter":false}
---



# Python 2 和 Python 3 的区别


## 1、Print 函数


```python
# python 2 print 语句
print 'hello world'
# python 3 print 函数
print('hello world')
```


## 2、 Unicode


Python 2 ASCII 编码
Python 3 Unicode 编码

[[computerbasic/编码|编码]]


## 3、除法


Python 2 中 `/` 整数相除的结果是一个整数，把小数部分完全忽略掉，浮点数除法会保留小数点的部分得到一个浮点数的结果。

Python 3 中 `/` 整数相除也可得到浮点数。


```python
# python2 
>>> 1 / 2
0
>>> 1.0 / 2.0
0.5

# python3
>>> 1/2
0.5
```

`//` 向下取整，Python 2 和 Python 3 中一致。


## 4、range


1）Python3中不再使用xrange方法，只有range方法

2）range在Python2中返回列表，而在Python3中返回range可迭代对象

Python2：

```python
>>> a=range(10) 
>>> print(a) 
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 
```

Python3:

```python
>>> a=range(10) 
>>> print(a) 
range(0, 10) 
>>> print(list(a)) 
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 
```



## 5、不等式运算符


Python2中不等于有两种写法 `!=` 和 `<>`

Python3中去掉了 `<>`, 只有 `!=` 一种写法


## 6、数据类型


1）在 Python2 中 long 是比 int 取值范围更大的整数，Python3 中取消了 long 类型，int 的取值范围扩大到之前的 long 类型范围

2）新增了 bytes 类型，对应于 Python2 版本的八位串，定义一个 bytes 字面量的方法如下：

```python
>>> b=b'china' 
>>> type(b) 
# python3
<class 'bytes'> 
# python2
<type 'str'>
```

3）str 对象和 bytes 对象可以使用 .encode() (str -> bytes) 或 .decode() (bytes -> str)方法相互转化

```python
>>> s=b.decode() 
>>> s 
'china' 
>>> b1=s.encode() 
>>> b1 
b'china' 
```

4）dict 的 .keys()、.items 和 .values() 方法返回迭代器，只能通过循环取值，不能通过索引取值，而之前的 iterkeys() 等函数都被废弃。同时去掉的还有 dict.has_key()，可以用 in 来代替

```python
dict={'a':1, 'b':2, 'c':3} 
for key in dict: 
    print(key) 
print('c' in dict) 
```


