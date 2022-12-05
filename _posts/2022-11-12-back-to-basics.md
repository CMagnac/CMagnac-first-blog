---
layout: post
title: Back to Basics
date: 2022-11-12 10:00:09 +0200
categories: Python
permalink: /:categories/:title
caption: Image by jeekang on GitHub 
image: privateinvestocat.jpg
---
Taking a one year break to learn on my own was a huge challenge.

Obviously, I have missed some steps during the process which really slowed me down.

The fact is, you need to come back, to iterate, to relearn or consolidate the news or old understanding in a desire of improvement.

In this post, we talk about a bunch of python **fundamentals**.

<br>

## Compiler & Interpreter

To make complex calculus, a computer need a language which will be implement by the programmer.

As a programmer, we can talk to our computer in the same way we use the natural language.

We use a set of command, called the **instruction list**.

Natural language and programming language can be compare on their structures : an alaphabet, a lexis, a syntax and semantics.

Compare to low programming language with their instructions list, a high programming language has to be define in a human readable way.

The programming language has to be interprete by an intrepretor before the computer core can use it to make things work.

There are two different way to transform a high level language into a computer language : **compiler** and **interpreter**.

In a compiler you transform the code only once into an excecutable programm that you can spread worldwide.

Whereas, with an intepreter you perform the code multiple time, each time it has to be run.

The interpretor read the file from left to right and up to bottom and raise an error if there are any mistakes in the semantic, vocabulary or syntax.

The file which contains the code is named a source file.
The source code is the high level language.

<br>

## Coding styles

These are the corner stones which make Python so awsome.

### The Functional

Every statement is treated as a mathematical equation and any forms of state or mutable data are avoided.

### The Imperative

This style is especially useful when manipulating data structures and produces elegant simple code.

### The Object-Oriented

It relies on data fields that are treated as objects and manipulated only through prescribed methods.

### The Procedural

Tasks are treated as step-by-step iterations where common tasks are placed in functions that are called as needed.

<br>

## REPL

REPL is an interactive shell.

+ Reads the command you enter
+ Evaluates and executes
+ Prints the output
+ Loops back and repeats the process

More informations [here](https://realpython.com/interacting-with-python/).

Jupyter notebook is a REPL based system.

<br>

## Dynamic

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

## High

The machine language speaks by the computer hardware defines the low-level language or the computer's native language.

Here are characterictics of the high level languages :

+ Easier to understand
+ Less memory efficient
+ Easier to debug
+ Easy to maintain
+ Portable (run on any supporting plateform)

Here are examples of interpreters:

+ Cpython written in C
+ Jypthon written in Java
+ PyPy written in Python
+ IronPython (program implemented in .NET)