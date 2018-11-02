---
title: Python函数中的参数传递
description: 
categories:
 - Python
tags: [Python语法]
---
### 变量与对象
>Python 中一切皆为对象，数字是对象，列表是对象，函数也是对象，任何东西都是对象。而变量是对象的一个引用（又称为名字或者标签），对象的操作都是通过引用来完成的。

### 定长对象与变长对象
Python中的对象分为两种：

- 定长对象：int, float, bool, string, tuple
- 变长对象：list, set, dict

对定长对象的任意改动都将重新为其分配内存空间；相反，对变长对象的改动是在原内存空间中进行的。参考如下代码：

```
#################
### IMMUTABLE ###
#################

def foo_int(var):
	var = 2
	return var

def foo_float(var):
	var = 1.0
	return var

def foo_bool(var):
	var = not var
	return var

def foo_string(var):
	var += "v"
	return var

def foo_tuple(var):
	var += (3,)
	return var

#################
### MUTABLE ###
#################

def foo_list(var):
	var.append(3)
	return var

def foo_set(var):
	var.add(3)
	return var

def foo_dict(var):
	var["foo"] = 1
	return var

if __name__ == '__main__':
	var = 1
	print(id(var) == id(foo_int(var))) # False
	var = 1.0
	print(id(var) == id(foo_float(var))) # False
	var = True
	print(id(var) == id(foo_bool(var))) # False
	var = 'test'
	print(id(var) == id(foo_string(var))) # False
	var = (1, 2)
	print(id(var) == id(foo_tuple(var))) # False
	var = [1, 2]
	print(id(var) == id(foo_list(var))) # True
	var = set([1, 2])
	print(id(var) == id(foo_set(var))) # True
	var = {0: "test"}
	print(id(var) == id(foo_dict(var))) # True
```

