
<table><tr><td bgcolor=#FF83FA>背景色的设置是按照十六进制颜色值</td></tr></table>
Python基础操作笔记
===

## 字符串

### 字符串是“不可变的”，可通过切片和连接“改变”。（略）



>- 三重引号的多行字符

```python
print("""that's your name,
and what's your name?

and you?""")
```
输出：
that's your name,
and what's your name?

and you?



>- 字符串通过下标来切片(修改)
```python
s = 'hello'
print(s[0])
#将字符串第1号元素-第2号元素赋给变量y
y = s[1:3] 
print(y)
```
输出：
h
el



#### isX字符串方法
>- .isalpha()返回True，如果字符串只包含字母，并且非空
>- .isalnum()返回True，如果字符串只包含字母和数字，且非空
>- .isdecimal()返回True，如果字符串只包含数字，且非空
>- .isspace()返回True，如果字符串只包含空格、制表符、换行，且非空
>- .istitle()返回True,如果字符串只包含以大写字母开头，后面全是小写字母的单词

```python
print('hello world'.startswith('hello'))
print('hello world'.endswith('hello'))
```
输出：
True
False



#### join()
>- join()将一个字符串列表，连接起来，组成一个单独的字符串

```python
print(' '.join(['my','name','is','lin']))
```
输出：
my name is lin



#### 文本对齐方法
```python
print('hello'.rjust(10))
print('hello'.rjust(10,'*'))
print('hello'.ljust(10))
print('hello'.center(20))
print('hello'.center(20,'='))
```
输出：
     hello
*****hello
hello
       hello
=======hello========

[^评注]:'hello'.rjust(10):右对齐，将'hello'放在一个长度为10的字符串中。而'hello'中有5个字符，所以左边会加上5个空格其他同上



#### 用strip()、rstrip()、lstrip()删除空白字符



```python
spam = ' hello word '
#去掉字符串首尾的空白字符
print(spam.strip())
#去掉右边的空白字符
print(spam.rstrip())
#去掉左边的空白字符
print(spam.lstrip())
```
输出：
hello word
 hello word
hello word



## 列表
>eg：
>list = [1,2,3,4]
>"1"是第1个元素或第0号

### 常用函数、方法

#### range()函数

```python
#打印0-5的列表
print(list(range(5)))
```
输出：
[0, 1, 2, 3, 4]



```python
#打印范围[1,21)，步长2的列表
print(list(range(1,21,2)))
```
输出：
[1, 3, 5, 7, 9, 11, 13, 15, 17, 19]



```python
#打印范围[21,1),步长为-2的列表
print(list(range(21,1,-2)))
```
输出：
[21, 19, 17, 15, 13, 11, 9, 7, 5, 3]



#### extend()函数

```python
list = [1,2,3,4]
#.extend([5,6,7])作用类似于 + [5,6,7] （拼接）
list.extend([5,6,7])
print(list)
```
输出：
[1, 2, 3, 4, 5, 6, 7]



#### .insert()方法

```python
list = [1,2,3,4]
#在第2号元素（3）前面插入数值6
list.insert(2,6)
print(list)
```
输出：
[1, 2, 6, 3, 4]



#### .index()、.get()方法

>- index('x')方法：传入一个值x，若值x在列表中，则返回它的下标；若x不在列表中，则报ValueError。
>- get('x')或get('x',0)作用和index()类似。不过get('x'),若x不在列表中，不会报错，只会返回0
```python
list = [1,2,3,4]
#打印2在列表中吗？2在1号位置
print(list.index(2))
```
输出：
1 

#### .split()方法

```python
s = 'this is a test.'
#将字符串拆成列表
print(s.split())
#将字符串s依据' '为分隔,拆成列表
print(list(s))
```
输出：
['this', 'is', 'a', 'test.']
['t', 'h', 'i', 's', ' ', 'i', 's', ' ', 'a', ' ', 't', 'e', 's', 't', '.']



```python
s = '12:35'
#将字符串s 依据':'为分隔，拆成列表
print(s.split(':'))
```
输出：
['12', '35']

#### .join()方法

```python
s = ['this', 'is', 'a', 'test.']
#将列表中的字符 转换成一个 字符串
print(' '.join(s))
```
输出：
this is a test.

#### .sort()、.shuffle()方法

```python
import random

t = [3,2,1,6,9,8,0,4]
#对列表t排序
t.sort()
print(t)
#对列表t随机排序
random.shuffle(t)
print(t)
#在列表t中随机选择一个数值
print(random.choice(t))
```
输出：
[0, 1, 2, 3, 4, 6, 8, 9]
[6, 0, 9, 2, 4, 8, 3, 1]
4

#### .randint()方法

```python
import random

#打印1-100的随机一个数
print(random.randint(1,101))
```
输出：
30



### 引用
```python
spam = 16
cheese = spam
spam =25
print(spam)
print(cheese)
```
输出：
25
16 （分析略）



