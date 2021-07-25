---
layout: post
title: 95-888 Data Focused Python Recitation
date: 2021-07-21
Author: Yihan
categories: [courses]
tags: [mcsnote]
comments: true
---



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

`Beautiful Soup` can be used to parse `html` or `xml` documents.

```python
from urllib.request import urlopen
from bs4 import BeautifulSoup
html = urlopen(url)
bsyc = BeautifulSoup(html.read(), 'lxml')
fout = open(txt, 'wt', encoding='utf-8')
fout.close()
```

#### Example Functions

```python
bsyc.title # Returns the first <title> tag
bsyc.title.string # Returns the content of the first title
bsyc.title.parent.name # returns parent tag
bsyc.find_all('title') # create list of all titles
```

#### Scraping a Yield Curve

```python
table_list = bsyc.findAll('table')
tc_table_list = bsyc.findAll('table', 't-chart')
tc_table = tc_table_list[0]
for c in tc_table.children:
	print(str(c)[:50])
for c in tc_table.children:
	for r in c.children:
		print(r.contents)
```



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

```python
b_rows = [True, False, True]
a1[b_rows, :]
# Select row 0 and row 2.
a1[a1 < -5] = 8
# Threshold: -5, larger: 8
```

### Intro to Pandas

#### Scalar Arithmetic

- `math` does not work on pandas
- Slicing:

```python
s1[:2] # to but not including s1[2]
s3['AAPL':'CSCO'] # 'AAPL' to and including 'CSCO'
```

#### `DataFrame` Cell

- Retrieve a *cell*:
  - `f1['CEO_buy'][2]   # True`  Not efficient!
  - `f1.loc[2]['CEO_buy']    # True`
  - `f1.loc[2, 'CEO_buy']    # True` 
- Delete a column: `del`
- Add row: `f1.loc[4] = [....]` *Upcast: If the data types of the new row don't match the existing , the column types will be upcast, and deleting this row will not affect the upcast*
-  `loc` and `iloc`:
  - `loc` gets rows and columns using `labels`
  - `iloc` gets rows and columns using `integers`
- Missing value
  - `f2.add(f3, fill_value=0)`  where `fill_value` fills `f2` but not f3
- Sorting:

```python
f4.sort_index() # sort rows
f4.sort_index(axis=1) # sort cols
# args: ascending = True
```

- Some Summary Statistics:

```python
f5.sum() # Series of column sums
f5.mean()
f5.var() # unbiased
f5.describe() # count\mean\std\min\25%\50%\75%\max
```

- Other Operations:
  - `idxmin(), idxmax()`: row of min, max
  - `prod()` : product of row vals by col
  - `cumsum(), cumprod()`: cumulative sum/product
  - .....and more

### Regular Expressions, Reading & Writing Formatted Data

| Expression | Meaning                                                      |
| ---------- | ------------------------------------------------------------ |
| `c`        | Matches the character `c`                                    |
| `\c`       | Matches `c`, even if `c` is a regular expression special character |
| `^`        | Matches the start of a string                                |
| `$`        | Matches the end of a string                                  |
| `.`        | Matches any single character in a string                     |
| `[abc]`    | Matches *one* character, either *a* or *b* or *c*            |
| `[^abc]`   | Matches one character, which is nor a or b or c              |
| `[a-z]`    | Matches *one* character, in range a thru z                   |
| `c*`       | Matches a sequence of 0 or more occurences of `c`            |
| `e1|e2`    | Matches *e1* or *e2*                                         |
| `e+`       | Matches a sequence of 1 or more occurences                   |
|            |                                                              |

#### Raw Strings

- To search a `\`

```python
# pat = '\\\\'
pat = r'\\'
```

#### Other Functions

```python
re.findall()    # return matches as list of strings
re.split()      # split string by occurrences of expressions
re.sub()        # replace
```

### Parsing HTML Tables Using Pandas

```python
tb1_list = pd.read_html(html, attrs={'class':'t-chart'},header=0,index_col=0)

type(tb1_list[0])
# <class 'pandas.core.frame.DataFrame'>
```

### JSON API Data

```python
sbdf = pd.read_json(json_link) # https://.....json
type(sbdf)
# DataFrame
```

### String Operations

```python
# Capitalization
s = 'this is a test'
s.capitalize()
# 'This is a test'
s.title()
# 'This Is A Test'
s.upper()
# 'THIS IS A TEST'
s = 'word'
s2 = s.center(10)
s2
# '   word   '
len(s2)
# 10
s2 = s.center(10, '-')
s2
# '---word---'
s2.strip()
# 'word'
s2.lstrip()
#'word   '
s2.rstrip()
#'   word'
s.count('t')
# 3
s.find('t') # much like .indexOf
# 0
```

#### String Formatting

- `d` : for *decimal(base 10)* **int**
- `s` : for *string*
- `f` : for *fixed-point* float
- `e` : for *exponential* float

#### String Formatting Justification

- `{:<width c}` left-justified
- `{:^width c}` entered
- `{:>width c}` right-justified

For **float** output, you can specify a **specification**.

`{:width.precision f}` float in width, fixed point, and precision after decimal point.

### Reading & Writing Files Revisit

#### Text File

```python
fin = open('dir/*.txt','rt',encoding='utf-8')
fout = open('dir/*.txt','wt',encoding='utf-8')
for line in fin:
	fout.write(line)
fout.close()
```

#### Binary File

```python
fin = open(..., 'rb',...)
fout = open(..., 'wb', ...)
```

#### CSV

```python
with open('....csv', 'r') as file:
	for line in file:
		print line
    
with open('....csv', 'w') as file:
  writer = csv.writer(file)
  writer.writerow(["index",...])
  ...
```

