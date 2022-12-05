---
layout: post
title: Back to Basics II
date: 2022-12-04 10:00:09 +0200
categories: Python
permalink: /:categories/:title
caption: Image by jeekang on GitHub 
image: privateinvestocat.jpg
---

There are five types of literals used in Python.

*Literal types indicate that a variable has a specific and concrete value.*
[PEP-0586](https://peps.python.org/pep-0586/)

A literal is data whose value is determined by the literal itself. Different kinds of data are coded in different ways, enabling Python (and the human reader of the source code) to determine each literal's type.

## 1. Numeric literals

The built in function isinstance allows you to determine the type of an object.

*isinstance(object, classinfo)*

Return True if the object argument is an instance of the classinfo argument, or of a (direct, indirect, or virtual) subclass thereof.

(Python 3.10.6 Documentation)

### 1.1 Integer

*Int, or integer, is a whole number, positive or negative, without decimals, of unlimited length.* [w3school](https://www.w3schools.com/python/python_numbers.asp)

```py
>>> a = 100_000_000
>>> isinstance(a, int)
True
```

Underscores don't change a literal's value, and their only role is to improve literal readability.

We can use octal representation of integer:

```py
octalint = 0o123 
```

Or hexadecimal

```py
hexaint = 0x123
```

### 1.2 Float

*Floating point is a type designed to store real numbers (in the mathematical sense). Float literals are distinguished from integers by the fact that they contain a dot (.) or the letter e (lower- or upper-case) or both.*
[PCEP](https://pythoninstitute.org/pcep)

```py
>>> a, b, c = .1, 0.01, 1E1
>>> isinstance(a, float)
true
```

### 1.3 Complex

*A Python complex number z is stored internally using rectangular or Cartesian coordinates. It is completely determined by its real part z.real and its imaginary part z.imag.*
[python.org](https://docs.python.org/3/library/cmath.html)

## 2. String literals

*Textual data in Python is handled with str objects, or strings. Strings are immutable sequences of Unicode code points.*
[python.org](https://docs.python.org/3/library/stdtypes.html#textseq)

Unpacking a string: 

```py
>>> a, b, c = '789'
>>> b
'8'
>>> isinstance(b, str)
true
```

## 3. Boolean literals

Boolean literals denote the only two possible values used by the Boolean algebra – their only acceptable denotations are **True** and **False**.

```py
>>> aboolean, bboolean = bool(0), bool(1)
>>> aboolean + bboolean
1
>>> isinstance(b, bool)
True
```

## 4. Literal collections

### 4.1 Lists

Some characteristics of python lists:

+ Sequences are **iterable**.
+ Lists are **mutable**.
+ Initialize in different ways.
+ Index may be positive or negative.
+ IndexError is raised if index out of range.
+ Slice is a portion of the list.

```py
>>> alist = [5, 6, 7, 8, 9]
>>> aslice = slice(2, -1)
>>> alist[aslice]
[7, 8]
```

Next is a list behaviour which is important to understand.

```py
>>> l1 = [5]
>>> l2 = l1
```
Then, each functions apply to l2 will have an impact on l1.

```py
>>> l2.append(True)
>>> l1
[5, True]
```

*You have to differentiate between an object and object identity. Identity is just a logical address to the memory cell of the object.*
[stackoverflow](https://stackoverflow.com/questions/29427131/assigning-a-list-to-another-list-in-a-list-of-lists-in-python)

Otherwise, if you assign the slice of a list to another list you will copy the source list.

```py
>>> l2 = [5, True]
>>> l3 = l2[:]
>>> l3.append(100)
>>> l2
[5, True]
>>> l3
[5, True, 100]
```

### 4.2 Tuples

Tuples are immutable sequences.

How to initialize them ?
```py
t1 = tuple()
t2 = 1,
t3 = 1, 2.5
```

Common characteristics with list:
+ If any of the slice's indices exceeds the permissible range, no exception is raised, the non-existent elements are not taken into consideration.
+ An attempt to access a non-existent tuple element raises the IndexError exception.
+ You can use in and not statement.
+ You canb iterate it with a loop.

### 4.3 Dictionaries

*Dictionaries are Python’s implementation of a data structure that is more generally known as an associative array. A dictionary consists of a collection of key-value pairs. Each key-value pair maps the key to its associated value.*
[realpython](https://realpython.com/python-dicts/)

```py
import string
alphabet = string.ascii_lowercase
aldict = dict(zip(list(alphabet), [_ for _ in range(1, len(alphabet)+1)]))
```

## 5. Special literals

*None is an instance of the NoneType object type. And it is a particular variable that has no object value.*
[geeksforgeeks](https://www.geeksforgeeks.org/python-none-keyword/)

```py
def hello():
    pass
print(hello())
```

This code will return a None value.