```python
spam = [0,1,2,3,4,5]
#简单理解，cheese、spam都指向同一个列表
cheese = spam
cheese[1] = 15
print(cheese)
print(spam)
```
输出：
[0, 15, 2, 3, 4, 5]
[0, 15, 2, 3, 4, 5]

[^分析]：★★★好好理解 4.27.2022

>- 创建列表spam时，你将对它的引用赋给了变量（spam）。但下一行只是将spam中的列表引用拷贝到cheese，而不是列表值本身。这意味着存储在spam和cheese中的值，现在指向了同一个列表。而这个列表本身实际从未复制。所以当修改cheese变量的第1号元素时，也修改了spam指向的同一个列表。
>- 变量就像包含着值的盒子。
>- 列表变量实际上没包含列表，而是包含了对列表的“引用”？？？4.27.2022
>- 参数如何传递给函数？：当函数被调用时，参数的值被赋值给变元。对于列表，变元得到的是引用的拷贝。



```python
def eggs(someParameter):
    someParameter.append('hello')

spam = [1,2,3]
eggs(spam)
print(spam)
```
输出：
[1, 2, 3, 'hello']
[^评注]

>- 当eggs()被调用时，没有使用返回值为spam赋新值。相反，它直接修改了该列表。
>- 尽管spam、someParameter包含了不同的调用，但它们指向的是同一个列表



### copy模块的copy()和deepcopy()函数



[^引子]：

>- 在处理列表或字典时，尽管传递引用常常是最方便的方法，但如果函数修改了传入的列表或字典，我们可能给不希望这些变得影响原来的列表或字典。用如下方法：

>- copy.copy(),可以用来复制列表或字典这样的可变值，而不只是复制引用。


```python
import copy

spam = ['a','b','c','d']
cheese = copy.copy(spam)
cheese[1] = 15
print(spam)
print(cheese)
```
输出：
['a', 'b', 'c', 'd']
['a', 15, 'c', 'd']
[^评注]

>- 这里spam、cheese变量指向了独立的2个列表
>- 如果要复制的列表中包含了列表（不是引用哈），那就使用copy.deepcopy()函数来代替？4.27.2022



### 多重赋值技巧



```python
cat = ['fat','black','loud']
#原本给多个变量赋值的方法
size = cat[0]
color = cat[1]
disposition = cat[3]
#现在给多个变量赋值的方法
size,color,disposition = cat
```
[^批注]
>- 变量的数目和列表的长度必须严格相等，对应吗？4.27.2022



### 增强的赋值操作

>- i += 1 等价于 i = i + 1 （以下同理）
>- i -= 1 ;i *= 1 ;i /= 1 ;i %= 1

>#### 列表里面操作：
>- 添加元素：.append();.insert(1,'hello')将hello插入第1号元素位置
>- 删除元素 ： del ；.remove(); .pop() 
>- 排序：.sort()
>    - 可指定reverse=True，让.sort()按逆序排列即  .sort(reverse=True)
>    - 不能对既有数字又有字符串的排序
>    - .sort()方法对字符串排序时，使用“ASCII字符顺序”。若要按普通的A-Z排序，应.sort(key=str.lower)或 .sort(key=str.upper) lower upper 没有括号！


## 集合

#### 操作集合的元素
>- add(),remove,min(),max(),sum(),len()
>- set_1 | set_2:集合1并集合2
>- set_1 & set_2:集合1交集合2
>- set_1 ^ set_2: （集合1并集合2）-（集合1交集合2）
>- set_1 - set_2:在集合1中去掉包含集合2的元素

>eg:
set_1 = {1,2,3,4,5}
set_2 = {2,3,0}
集合set_1,set_2可以运算，可变，数值是唯一的，



[^注意]
>- {}这是一个字典
>- 集合中的元素是无序的

## 字典

>
```python
dict = {'one':1,'two':2}
#打印键'one'对应的值
print(dict['one'])
#修改键'one'的值为2
dict['one'] = 2
print(dict)
#添加键'three'的值为3
dict['three'] = 3
print(dict)
#删除键'one'对应的值
del dict['one']
print(dict)
```
输出：
1
{'one': 2, 'two': 2}
{'one': 2, 'two': 2, 'three': 3}
{'two': 2, 'three': 3}

```python
dict = {'one':1,'two':2}
#dict.get('one')与dict['one']作用类似，但对于字典中没的key，value，dict.get('ok'，0)不会报错；dict['ok']会报错
print(dict.get('one'))
print(dict['one'])
```
输出：
1
1
[^评注]
>- .get()方法有2个参数：要取得其值的键key；若该键key不存在，则返回备用值，备用值通常为0
>- .get('hello',0)

### setdefault()方法
>- .setdefault('x1','white'),该方法的第一个参数：是要检查的键key。第二个参数：若检查的键key不存在时设置的值。
>- 如果该键key确实存在，方法就返回该键对应的值。
```python
spam1 = {'name':'Pooka','age':5}
print(spam1.setdefault('color','white'))

spam2 = {'name':'Pooka','color':'black'}
print(spam2.setdefault('color','white'))
```
输出：
white
black


## 元组turple
>[^注意]：元组不可修改※※


