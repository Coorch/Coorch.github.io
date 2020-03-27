---
layout: post
title: Python的五种参数
categories: Python
description: 位置参数、关键字参数、可变位置参数、可变关键字参数、默认参数
keywords: Python, 参数
---
### <center>Python的五种参数详解</center>

#### 1、位置参数 

```python
def f(a, b):
    print(a, b)
f(1, 2) # 1, 2
```

&emsp;&emsp;顾名思义，位置参数是按照位置来给形参赋值的。比如例子中f有两个参数，调用的时候，按照位置的前后顺序，a=1, b=2，所以输出是这样的结果
<br>
#### 2、关键字参数

```python
def f(a, b):
    print(a, b)
f(b = 1, a = 2) # 2, 1
```

&emsp;&emsp;顾名思义，关键字参数是按照关键字来给形参赋值的，对于关键字参数，位置的前后就不重要了。

**关键字参数必须在位置参数的右边**

```python
f(b=1, 2) # SyntaxError: positional argument follows keyword argument
f(a=1, 2) # SyntaxError: positional argument follows keyword argument
```

&emsp;&emsp;这样的输入也不行，因为位置参数默认按照前后顺序赋值，第一个值赋给的形参是a，再给a用关键字的形式赋值就会报错了

```python
f(1, a=1)     # TypeError: f() got multiple values for argument 'a'
f(1, a=1, b=2)# TypeError: f() got multiple values for argument 'a'
```

**混合使用，关键字参数不要给位置参数重复赋值！！！**
<br>
#### 3、默认参数

```python
def f(a, b=2):
    print(a, b)
f(1) # 1,2
```

&emsp;&emsp;顾名思义，默认参数就是指在定义的时候，形参已经给定了一个默认值，在调用函数的时候，不给默认参数传递参数也是可以的。

**默认参数必须在位置参数和关键字的右边**

```python
def f(a=1, b):
    print(a, b)
f(2)   # SyntaxError: non-default argument follows default argument
f(b=2) # SyntaxError: non-default argument follows default argument
```

**非默认参数缺一不可**

```python
def f(a, b=1):
    print(a, b)
f() #T ypeError: f() missing 1 required positional argument: 'a'
```
<br>
#### 4、可变位置参数 def f(*args):

```python
def f(*args):
    print(args)
f(1,2,3)  # (1, 2, 3)
f(1,2,3,4)# (1, 2, 3, 4)
```

&emsp;&emsp;可变的意思是参数的数量是可以变化的，只有一个*，说明是可变位置参数，在函数中处理时，可变位置参数会被解析为元组。

**可变位置参数不能传入关键字参数**

```python
def f(*args):
    print(args)
f(1,2,c=3) # TypeError: f() got an unexpected keyword argument 'c' 
```
<br>
#### 5、可变关键字参数 def f(**kw):

&emsp;&emsp;有两个*，说明是可变关键字参数，在函数中处理时，可变关键字参数会被解析为字典。

```python
def f(**kw):
    print(kw)
f(a=1,b=2,c=3) # {'a': 1, 'b': 2, 'c': 3}
```

**可变关键字参数不能传入位置参数，而且和关键字参数一样，必须在位置参数的右边**

```python
def f(**kw):
    print(kw)
f(1,b=2,c=3) # TypeError: f() takes 0 positional arguments but 1 was given
f(a=1,b=2,3) # SyntaxError: positional argument follows keyword argument
```
<br>
#### 6、查看参数类型

&emsp;&emsp;需要借助内置的inspect模块来查看

```python
from inspect import signature
def f(a,b=1,*args, **kw):
  	print(f'a:{a},b:{b}')
for name,val in signature(f).parameters.items():
    print(name,val.kind)
    # a POSITIONAL_OR_KEYWORD
	# b POSITIONAL_OR_KEYWORD
	# args VAR_POSITIONAL
	# kw VAR_KEYWORD
```

&emsp;&emsp;该模块不能查看默认参数；a和b都可以是位置或者关键字参数。