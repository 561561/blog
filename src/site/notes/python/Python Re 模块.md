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
