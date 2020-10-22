# Learn Haskell

[Types and Classes](#types-and-classes)

## GHC 
```
ghci
:load 'filename.hs'
:r
:edit name
:edit
:type expr
:?
:quits
```

## Example of haskell 
```
double x = x + x
quadruple x = double (double x)
```

## Naming requirements
- Function and argument names must begin with a lower-case letter.
- By convention, list arguments usually have an **'s'** suffix on their name. (eg; xs, ns, nss)

## The Layout rule
- In a sequence of definitions, each definition must begin in precisely the same column.
- The layout rule avoids the need for explicit syntax to indicate the grouping of definitions.
``` 
a = b + c
    where
        b = 1
        c = 2
d = a * 2 
```

## Types and Classes
A type is a name for a collection of related values. (eg; **Bool** contains **True** or 
**False**)  

### Type Errors
Applying  a function to one or more arguments of the wrong type is called a **type error.**

```
> 1 + False
Error
```

### Types in haskell
If evaluating an expression **e** would produce a value of type **t**, then **e** has type **t** written,
```
e::t
```
- Every well formed expression has a type, which can be automatically calculated at compile time using a process called type inference.
- All type errors are found at compile time, which makes programs safer and faster by removing the need for type checks at run time.
```
> :type not False
not False :: Bool
```

### Basic types
- **Bool** - logical values
- **Char** - single characters
- **String** - strings of characters
- **Int** - fixed-precision integers
- **Integer** - arbitrary-precision integers
- **Float** - floating-point numbers

### List types
A list is sequence of values of the same type:
```
False,True,False] :: [Bool]
[’a’,’b’,’c’,’d’] :: [Char]
```
**[t] is the type of lists with elements of type t.**

- The type of a list says nothing about its length.
```
[False,True] :: [Bool]
[False,True,False] :: [Bool]
```
- The type of the elements is unrestricted.  For example, we can have lists of lists:
```
[[’a’],[’b’,’c’]] :: [[Char]]
```

## Tuple types

