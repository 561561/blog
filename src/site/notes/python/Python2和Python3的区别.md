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


