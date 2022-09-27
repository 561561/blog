---
{"dg-publish":true,"dg-permalink":"python/re","permalink":"/python/re/","dgHomeLink":true,"dgPassFrontmatter":false}
---



# Python Re 模块


>[Python 正则表达式 | 菜鸟教程 (runoob.com)](https://www.runoob.com/python/python-reg-expressions.html)


## re.match


re.match 尝试从字符串的起始位置匹配一个模式

```python
import re 
print(re.match('www', 'www.runoob.com').span()) 
# 在起始位置匹配 
print(re.match('com', 'www.runoob.com')) 
# 不在起始位置匹配

# 输出
# (0, 3)
# None
```


```python
import re


line = "Cats are smarter than dogs"
matchObj = re.match( r'(.*) are (.*?) .*', line, re.M|re.I)

if matchObj:
   print("matchObj.group() : ", matchObj.group())
   print("matchObj.group(1) : ", matchObj.group(1))
   print("matchObj.group(2) : ", matchObj.group(2))
   print("matchObj.groups() : ", matchObj.groups())
else:
   print("No match!!")

# 输出
# matchObj.group() : Cats are smarter than dogs 
# matchObj.group(1) : Cats 
# matchObj.group(2) : smarter 
# matchObj.groups() : ('Cats', 'smarter')
```


## re.search


re.search 扫描整个字符串并返回第一个成功的匹配

```python
import re 
print(re.search('www', 'www.runoob.com').span()) 
# 在起始位置匹配 
print(re.search('com', 'www.runoob.com').span()) 
# 不在起始位置匹配

# 输出
# (0, 3) 
# (11, 14)
```

```python
import re


line = "Cats are smarter than dogs"
matchObj = re.search( r'(.*) are (.*?) .*', line, re.M|re.I)

if matchObj:
   print("matchObj.group() : ", matchObj.group())
   print("matchObj.group(1) : ", matchObj.group(1))
   print("matchObj.group(2) : ", matchObj.group(2))
   print("matchObj.groups() : ", matchObj.groups())
else:
   print("No match!!")

# 输出
# matchObj.group() : Cats are smarter than dogs 
# matchObj.group(1) : Cats 
# matchObj.group(2) : smarter 
# matchObj.groups() : ('Cats', 'smarter')
```

re.match 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None；而 re.search 匹配整个字符串，直到找到一个匹配。


## re.sub


```python
import re 

phone = "2004-959-559 # 这是一个国外电话号码"

# 删除字符串中的 Python注释 
num = re.sub(r'#.*$', "", phone) 
print("电话号码是: ", num) 

# 删除非数字(-)的字符串 
num = re.sub(r'\D', "", phone) 
print("电话号码是 : ", num)

# 输出
# 电话号码是: 2004-959-559 
# 电话号码是 : 2004959559
```

```python
import re 

# 将匹配的数字乘以 2 
def double(matched): 
    value = int(matched.group('value')) 
    return str(value * 2) 
s = 'A23G4HFD567' 
print(re.sub('(?P<value>\d+)', double, s))
```

### `(?P...)` 分组匹配

例：身份证 1102231990xxxxxxxx

```python
import re
s = '1102231990xxxxxxxx'
res = re.search('(?P<province>\d{3})(?P<city>\d{3})(?P<born_year>\d{4})',s)
print(res.groupdict())

# 输出
# {'province': '110', 'city': '223', 'born_year': '1990'}
```


## re.compile


```python
import re

s = 'one12twothree34four'
pattern = re.compile(r'\d+')
m = pattern.match(s)
print(m)
# 输出
# None

m = pattern.match(s, 2, 10)
print(m)
# 输出
# None

m = pattern.match(s, 3, 10)
print(m)
# 输出
# <_sre.SRE_Match object at 0x10a42aac0>

>>> m.group(0) # 可省略 0 
'12' 
>>> m.start(0) # 可省略 0 
3 
>>> m.end(0) # 可省略 0 
5 
>>> m.span(0) # 可省略 0 
(3, 5)
```


## re.findall


```python
import re

pattern = re.compile(r'\d+')   # 查找数字
result1 = pattern.findall('runoob 123 google 456')
result2 = pattern.findall('run88oob123google456', 0, 10)
  

print(result1)
print(result2)

# 输出
# ['123', '456']
# ['88', '12']
```

```python
import re

result = re.findall(r'(\w+)=(\d+)', 'set width=20 and height=10')

print(result)

# 输出
# [('width', '20'), ('height', '10')]
```


## re.finditer


```python
import re 
it = re.finditer(r"\d+","12a32bc43jf3") 
for match in it: 
    print(match.group())

# 输出
# 12 
# 32 
# 43 
# 3
```


`findall` 返回列表

`finditer` 换回迭代器


## re.split


```python
import re

print(re.split('\W+', 'runoob.'))
print(re.split('\W+', 'runoob, runoob, runoob.'))
print(re.split('(\W+)', 'runoob.'))
print(re.split('(\W+)', ' runoob, runoob, runoob.'))
# 参数 1 为分割次数
print(re.split('\W+', ' runoob, runoob, runoob.', 1))
```

输出

```python
['runoob', '']
['runoob', 'runoob', 'runoob', ''] 
['runoob', '.', '']
['', ' ', 'runoob', ', ', 'runoob', ', ', 'runoob', '.', ''] 
['', 'runoob, runoob, runoob.']
```

