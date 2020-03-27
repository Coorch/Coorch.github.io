---
layout: post
title: 命令行解析工具
categories: Python
description: Python中的命令行解析库讲解
keywords: Python, 命令行
---
### <center>Python的命令行解析</center>
</br>
Python中的命令行解析库，主要有以下四种：

- sys.argv
- argparse
- click
- fire

#### sys.argv
```Python
from sys import argv
```
导入argv后，可以将其视作一个列表；
如果在命令行运行的是python test.py 1，那么在test.py中argv[0] = 'test.py',argv[1] = '1';
以此类推。

用sys模块只支持一些简单的传入，不能设定参数名称。

#### argparse库

#### click

#### fire库
这是一个神器，没有前两个库操作复杂，而且可以直接调用py文件中的函数、变量、类、实例等等。
