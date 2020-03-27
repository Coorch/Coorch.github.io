---
layout: post
title: 最大公约数
categories: Python
description: 最大公约数的两种求取算法
keywords: Python, 辗转相除法，更相减损术
---

### <center>最大公约数</center>

#### 1、辗转相除法

&emsp;&emsp;也称欧几里得算法。基本原理是，对于a和b两个正整数，不妨设a>b，则a和b的最大公约数gcd也是a与b的余数和b的最大公约数。
$$
gcd(a,b)=gcd(b,a\%b)......\%表示取余数
$$
编程实现的话，可以用递归来实现。

#####&emsp;（1）Python：

###### &emsp;&emsp;	1）两个数的最大公约数

```Python
def my_gcd(a, b):
    return b if a%b==0 else my_gcd(b, a%b)
```

&emsp;&emsp;函数中并没有对a和b进行大小比较，因为，如果a<b的话，a%b=a，执行else的时候就相当于把a和b调换了位置。

&emsp;&emsp;有内置的系统函数gcd，在Python3中使用时需要提前导入

```Python
from fractions import gcd
```

###### &emsp;&emsp;	2）数组的最大公约数

&emsp;&emsp;无论是上面自己的写的gcd，还是内置的系统函数，其输入参数都是两个数，如果想求整个数组的最大公约数，就需要用到Python的高级函数reduce。使用reduce前需要导入

```Python
from functools import reduce
```

&emsp;&emsp;先看reduce的定义：**reduce(function, iterable[, initializer])**

&emsp;&emsp;第一个参数function，要求是一个参数个数为2的函数，是第二个参数iterable——可迭代对象——的连续两项。

&emsp;&emsp;reduce的作用是：

- 将iterable看作是一个栈，将前两项pop出来，作为function的输入；
- 再把function的输出push到iterable中作为栈顶；
- 重复前面两步，直到iterable中只有一个元素，返回这个元素。

&emsp;&emsp;所以，要求数组a的最大公约数g，只需三行代码即可：

```Python
from functools import reduce
from fractions import gcd
g = reduce(gcd, a)
```
<br>
#### 2、更相减损术

&emsp;&emsp;出自《九章算术》，基本原理是，对于a和b两个正整数，不妨设a>b，则a和b的最大公约数gcd也是a与b的差和b的最大公约数。
$$
gcd(a,b)=gcd(a-b,b)
$$
&emsp;&emsp;Python代码如下：

```Python
def my_gcd(a, b):
    if a == b: return a
    elif a > b: return my_gcd(a - b, b)
    else: return my_gcd(a, b - a)
```

