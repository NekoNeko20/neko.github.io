---
layout:post
title:95-888 Data Focused Python Recitation
date:2021-07-21
author:Yihan
categories:[courses]
tags:[mcsnote]
comments:true
---



## 95-888 Data Focused Python

This note mainly serves as a **Recitation** for CMU 95-888 Data Focused Python placement test.

### Fundamentals

```
2 ** 3 ** 2 == 2 ** (3 ** 2)
```

#### Built-in Types

`list` : Like an array, where elements are mutable.

`tuple`: Like a record, where elements are immutable.

`set`: Just one of each value/

#### List

- Operations:
  - `append(val)`
  - `insert(idx, val)` insert a value to idx.
  - `remove(val)` removes the first match of val
  - `pop([idx])` return an item at idx, and remove the item
  - `count(val)` count number of vals in list
  - `sort()` sort the list ascending by default
  - `reverse()` reverse the order

#### Sequence Slices

`list` and `str` are sequence types.

`seq[i:j:k]` : from item `i`, to but **not including** item `j` , with step size `k`.

```python
# Example:
#       0  1 2 3  4
ages = [3,12,5,33,68]
ages[0:3:1]
# [3,12,5]
```

#### IDs

Each object is uniquely identified by its id.

```python
id(7)
# 1848132

x = 7
id(x)
# 1848132
```

This proves that x is a reference to 7. But collections can have equal items but not having same ids.

**IDs in comparison: ** `is` and `is not` compare object *ids*, `==` and `!=` compare object *values*.

```python
a = 12
b = 12
a == b
# True
a is b
# True
not a == b
# False
```

#### Copying a Text File

```python
fin = open('dir/*.txt',
					 'rt', # read text
           encoding = 'utf-8')
fout = open('dir/*.txt',
					  'wt',
					  encoding='utf-8')
for line in fin:
	fout.write(line)
fout.close()
```

### More Collections, Type Conversion and Web Scraping

#### Tuple

- A `tuple` is immutable. But a variable can be changed to refer to a different tuple.
- One item tuple:

```python
t = (6)
t
# 6 This is only one number
t = (6,)
t
# (6,) This is a tuple.
```

#### Set

- Operations:

  - `add(val)` 
  - `discard(val)` remove `val` from `set`
  - `remove(val)` remove `val` and fails when `val` is not a member
  - `pop()` remove and return a arbitrary item
  - `clear()` remove all
  - `val` in `s`     is `val` in s? True or False

  - `s1.difference(s2)` s1-s2
  - `s1.symmetric_difference(s2)` Both (s1-s2) and (s2-s1)
  - `s1.intersection(s2)` s1 and s2 have in common
  - `s1.isdisjoint/issubset/issuperset/union(s2)` True or False

- One-Item sets and dicts:

```python
de = {} # empty dict
se = set() # empty set
d1 = {key:value} # one-item dict
s1 = {value} # one-item set
```

#### Web Scraping







### Construction and Comprehension, Exceptions, User Input, Functions, Modules and Intro to Numpy

#### `list` `tuple` and `set` Construction

```python
tup1 = tuple('this is a test')
# ('t', 'h', 'i', 's'....'t','e','s','t')
s1 = set(tup1)
# ['a', 'i', ...'t']
```

- Creating a `dict`

```python
set_of_2_tups = {('a', 12), ('b', 22)}
d1 = dict(set_of_2_tups)
d1
# {"b":22, "a":12}
```

#### Comprehension

```python
# List
[expr for var(s) in tier of [for_or_if ..]]
# Set
{v for v in ...}
# Dict
{k:k**2 for k in ...}
```

#### Defining Functions

- A special syntax `*` in function definitions in Python is used to pass a variable number of arguments.

```python
def printarg(*args):
	for arg in args:
		print(arg)
```

#### Python Modules

- Module May Define......
  - Variables: `pi` `e`
  - Functions: `sqrt` `cos`
  - Classes: `BinaryTree`
- `__name__`: Within any module variable `__name__` is set to the name of the module.

#### Numpy `ndarray`

- `ndarray` always performs better than lists in *size / performance(fixed) / Functionality*
- `list` vs `ndarray`:

```python
lsl = [0,1,2,3,4]
lsl *= 2
# [0,1,2,3,4,0,1,2,3,4] concatenation
a = np.array(lsl)
a += 1
# array([1,2,3,4,5]) # scalar

```

- `copy()`:

```python
a4 = a2[:5].copy()
```

- Creating `ndarray`s:

```python
np.ones(shape)	# ndarray of all 1.0s
np.zeros(shape)  # ndarray of all 0.0s
np.full(shape,val)
np.eye(N) # NxN identity matrix
```

- Boolean Indexes