```python
t = [1,2,3,4]
print(t)
#将列表转换成元组tuple。（转换的目的：元组不让修改）
p = tuple(t)
print(p) 
```
输出：
[1, 2, 3, 4]
(1, 2, 3, 4)

```python
s = ('cat','dog',5)
#将元组转换成列表
t = list(s)
print(t)
```
## 

## for循环
```python
x = int(input())
#这是使用其他语言的方式
isprime = True
for k in range(2,x):
    if x%k == 0:
        isprime = False
if isprime:
    print('is prime.')
else:
    print('is not prime.')
```
## while循环

>- break语句：如果执行遇到break语句，就会马上退出while循环子句
>- continue语句：如果程序执行遇到continue语句，就会马上跳回while循环开始处（继续循环）

### 等价的while循环
>- while循环可以做和for循环一样的事
[^批注] 这有啥用？？？4.26.2022


## 异常
用 try-except-else 代码块 处理异常
或：
```python
try:
    语句块1
except 异常类型1：
    语句块2
...
except 异常类型n：
    语句块n+1
#else的作用：try了后，没有出现上述异常类型，则运行else
else:
    语句块n+2
#finally作用：无论上述有没有异常出现，都要运行finally
finally：
    语句块n+3
```
eg:
```python
x = int(input())
t = [1,2,3,4,5]
try:
    print(t[x])
    print('hello')
except:
    print('x is not a valid index.')
else:
    print('nothing')
finally:
    print('anyway')
```
输入：2
输出：
2
3
hello
nothing
anyway

输入：7
输出：
x is not a valid index.
anyway

## 自定义函数 def
>- 函数定义时的参数称为形参（类似于变量）
>- 当调用参数时，函数中的参数值称为实参
>- 函数形参取得的值 == 调用函数时提供的实参

[^批注] ★★★
>- 当调用函数时没提供对应形式参数的值时，可以指定默认形式参数。
>- 如果调用函数时提供了实参，在调用时，（实参）会代替默认值。 
>- *或**加在形参前面，表示不定长参数，分别用来接收不带变量名的多余参数和带有变量名的多余参数，分别将它们以元组、字典形式接收进函数。
>- 当实参是不可变对象时，形参值改变不影响实参
>- 当实参是可变对象时，形参值改变可能影响实参
>- return后面的表达式的值就成为这次函数调用的返回值
>- 若函数没有用return语句返回，这时函数返回值为None；若return后面没有表达式，函数返回值为None
>- return：函数返回值或者表达式
>- None表示没有值
>- 对于没有return语句的函数定义，Python都会在末尾加上return None


```python
l = [2,3,5,7]
#将列表l拆成单独的实参值 （实参拆包）
print(*l)
```
输出：
2 3 5 7

#### 局部变量和全局变量
[^评注] 
这部分不太懂4.26.2022
```python
def scope():
    #此处var1 = 1是局部变量 
    var1 = 1
#此处var1 = 10 是全局变量
var1 = 10
```
```python
def scope():
    #若希望在函数中使用全局变量，需要用global关键字声明。这里var1是全局变量
    global var1
    var1 = 1
```
##### 局部和全局作用域
>- 在被调用函数内赋值的变元和变量，处于该函数的“局部作用域”
>- 在所有函数外赋值的变量，属于“全局作用域”
>- 处于局部（全局）作用域的变量，称为局部（全局）变量
>- 一个变量必是其中一种，不能既是全局又是局部
[^理解]
>- 可将“作用域”视作变量的容器。当作用域被销毁时，所有保存在该作用域的变量的值就被丢弃了。
>- 全局作用域，它是在程序开始时创建的。如果程序终止，全局作用域就被销毁了，这些变量就丢失了。下次运行程序时，这些变量是不会记住之前运行的值的。
>- 一个函数被调用时，就创建了局部作用域。在这个函数内赋值的所有变量，存在于该局部作用域。函数返回时，这个局部作用域就被销毁了，这些变量就丢失了。下次调用这个函数时，局部变量就不会记得该函数上次被调用时保存的值。
[^作用或用途]
>- 当特定函数调用中的代码修改变量时，该函数与程序其他部分的交互，只能通过它的参数和返回值。这缩小了可能导致缺陷的代码作用域。
>- 如果程序只包含全局变量，又有一个变量赋值错误的缺陷，那就很难追踪这个赋值错误发生的位置。它可能在程序的任何地方赋值
>- 如果缺陷是因为局部变量错误赋值，就只有那一个函数中的代码可能产生赋值错误。

###### 全局变量能用于全局作用域
###### 局部作用域可以访问全局变量

###### 局部变量不能在全局作用域中使用
```python
def spam():
    eggs = 32125
spam()
print(eggs)
```
输出：
发生异常: NameError
name 'eggs' is not defined
  File "D:\桌面\python每日练习\Untitled-1.py", line 4, in <module>
    print(eggs)
[^原因]eggs变量属于spam()调用所创建的局部作用域。在程序执行从spam返回后，该局部作用域就被销毁了，不再有名为eggs的变量了。

