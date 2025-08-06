---
title: Python
tags: 
- Python
- AI
categories:
- 学习
---

# Python

> 2025-6-14，立项

AI 学习的前置技能。

环境：**Anaconda**

教程：[廖雪峰的官方网站 Python教程](https://liaoxuefeng.com/books/python/introduction/index.html)

## Anaconda

下载地址：https://www.anaconda.com/download/success

初用下来，在 Anaconda Navigator 这硬控我 2h，之后了解才知道 Anaconda Navigator 不是关键，Anaconda Prompt 才是关键。而 Anaconda 可以简单理解为是对 Python 环境与依赖进行管理的一个工具，命令行工具才是关键，后续需要了解他的常用命令。无视 Anaconda Navigator 后，直接在 VSCode 中，配置好 Python 环境，开始使用。

## Python 语法

### Python 基础

- 输入，输出。

  input()，print()。包含一些转义字符，多行文本输出。

- 数据类型与变量。

  整数、浮点数（1e10）、字符串、布尔值（True、False）、空值（None）。

- 字符串和编码

  字符编码。ASCII，GB2312，Unicode，UTF-8。

  ord()，chr()。

  encode()，decode()。

  格式化方法。占位符，format()，f-string。

- list 和 tuple

  []，()。

- 条件判断

  ```python
  if age >= 6:
  elif age >= 18:
  else:
  ```

- 模式匹配

  ```python
  age = 15
  match age:
      case x if x < 10:	# 同时赋值了
          print(f'< 10 years old: {x}')
      case 10:
          print('10 years old.')
      case 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18:
          print('11~18 years old.')
      case 19:
          print('19 years old.')
      case _:
          print('not sure.')
  
  ```

- 循环

  ```python
  # for
  sum = 0
  for x in range(101):
      sum = sum + x
  print(sum)
  
  # while
  sum = 0
  n = 99
  while n > 0:
      sum = sum + n
      n = n - 2
  print(sum)
  
  ```

- dict 和 set

### 函数

```
def name():
	# todo
	pass # 占位符
```

必选参数、默认参数、可变参数、关键字参数和命名关键字参数。

关键字参数，同时传入变量名与变量值。

命名关键字参数，传入的变量名必须与命名值相符。


### 高级特性

list 或 tuple 的切片。

迭代。就是循环。

列表生成式。通过表达式生成一个 list。

生成器。基于列表生成式，还有函数版本的，可以玩的很复杂。

迭代器。配合生成，用于迭代。


### 函数式编程

待定。