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
- **++** to concatenate two lists
- **:** to add an element to the front of a list only one 
- 1:2:3:[] this is the same as [1,2,3] (syntactic sugar)
- [1,2,3,4] !! 0 gives the 1st element from the list (!!)

#### Function operations of list
- **head** - gives the first element from the list
- **tail** - gives all the elements but first
- **last** - gives the last element from the list
- **init** - gives all the elements but the last
- **length** - gives the length of the list
- **null** - checks if the list if empty or not
- **reverse** - gives the list in reverse order
- **take** - gives the n amount of numbers from the list "take 3 [4,5,7,8,5,3]" -> [4,5,7]
- **drop** - delete the n number of elements from the list "drop 3 [4,5,7,8,9]" -> [8,9] 
- **maximum**, **minimum**, **sum**, **product**
- **elem** - check whether element exists in a list "4 'elem' [3,4,6,8,7]" -> True


- `[1..10]` generate numbers from 1 - 10 same for letters
- `[2,4..10]` generate numbers that /2 from 1 - 10 
- `[20,19..1]` gives 20 - 1 in a list
- `take 10 [2,4..]` gives the first 10 multiples of 2

- cycle - cycle takes a list and go through infinite time
- repeat - takes an element and repeat it infinite time
- replicate - "replicate 3 10" -> [10, 10, 10]

#### List comprehension (filtering, predicate, condition) 
- `[x*2 | x<- [1..10]]` - generate a list of numbers from 1 - 10 and assign each number to x then times it by 2
- `[x*2 | x<- [1..10], x*2 >= 12]` - only output the numbers which are greater than or equal to 12
```
boomBang xs = [if x < 10 then "BOOM" else "BANG!" | x <- xs, odd x]
```
- [x | x <- [1..10], x /= 5, x /= 7, x/= 1] - you can have as many predicates as you want
- an element must satisfy all the predicates to be included in the resulting list

- `[x*y | x <- [2,5,10], y <-[6,8,10]]` draw from several lists 
- ^ output this [12,16,20,30,40,50,60,80,100]
```
 let nouns = ["hello","car","pool","cricket","wow"]
 let verbs = ["ride","run","climb","swim"]
ohNo nouns verbs = [noun ++" "++ verb | noun <- nouns, verb <- verbs]
```
- `length' xs = sum(1 | _ <- xs)` "_" is a wild card
```
removeNonUpper xs = [c | c <- xs, c `elem`['A'..'Z']]
removeUpper xs = [c | c <- xs, c `elem`['a'..'z']]
```
```
let xxs = [[1,3,5,2,3,1,2,4,5],[1,2,3,4,5,6,7,8,9],[1,2,4,2,1,6,3,1,3,2,3,6]] 
getEven xxs = [[x | x <- xs, even x] | xs <- xxs]
```

- fst takes a pair and returns its first component
- fst (8,10) return 8 

- snd takes a pair and return its second component
- snd (8,10) return 10

- zip - takes two lists and pair them together
- `zip [1,2,3,4] [3,4,5,3,8]`
- `zip [1..5] ["one", "two", "three", "four", "five"]`
```
triangles = [(a,b,c) | a <- [1..10], b <- [1..10], c <- [1..10], a^2 + b^2 == c^2, a+b+c == 24]

rightTriangles = [(a,b,c) | c <- [1..10], b <- [1..c], a <- [1..b], a^2 + b^2 == c^2, a+b+c == 24]
```
## Tuple types