###### 局部作用域不能使用其他局部作用域的变量
[^]程序调用？返回？？4.27.2022

###### 全局变量可以在局部作用域中读取
```python
def spam():
    print(eggs)
eggs = 42
spam()
print(eggs)
```
输出：
42
42
{^分析}在spam()函数中，没有变量名为eggs，也没有代码为eggs赋值，所以当spam()使用eggs时，Python认为它是对全局变量eggs的引用。

###### 名称相同的局部变量和全局变量
{^批注}尽量避免全局变量和局部变量同名！！！ ★★★ 
```python
def spam():
    eggs = 'spam local'
    print(eggs)#prints 'spam local'

def bacon():
    eggs = 'bacon local'
    print(eggs)#prints 'bacon local'
    spam()
    print(eggs)#prints 'bacon local'

eggs = 'global'
bacon()
print(eggs)#prints 'global'
```
输出：
bacon local
spam local
bacon local
global

#### 递归
>递归：函数调用自身的编程技巧
[^评注]CSDN/知乎/百度/Google上搜索了解 “递归”

##### sorted函数语法
>- 

##### map函数
>- 语法：


##### zip函数
>- 语法：

#### 模块、包 ★★★★★
>- 包：为了使Python应用更具可拓展性，可以把多个模块文件组织成目录。
>- 包是一个目录，包含一组模块文件和一个init.py文件。
>- 如果模块存在于包中，使用" import 包名.模块名 "导入包中的模块
>- 用以下形式调用函数： "包名.模块名.函数"

#### sys模块 ？？？啥意思4.26.2022
>- sys.argv 从程序外部向程序传递参数
>- sys.path 模块搜索路径的字符串列表
>- sys.stdin 标准输入
>- sys.stdout 标准输出

#### 文件读写函数 ???学的不好。看书/csdn/百度 4.26.2022
>- open() 打开文件
>- read(size) 从文件中读取长度为size的字符串，若未给定或为负则读取所有内容
>- readline() 读取整行，返回字符串
>- readlines() 读取所有行并返回列表
>- write(s) 把字符串s的内容写入文件
>- writelines(s) 向文件写入一个元素为字符串的列表，若需要换行则要自己加入每行的换行符
>- tell() 返回文件读写的当前位置
>- close() 关闭文件。关闭文件后不能再进行读取操作

#### 面向对象
>- 面向对象：封装 继承 多态

#### 类
>- 类class中 self怎么理解？怎么使用？4.26.2022
>- Python中，使用内置方法isinstance()来测试一个对象是否为某个类的实例。 isinstance(对象名,类)

##### 封装
>- 封装：将数据和对数据的操作组合起来构成类，类是一个不可分割的独立单位
>- 类中既要提供与外部联系的接口，同时又要尽可能隐藏类的实现细节

###### 私有成员与公有成员
>- _xxx :受保护成员，不能用 from module import * 导入
>- __xxx__ :系统定义的特殊成员
>- __xxx ：私有成员，只有类内自己能访问，不能使用对象直接访问到这个成员

#### 多态？？？4.26.2022
>- 多态：子类的对象可以传递给需要父类类型的参数。动态绑定？、


# 自动化任务

## 正则表达式
>- 正则表达式是用来查找文本的
>- 正则表达式，简称regex

### 创建正则表达式对象及匹配Regex对象

```python
import re

#r‘字符串’，将该字符串标记成原始字符串
phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
mo = phoneNumRegex.search("My number is 415-222-3211.")
print('Phone number found: ' + mo.group())
```
输出：
Phone number found: 415-222-3211

### 用正则表达式匹配更多模式

#### 利用括号分组
```python
import re

phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)')
mo = phoneNumRegex.search("My number is 415-222-3211.")
#打印第一组的（第一个括号内的）
print( mo.group(1))
#打印第二组的（第二个括号内的）
print( mo.group(2))
#略
print( mo.group(3))
```
输出：
415
222
3211

##### 一次获取所有分组
```python
import re

phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)')
mo = phoneNumRegex.search("My number is 415-222-3211.")
#一次获取所有分组
print( mo.groups())
```
输出：
('415', '222', '3211')

##### 转义括号
>- 括号在正则表达式中有特殊含义。，若要在文本中匹配括号，则需对括号转义
```python
import re

#匹配第一组的括号，（对括号转义）
phoneNumRegex = re.compile(r'(\(\d\d\d\))-(\d\d\d)-(\d\d\d\d)')
mo = phoneNumRegex.search("My number is (415)-222-3211.")
print(mo.group(1))
print(mo.group(2))
```
输出：
(415)
222

#### 用管道|匹配多个分组
>- 字符| 称为管道，表示 “或”。

```python
import re

#第一次出现的匹配文本，将作为Match对象返回
heroRegex = re.compile(r'Batman|Tina Fey')
mo1 = heroRegex.search('Batman and Tina Fey.')
print(mo1.group())

mo2 = heroRegex.search('Tina Fey and Batman.')
print(mo2.group())
```
输出：
Batman
Tina Fey

