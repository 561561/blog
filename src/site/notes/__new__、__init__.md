---
{"dg-publish":true,"dg-permalink":"python/new_init","permalink":"/python/new_init/","dgHomeLink":true,"dgPassFrontmatter":false}
---



# `__init__` 和 `__new__` 


`__new__` 

创建实例

参数：至少一个 `cls`

返回：返回实例


`__init__` 

初始化实例

参数：至少一个`self`

返回：不需要返回值

```python
class Person:
    def __new__(cls, *args, **kwargs):
        print("in __new__")
        instance = super().__new__(cls)
        return instance

    def __init__(self, name, age):
        print("in __init__")
        self._name = name
        self._age = age


p = Person("Wang", 33)

# 输出：
# in __new__ 
# in __init__
```

## 单例模式


```python
class Singleton:
    _instance = None
    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)

        return cls._instance
  

s1 = Singleton()
s2 = Singleton()
print(s1)
print(s2)

# 输出
# <__main__.Singleton object at 0x000001AD379134A8> 
# <__main__.Singleton object at 0x000001AD379134A8>
```


## 工厂模式


```python
class Fruit(object):
    def __init__(self):
        pass

    def print_color(self):
        pass
  

class Apple(Fruit):
    def __init__(self):
        pass
  
    def print_color(self):
        print("apple is in red")
  

class Orange(Fruit):
    def __init__(self):
        pass


    def print_color(self):
        print("orange is in orange")
  

class FruitFactory(object):
    fruits = {"apple": Apple, "orange": Orange}

    def __new__(cls, name):
        if name in cls.fruits.keys():
            return cls.fruits[name]()
        else:
            return Fruit()
  

fruit1 = FruitFactory("apple")
fruit2 = FruitFactory("orange")
fruit1.print_color()    
fruit2.print_color()
```


> 参考：[Python面试之理解__new__和__init__的区别 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/35943253)