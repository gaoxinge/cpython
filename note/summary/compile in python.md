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

Symbol tabel is created in step3 and used to generate byte code in step4. From [symtable — Access to the compiler’s symbol tables](https://docs.python.org/3.7/library/symtable.html), we can operate on ast easily.

### get a symbol table

```python
import symtable
table = symtable.symtable("def some_func(): pass", "<string>", "exec")
table = symtable.symtable("""
def outer(aa):
    def inner():
        bb = 1
        return aa + bb + cc
    return inner
""", "<string>", "exec")
```

### operate a symbol table

```python
import symtable


def describe_symbol(sym):
    assert type(sym) == symtable.Symbol
    print("Symbol:", sym.get_name())

    for prop in [
            'referenced', 'imported', 'parameter',
            'global', 'declared_global', 'local',
            'free', 'assigned', 'namespace']:
        if getattr(sym, 'is_' + prop)():
            print('    is', prop)


# test1
table = symtable.symtable("""
def outer(aa):
    def inner():
        bb = 1
        return aa + bb + cc
    return inner
""", "<string>", "exec")

inner_table = table.get_children()[0].get_children()[0]
aa_symbol = inner_table.lookup("aa")
bb_symbol = inner_table.lookup("bb")
cc_symbol = inner_table.lookup("cc")
describe_symbol(aa_symbol)
describe_symbol(bb_symbol)
describe_symbol(cc_symbol)

print("=======================================================")

# test2 
table =  symtable.symtable("""
def outer():
    global gg
    return ff + gg
""", "<string>", "exec")

outer_table = table.get_children()[0]
ff_symbol = outer_table.lookup("ff")
gg_symbol = outer_table.lookup("gg")
describe_symbol(ff_symbol)
describe_symbol(gg_symbol)
```

```python
import symtable


def describe_symtable(st, recursive=True, indent=0):
    def print_d(s, *args):
        prefix = ' ' * indent
        print(prefix + s, *args)

    assert isinstance(st, symtable.SymbolTable)
    print_d('Symtable: type=%s, id=%s, name=%s' % (
                st.get_type(), st.get_id(), st.get_name()))
    print_d('  nested:', st.is_nested())
    print_d('  has children:', st.has_children())
    print_d('  identifiers:', list(st.get_identifiers()))

    if recursive:
        for child_st in st.get_children():
            describe_symtable(child_st, recursive, indent + 5)


table = symtable.symtable("""
def outer(aa):
    def inner():
        bb = 1
        return aa + bb + cc
    return inner
""", "<string>", "exec")


describe_symtable(table)
```

## code object / byte code

### generate code from bytecode

- [Exploring and decompiling python bytecode [closed]](https://stackoverflow.com/questions/1149513/exploring-and-decompiling-python-bytecode)

## pyc