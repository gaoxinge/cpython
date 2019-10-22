## 介绍

- [Python源码剖析](https://book.douban.com/subject/3117898/)
- 闲谈后
  - [逃不开的 CPython](https://zhuanlan.zhihu.com/manjusakac)
  - [源码读Python](https://zhuanlan.zhihu.com/c_168776105)
- cpython internals
  - [info](http://pgbovine.net/cpython-internals.htm)
  - [course](http://courses.pgbovine.net/csc253/)
  - [video](http://v.youku.com/v_show/id_XMTQ0NzY5ODcyOA==.html?spm=a2hzp.8244740.0.0&f=26549146)
  - [note]()
  - [summary](https://medium.com/@dawran6/getting-started-with-python-internals-a5474ccb8022)
- [amygdalama/python-internals](https://github.com/amygdalama/python-internals)
- Python’s Innards
  - [Python’s Innards: Introduction](https://tech.blog.aknin.name/2010/04/02/pythons-innards-introduction/)
  - [Python’s Innards: Objects 101](https://tech.blog.aknin.name/2010/05/12/pythons-innards-objects-101/)
  - [Python’s Innards: Objects 102](https://tech.blog.aknin.name/2010/05/19/pythons-innards-objects-102/)
  - [Correction for ‘Python’s Innards: Objects 102’](https://tech.blog.aknin.name/2010/05/20/correction-for-pythons-innards-objects-102/)
  - [Python’s Innards: pystate](https://tech.blog.aknin.name/2010/05/26/pythons-innards-pystate/)
  - [Python’s Innards: Naming](https://tech.blog.aknin.name/2010/06/05/pythons-innards-naming/)
  - [Python’s Innards: Code Objects](https://tech.blog.aknin.name/2010/07/03/pythons-innards-code-objects/)
  - [Python’s Innards: for my wife](https://tech.blog.aknin.name/2010/07/04/pythons-innards-for-my-wife/)
  - [Python’s Innards: Interpreter Stacks](https://tech.blog.aknin.name/2010/07/22/pythons-innards-interpreter-stacks/)
  - [Python’s Innards: Hello, ceval.c!](https://tech.blog.aknin.name/2010/09/02/pythons-innards-hello-ceval-c-2/)
- [summary](https://github.com/gaoxinge/cpython/tree/python_study/note/summary)

## compiler

- [PEP 339 -- Design of the CPython Compiler](https://www.python.org/dev/peps/pep-0339/)
- [Python internals: Working with Python ASTs](https://eli.thegreenplace.net/2009/11/28/python-internals-working-with-python-asts)
- [Python internals: adding a new statement to Python](https://eli.thegreenplace.net/2010/06/30/python-internals-adding-a-new-statement-to-python)
- [Python internals: Symbol tables, part 1](https://eli.thegreenplace.net/2010/09/18/python-internals-symbol-tables-part-1)
- [Python internals: Symbol tables, part 2](https://eli.thegreenplace.net/2010/09/20/python-internals-symbol-tables-part-2)
- [Python internals: how callables work](https://eli.thegreenplace.net/2012/03/23/python-internals-how-callables-work)
- [Understanding UnboundLocalError in Python](https://eli.thegreenplace.net/2011/05/15/understanding-unboundlocalerror-in-python)

## virtual machine

- [Introduction to the Python Interpreter, Part 1: Function Objects](http://akaptur.com/blog/2013/11/15/introduction-to-the-python-interpreter/)
- [Introduction to the Python Interpreter, Part 2: Code Objects](http://akaptur.com/blog/2013/11/15/introduction-to-the-python-interpreter-2/)
- [Introduction to the Python Interpreter, Part 3: Understanding Bytecode](http://akaptur.com/blog/2013/11/17/introduction-to-the-python-interpreter-3/)
- [Introduction to the Python Interpreter, Part 4: It's Dynamic!](http://akaptur.com/blog/2013/12/03/introduction-to-the-python-interpreter-4/)
- [A Python Interpreter Written in Python](http://www.aosabook.org/en/500L/a-python-interpreter-written-in-python.html)
- [nedbat/byterun](https://github.com/nedbat/byterun)

## data model

- [Python objects, types, classes, and instances - a glossary](https://eli.thegreenplace.net/2012/03/30/python-objects-types-classes-and-instances-a-glossary)
- [The fundamental types of Python - a diagram](https://eli.thegreenplace.net/2012/04/03/the-fundamental-types-of-python-a-diagram)
- [Python object creation sequence](https://eli.thegreenplace.net/2012/04/16/python-object-creation-sequence)
- [Under the hood of Python class definitions](https://eli.thegreenplace.net/2012/06/15/under-the-hood-of-python-class-definitions)

## 引用计数

- [扩展Python模块系列(四)----引用计数问题的处理](https://blog.csdn.net/kof2019/article/details/77824473)
- [Python引用计数(Reference Count)](https://www.jianshu.com/p/ecea193abec4)

## cpython extension

- [Extending and Embedding the Python Interpreter](https://docs.python.org/2/extending/index.html)
- [Python/C API Reference Manual](https://docs.python.org/2/c-api/index.html)
- [A Whirlwind Excursion through Python C Extensions](https://nedbatchelder.com/text/whirlext.html)
- [pythonc-api-1](https://jayrambhia.com/blog/pythonc-api-1)
- [pythonc-api-reference-counting](https://jayrambhia.com/blog/pythonc-api-reference-counting)
- [pythonc-api-making-a-type](https://jayrambhia.com/c++/daily%20posts/python/technical/blog/pythonc-api-making-a-type)
- [浅谈Python C扩展](https://blog.csdn.net/fitzzhang/article/details/79212411)

## other

- [cython](https://github.com/cython/cython)
  - [Cython: C-Extensions for Python](https://cython.org/)
  - [Cython 基本用法](https://zhuanlan.zhihu.com/p/24311879)
  - [用Cython加速Python到“起飞”](https://www.jianshu.com/p/fc5025094912)
  - [Cython三分钟入门](http://python.jobbole.com/87368/)
  - [用 Cython 造个轮子](https://zhuanlan.zhihu.com/p/38212302)
- [SWIG](https://github.com/swig)
- [numba/numba](https://github.com/numba/numba)
- [pybind/pybind11](https://github.com/pybind/pybind11)
- [Boost.Python](https://www.boost.org/doc/libs/1_58_0/libs/python/doc/)