#### 用问号实现可选匹配
>- (字符串)? ：字符串在不在，都是可选的（要么没有，要么有一个）

```python
import re

batRegex = re.compile(r'Bat(wo)?man')
mo1 = batRegex.search('The Adventures of Batman.')
print(mo1.group())

mo2 = batRegex.search('The Adventures of Batwoman.')
print(mo2.group())
```
输出：
Batman
Batwoman

#### 用星号匹配0次或多次

```python
import re

batRegex = re.compile(r'Bat(wo)*man')
mo1 = batRegex.search('The Adventures of Batman.')
print(mo1.group())

mo2 = batRegex.search('The Adventures of Batwoman.')
print(mo2.group())

mo3 = batRegex.search('The Adventures of Batwowowoman')
print(mo3.group())
```
输出：
Batman
Batwoman
Batwowowoman

#### 用加号匹配一次或多次

```python
import re

batRegex = re.compile(r'Bat(wo)+man')
mo2 = batRegex.search('The Adventures of Batwoman.')
print(mo2.group())

mo3 = batRegex.search('The Adventures of Batwowowoman')
print(mo3.group())
```
输出：
Batwoman
Batwowowoman

#### 用花括号匹配特定次数
>- 正则表达式(Ha){3}将匹配字符串'HaHaHa',但不会匹配'HaHa'、'Ha'
```python
import re

batRegex = re.compile(r'Bat(wo){3}man')
mo3 = batRegex.search('The Adventures of Batwowowoman')
print(mo3.group())
```
输出：
Batwowowoman

>- 花括号还能指定范围。(Ha){2,4}可以匹配'HaHa' 'HaHaHa' 'HaHaHaHa'
```python
import re

batRegex = re.compile(r'Bat(wo){2,4}man')
mo1 = batRegex.search('The Adventures of Batwowoman')
print(mo1.group())

mo2 = batRegex.search('The Adventures of Batwowowoman')
print(mo2.group())

mo3 = batRegex.search('The Adventures of Batwowowowoman')
print(mo3.group())
```
输出：
Batwowoman
Batwowowoman
Batwowowowoman

>- (ha){,3}:不限定最小值
>- (ha){2,}:不限定最大值

### 贪心和非贪心匹配
>- python的正则表达式是“贪心的”，它们会尽可能匹配最长的字符串
>- 花括号的“非贪心”匹配尽可能最短的字符串。（在结束的花括号后加个?）

```python
import re

#“贪心”
greedyHaRegex = re.compile(r'(Ha){3,5}')
mo1 = greedyHaRegex.search('HaHaHaHaHa')
print(mo1.group())

#“非贪心”
greedyHaRegex = re.compile(r'(Ha){3,5}?')
mo2 = greedyHaRegex.search('HaHaHaHaHa')
print(mo2.group())
```
输出：
HaHaHaHaHa
HaHaHa

[^注意]
>- 问号在正则表达式中可能有2种含义
    >- 声明 非贪心 匹配
    >- 表示可选的分组

### .findall()方法
>- .findall()类似于.search()方法。.findall()方法将返回一组字符串，包含被查找字符串中的所有匹配。
```python
import re

#正则表达式未分组
phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
mo = phoneNumRegex.findall('Cell:416-241-2415 Work:234-531-8532')
print(mo)

#正则表达式已分组
phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)')
mo1 = phoneNumRegex.findall('Cell:416-241-2415 Work:234-531-8532')
print(mo1)
```
输出：
['416-241-2415', '234-531-8532']
[('416', '241', '2415'), ('234', '531', '8532')]

### 字符分类
>- \d :0-9的数字；\D :除0-9外的任何字符
>- \w :字母、数字、下划线字符；\W :除字母、数字、下划线字符外的任何字符
>- \s :空格、制表符、换行符； \S :除空格、制表符、换行符的任何字符

```python
import re

xmaxRegex = re.compile(r'\d+\s\w+')
a = xmaxRegex.findall('12 drummers,11 pipers,10 lords,9 ladies')
print(a)
```
输出：
['12 drummers', '11 pipers', '10 lords', '9 ladies']

### 建立自己的字符分类
>- 可以用方括号[ ]来定义自己的字符

```python
import re

vowelRegex = re.compile(r'[aeiouAEIOU]')
print(vowelRegex.findall('RoboCop eats baby food.BABY FOOD.'))
```
输出：
['o', 'o', 'o', 'e', 'a', 'a', 'o', 'o', 'A', 'O', 'O']

```python
import re

#在字符串aeiouAEIOU前面加入^,表示匹配所有非元音字符
vowelRegex = re.compile(r'[^aeiouAEIOU]')
print(vowelRegex.findall('RoboCop eats baby food.BABY FOOD.'))
```
输出：
['R', 'b', 'C', 'p', ' ', 't', 's', ' ', 'b', 'b', 'y', ' ', 'f', 'd', '.', 'B', 'B', 'Y', ' ', 'F', 'D', '.']

