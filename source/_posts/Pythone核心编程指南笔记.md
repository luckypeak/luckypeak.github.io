---
title: Python核心编程指南笔记
date: 2016-11-18 10:19:00
tags: 
    - python
	- 入门	
---

Python核心编程指南学习笔记

# 代码风格
 1.跨行的代码需要加反斜线（\）继续，括号内的语句可以不用加
 2.使用空格，而不是使用缩进；四个空格。制表符对于不同编辑器显示不同
 

 __name__ 标识模块如何被加载
 1.当模块是被导入，__name__的值是模块名字
 2.模块被直接执行时,__name__的值是__main__

 Python 对于不可变对象，Python会缓存，所以可能两个赋值整数的对象相等
 ```
 a = 1 b = 1  
 a==b 返回 True
 ```

# 内建函数
 str(),repr()返回变量的字符表示； 一般可以通过eval(repr(obj)) 重新获取对象；repr 等同于 ``
 str() 主要是生成一个描述性好的字符串
 cmp(obj1,obj2) 比较两个对象大小
 type（） 返回对象类型 

 对象比较
 is 两个对象是不一样，引用一样
 is not 

 类型工厂
 list(),dict(),tuple(),int()
 通过调用这些方法将生成对应实例

# 列表解析

语法 

````
[expr for expr in iterable]
[i for i in range(10)] 
[expr for expr in iterable if con]
[i for i in range(10) if i % 2 == 0]
```

# 生成器表达式

```
(expr for expr in iterable)
(i for i in range(10) )
(expr for expr in iterable if con)
(i for i in range(10) if i % 2 == 0)
```

生成器表达式并不立即生成一个列表，返回一个生成器。可以在序列过长，每次获取一个元素。
