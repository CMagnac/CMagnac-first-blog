---
layout: post
title: Back to Basics
date:   2022-11-12 10:00:09 +0200
categories: Python
permalink: /:categories/:title
caption: Image by jeekang on GitHub 
image: privateinvestocat.jpg
---


Taking a one year break to learn on my own was a huge challenge.

Obviously, I have missed some steps during the process which really slowed me down.

The fact is, you need to come back, to iterate, to relearn or consolidate the news or old understanding in a desire of improvement.

<br>

## Fundamentals

### Compiler & Interpreter


The **compiler** is a programm that transforms source code into an object code.

The **interpreter** is a layer of software that works between your program and your computer hardware to get your code running.

<br>

### Coding styles


These are the corner stones that make Python so awsome.

+ Functional
 Every statement is treated as a mathematical equation and any forms of state or mutable data are avoided. to parallel processing
+ Imperative
 This style is especially useful when manipulating data structures and produces elegant yet simple code.
+ Object-Oriented
Relies on data fields that are treated as objects and manipulated only through prescribed methods.
+ Procedural
Tasks are treated as step-by-step iterations where common tasks are placed in functions that are called as needed.

<br>

### What is REPL ?

REPL is an interactive shell.

+ Reads the command you enter
+ Evaluates and execute
+ Print the output
+ Loops back and repeats the process

More informations [here](https://realpython.com/interacting-with-python/).

Otherwise, Jupyter notebook is a REPL based system.

<br>

### Dynamic


Python is **dynamically typed** as the interpreter keeps track of all variables types.
You cannot do anything with the type of data you're working with.

One example : 

```py
print("a" + 1)
```

will return

```py
TypeError: can only concatenate str (not "int") to str
```

<br>

### High & Low

The *machine language* speaks by the computer hardware defines the low-level language or the computer's native language.

Here are characterictics of the high level languages :

+ easier to understand
+ less memory efficient
+ easier to debug
+ easy to maintain
+ portable (run on any supporting plateform)
+ requier a compiler or interpreter

Here are examples of interpreters:

+ Cpython written in C
+ Jypthon written in Java
+ PyPy written in Python
+ IronPython (program implemented in .NET)