### 插入字符和美元符
>- 在正则表达式开始处插入 ^ ,表示匹配必须发生在被查找文本的开始处。
>- 在正则表达式的末尾加上 $ ,表示匹配必须发生在被查找文本的结束处。
>- 可同时使用 ^字符串$ ，表示整个字符串必须匹配该模式

```python
import re

beginsWithHello = re.compile(r'^Hello')
print(beginsWithHello.search('Hello world!'))
print(beginsWithHello.search('He sai hello.'))

endsWithNumber = re.compile(r'\d$')
print(endsWithNumber.search('nihao 16'))
print(endsWithNumber.search('nihao'))

wholeStringIsNum = re.compile(r'^\d+$')
print(wholeStringIsNum.search('14245566'))
print(wholeStringIsNum.search('13gfsd3565'))
print(wholeStringIsNum.search('124 65346 212'))
```
输出：
<re.Match object; span=(0, 5), match='Hello'>
None
<re.Match object; span=(7, 8), match='6'>
None
<re.Match object; span=(0, 8), match='14245566'>
None
None

### 通配字符
>- .(句点)字符称为“通配符”，它匹配除了换行之外的所有字符。
>- .ab :只匹配ab前的一个字符 ★★ 

```python
import re

atRegex = re.compile(r'.at')
print(atRegex.findall('The cat in the hat sat on the flat mat,*at,$at.'))
```
输出：
['cat', 'hat', 'sat', 'lat', 'mat', '*at', '$at']
[注意]若要匹配真正的句点（.） ，则转义 \.

#### 用点 星匹配所有字符
>- .*表示匹配任意文本

```python
import re

#贪心
greedRegex = re.compile(r'<.*>')
mo = greedRegex.search('<To serve man> for dinner.>')
print(mo.group())

#不贪心
nogreedRegex = re.compile(r'<.*?>')
mo1 = nogreedRegex.search('<To serve man> for dinner.>')
print(mo1.group())
```
输出：
<To serve man> for dinner.>
<To serve man>

[^注]
>- {n,m}? *? +?表示对前面的分组进行 非贪心匹配

#### 用句点字符匹配换行
>- 通过传入re.DOTALL作为re.compile()的第二个参数，可以让句点（.）字符匹配所有字符

```python
import re

newlineRegex = re.compile('.*')
a = newlineRegex.search('Serve the public trust.\nProtect the innocent.\nUphold the law.')
print(a.group())
```
输出：
Serve the public trust.

```python
import re

newlineRegex = re.compile('.*',re.DOTALL)
a = newlineRegex.search('Serve the public trust.\nProtect the innocent.\nUphold the law.')
print(a.group())
```
输出：
Serve the public trust.
Protect the innocent.
Uphold the law.
[^分析]
>- 第一个代码的正则表达式没有向re.compile()传入re.DOTALL,它将匹配所有字符，直到第一个换行字符。
>- 第二个代码 则匹配所有字符，包括换行字符

#### 不区分大小写的匹配
>- 要让正则表达式不区分大小写，可以向re.compile()传入re.IGNORECASE或re.I作为第二个参数

```python
import re

robocop = re.compile(r'robocop',re.I)
a = robocop.search('Robocop is part man,all cop.')
print(a.group())
```
输出：
Robocop

#### 用sub()方法替换字符串
>- Regex对象的sub()方法需要传入2个参数。第一个参数是一个字符串，用于替代发现的匹配；第二个参数是一个字符串，是正则表达式。
```python
import re

namesRegex = re.compile(r'Agent \w+')
print(namesRegex.sub('CENSORED','Agent Alice gave the....to Agent Bob.'))
```
输出：
CENSORED gave the....to CENSORED.

#### 管理复杂的正则表达式
不太理解。4.29.2022

>- 向re.compile()传入变量re.VERBOSE,作为第二个参数，即告诉re.compile(),忽略正则表达式字符串中的空白符和注释。

