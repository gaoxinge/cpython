# compile in python

## flow

From [PEP 339 -- Design of the CPython Compiler](https://www.python.org/dev/peps/pep-0339/), we have

- Parse source code into a parse tree (Parser/pgen.c)
- Transform parse tree into an Abstract Syntax Tree (Python/ast.c)
- Transform AST into a Control Flow Graph (Python/compile.c)
- Emit bytecode based on the Control Flow Graph (Python/compile.c)

## abstract syntax tree

From [ast — Abstract Syntax Trees](https://docs.python.org/3/library/ast.html#abstract-grammar), we can operate on ast easily.

### get a node / AST class

```python
import ast

node = ast.UnaryOp(ast.USub(), ast.Num(5, lineno=0, col_offset=0), lineno=0, col_offset=0) 

node = ast.BinOp(ast.Str('xy'), ast.Mult(), ast.Num(3))
node = ast.fix_missing_locations(node)  # fill lineno and col_offset

node = ast.parse('1+2', mode='eval')  # equivalent to compile('1+2', filename='<string>', mode='eval', flags=ast.PyCF_ONLY_AST)
```

### operate on node / AST class

```python
import ast

class MyVisitor(ast.NodeVisitor):
    def visit_Str(self, node):
        print 'Found string "%s"' % node.s


node = ast.parse('''
favs = ['berry', 'apple']
name = 'peter'

for item in favs:
    print '%s likes %s' % (name, item)
''')

MyVisitor().visit(node)
```

```python
import ast

class MyVisitor(ast.NodeVisitor):
    def visit_Str(self, node):
        print 'Found string "%s"' % node.s


class MyTransformer(ast.NodeTransformer):
    def visit_Str(self, node):
        return ast.Str('str: ' + node.s)


node = ast.parse('''
favs = ['berry', 'apple']
name = 'peter'

for item in favs:
    print '%s likes %s' % (name, item)
''')

MyTransformer().visit(node)
MyVisitor().visit(node)
```

### generate code from ast

- [andreif/codegen](https://github.com/andreif/codegen)
- [berkerpeksag/astor](https://github.com/berkerpeksag/astor)

## symbol table

Symbol tabel is created in step3 and used to generate byte code in step4.

## code object / byte code

### generate code from bytecode

- [Exploring and decompiling python bytecode [closed]](https://stackoverflow.com/questions/1149513/exploring-and-decompiling-python-bytecode)

## pyc