```python
import re

phoneRegex = re,compile(r'''(
(\d{3}|(\d{3}\))?       #area code
(\s|-|\.)?              #separator
\d{3}                   #first 3 digits
(\s|-|\.)               #separator
\d{4}                   #last 4 digits
(\s*(ext|x|ext.)\s*\d{2,5})?  #extension
)''',re.VERBOSE)
```
[^分析]
>- 三重引号（'''）可以创建多行字符串，即可以将正则表达式放在多行中，让其更可读。
>- 正则表达式中的注释和Python中的注释类似。

#### 组合使用re.IGNORECASE、re.DOTALL、re.VERBOSE

>- re.compile()函数只接受一个值作为它的第二个参数。
>- 此时可用（|）将变量组合起来，从而绕过这个机制。

```python
import re

#使用第二个参数的全部2个选项
someRegexValue = re.compile('foo',re.IGNORECASE | re.DOTALL)
#使用第二个参数的全部3个选项
someRegexValue = re.compile('foo',re.IGNORECASE | re.DOTALL | re.VERBOSE)
```

### 用pyperclip模块复制粘贴字符串★★★ 

>- pyperclip模块有copy()、paste()函数，可以向剪贴板发送文本，或从它接收文本。
>- 将程序的输出发送到剪贴板，使它可以粘贴到邮件或其他程序

```python
import pyperclip

pyperclip.copy('hello world.')
print(pyperclip.paste())
```
输出：
hello world.

### 正则表达式小项目
>- 路径：D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email\phoneAndEmail.py

### 常用的实用正则表达式整理

>- 只能输入数字："^[0-9]*$"。
>- 只能输入n位的数字："^"d{n}$"。
>- 只能输入m~n位的数字：。"^"d{m,n}$"
>- 验证用户密码："^[a-zA-Z]"w{5,17}$"正确格式为：以字母开头，长度在6~18之间，只能包含字符、数字和下划线。
>- 只能输入汉字："^["u4e00-"u9fa5]{0,}$"
>- 验证Email地址："^"w+([-+.]"w+)*@"w+([-.]"w+)*"."w+([-.]"w+)*$"。
>- 验证InternetURL："^http://(["w-]+".)+["w-]+(/["w-./?%&=]*)?$"。
>- 验证电话号码："^("("d{3,4}-)|"d{3.4}-)?"d{7,8}$"正确格式为："XXX-XXXXXXX"、"XXXX- XXXXXXXX"、"XXX-XXXXXXX"、"XXX-XXXXXXXX"、"XXXXXXX"和"XXXXXXXX"。
>- 验证身份证号(15位或18位数字)："^"d{15}|"d{18}$"。
>- 验证一年的12个月："^(0?[1-9]|1[0-2])$"正确格式为："01"～"09"和"1"～"12"。
>- 验证一个月的31天："^((0?[1-9])|((1|2)[0-9])|30|31)$"正确格式为;"01"～"09"和"1"～"31"。

### 利用正则表达式限制网页表单里的文本框输入内容（个人不怎么使用）：

>- 用正则表达式限制只能输入中文：οnkeyup="value=value.replace(/[^"u4E00-"u9FA5] /g,’’)" onbeforepaste="clipboardData.setData(’text’,clipboardData.getData(’text’).replace(/[^"u4E00-"u9FA5]/g,’’))"
>- 用正则表达式限制只能输入数字：οnkeyup="value=value.replace(/[^"d]/g,’’) "onbeforepaste="clipboardData.setData(’text’,clipboardData.getData(’text’).replace(/[^"d]/g,’’))"
>- 用正则表达式限制只能输入数字和英文：οnkeyup="value=value.replace(/["W]/g,’’) "onbeforepaste="clipboardData.setData(’text’,clipboardData.getData(’text’).replace(/[^"d]/g,’’))"


## 读取文件

### 文件与文件路径

#### 当前工作目录
>- os.getcwd()获得当前工作路径
>- os.chdir()改变当前工作路径
```python
import os

print(os.getcwd())

os.chdir('D:\\桌面')
print(os.getcwd())
```
输出：
D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email
D:\桌面

#### 绝对路径与相对路径
>- 绝对路径，总是从根文件夹开始
>- 相对路径，相对于程序的当前工作目录
>- 单个点（.），表示当前文件所在工作目录
>- 点点（..），返回上一级文件夹

#### 用os.makedirs()创建文件夹
```python
import os

os.makedirs('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找')

```
查找文件夹，确实创建了这个文件夹

#### 处理绝对路径、相对路径

>- os.path.abspath(path),将相对路径转换成绝对路径
>- os.path.isabs(path)，若是绝对路径返回True
>- os.path.relpath(path,start)将返回从start路径到path的相对路径的字符串。若未提供start，则以当前工作目录为start
```python
import os

print(os.path.abspath('.'))
print(os.path.abspath('.\\Scripts'))
print(os.path.isabs('.'))
```
输出：
D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email
D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email\Scripts
False

```python
import os

print(os.path.relpath('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习','D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email\Scripts'))
```
输出：
..\..\..

>- os.path.dirname(path)返回一个字符串，包含path参数中最后一个斜杠之前的所有内容
>- os.path.basename(path)返回一个字符串，包含path参数中最后一个斜杠之后的所有内容
```python
import os

path = 'D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email'
print(os.path.dirname(path))
print(os.path.basename(path))
```
输出：
D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目
快速查找剪贴板的电话、email
>- os.path.split(path),返回一个完整的路径
```python
import os

path = 'D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\快速查找剪贴板的电话、email'
print(os.path.split(path))
#打印为列表
print(path.split(os.path.sep))
```
输出:(元组)
('D:\\桌面\\研究生阶段文件\\准研究生阶段2022.4--2022.8\\编程大类文件\\python\\python每日练习\\自动化任务的小项目', '快速查找剪贴板的电话、email')
['D:', '桌面', '研究生阶段文件', '准研究生阶段2022.4--2022.8', '编程大类文件', 'python', 'python每日练习', '自动化任务的小项目', '快速查找剪贴板的电话、email']

#### 查看文件大小和文件夹内容
>- os.path.getsize(path)将返回path参数中文件的字节数
>- os.listdir(path)将返回文件名字字符串的列表，包含path参数的每个文件。

```python
import os

a = os.path.getsize('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、')
print(a)
b = os.listdir('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、')
print(b)
```
输出：
0
['5.3.2020练习.py', '5.5练习.py']
#### 检查路径的有效性

>- os.path.exists(path)，若path路径的文件（夹）存在，则返回True
>- os.path.isfile(path),若path路径的文件存在，则返回True
>- os.path.isdir(path),若path路径的文件夹存在，则返回True
```python
import os

print(os.path.exists('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、'))
print(os.path.isdir('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、'))
```
输出：
True
True

### 文件读写过程
1. 调用open()函数，返回一个File对象
2. 调用File对象的read()或write()方法
3. 调用File对象的close()方法
 ```python
import os

helloFile = open('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\hello.txt')
#读取hello.txt
helloContent = helloFile.read()
print(helloContent)
```
输出：
hello world

```python
import os

helloFile = open('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\逐行读取.txt')
#逐行读取txt文件
helloContent = helloFile.readlines()
print(helloContent)
```
输出：（多了个换行符\n）
['1234\n', '23456\n', '24561\n', '2445']

```python
import os

helloFile = open('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\hello.txt','w')
helloContent = helloFile.write('你好呀\n')
#打印出写入的字符个数
print(helloContent)
helloFile.close()

helloFile = open('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\hello.txt','a')
helloContent = helloFile.write('勇士')
helloFile.close()

helloFile = open('D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\hello.txt')
content = helloFile.read()
helloFile.close()
print(content)
```
输出：
4
你好呀
勇士

### 用shelve模块保存变量
>- 利用shelve模块，可以将Python程序中的变量保存到二进制的shelf文件中。shelve模块让你在程序中保存和打开。
```python
import shelve

shelfFile = shelve.open('mydata')
cats = ['Zophie','Pooka']
shelfFile['cats'] = cats
#key为 cats，value为['Zophie','Pooka']
print(shelfFile['cats'])
print(list(shelfFile.keys()))
print(list(shelfFile.values()))
shelfFile.close
```
输出：
['Zophie', 'Pooka']
['cats']
[['Zophie', 'Pooka']]

### 用pprint.pformat()函数保存变量
>- pprint.pprint()函数将列表或字典的内容“漂亮打印”到屏幕。
>- pprint.pformat()函数将返回同样的文本字符串，但不打印它。

```python
import pprint

cats = [{'name': 'Zophie','desc': 'chubby'},{'name': 'Tobby','desc': 'lazy'},{'name': 'James','desc': 'x'}]
#不打印出来
pprint.pformat(cats)
#会被打印出来
pprint.pprint(cats)

fileObj = open('myCats.py','w')
fileObj.write('cats = ' + pprint.pformat(cats) + '\n')
fileObj.close()

fileObj = open('myCats.py')
print(fileObj.read())
fileObj.close()
print(cats[0])
print(cats[0]['name'])
```
输出：
[{'desc': 'chubby', 'name': 'Zophie'},
 {'desc': 'lazy', 'name': 'Tobby'},
 {'desc': 'x', 'name': 'James'}]
cats = [{'desc': 'chubby', 'name': 'Zophie'},
 {'desc': 'lazy', 'name': 'Tobby'},
 {'desc': 'x', 'name': 'James'}]
{'name': 'Zophie', 'desc': 'chubby'}
Zophie

### 小项目：多重剪贴板
>- 背景：需要填充网页或软件中的许多表格，其中包含一些文本字段。但剪贴板一次只能复制一段内容。如果有几段不同的文本需要复制，就不得不一次又一次的标记、复制几个相同的内容。
>- 现在可以用Python，追踪几段文本？？？5.5.2022
>- 多重剪贴板命名为 mcb.pyw （multiclipboard）。pyw扩展名意味着python运行该程序时，不会显示终端窗口。
>- 该程序利用一个关键字保存每段剪贴板文本。例如，当运行py mcb.pyw save spam，剪贴板中当前的内容就用关键字spam保存；通过运行py mcb.pyw spam，这段文本将重新加载到剪贴板中。
>- 如果用户忘记了都有哪些关键字，可运行py mcb.pyw list,将所有关键字的列表复制到剪贴板中。

[^注释]：详细内容参考书 《Python编程快速上手》P153
>- 项目地址：D:\桌面\研究生阶段文件\准研究生阶段2022.4--2022.8\编程大类文件\python\python每日练习\自动化任务的小项目\文件查找、\mcb.pyw
[^疑问] 该脚本怎么运行？？？5.5.2022 

>- sys.argv是一个从【程序外部】获取参数的桥梁，从外部取得的参数可以是多个，所以获得的是一个列表（list)，也就是说sys.argv其实可以看作是一个列表，可以用[0]、[1]、[2]、[3]…等提取其中的元素。第一个元素（sys.argv[0]）是程序本身，随后才依次是外部给予的参数。
？？再看看B站视频5.5.2022
[^不会的] 