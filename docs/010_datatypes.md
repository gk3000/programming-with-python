# Data types


Python is loosely-typed language which means the type of variable is defined by it's value. Different data types are used to define what we can do with different types of data. For example, we can do math with numbers but we can not do math with text. 

In Python we have these data types:

## Strings:

### str

For text we use strings -- data type is called `str` -- examples: "banana", 'Luke', "555"

---

## Numbers:	

### int

-- whole numbers such as 3, 13, 69 -- just numbers without any quotation marks 

### float

-- numbers with decimal point, like 3.14 or 101.1 or even 99.0

### complex

-- numbers with a "j" as the imaginary part (we can ignore that for now, for more info go to https://docs.python.org/3.7/library/functions.html#complex)

---

## Sequence Types:	

### list

-- list is an ordered sequence of several records inside square brackets, like ['luke', 100, 'force', 5.5]

### tuple

is orderd immutable sequence of records inside parenthesis like ('luke', 100, 'force', 5.5)

### range

-- immutable sequence of numbers which is commonly used for looping:
range (5) gives numbers from 0 to 5 (exclusively) -- 0-4
range (0,5) -- numbers 0-4
range (0,5,2) -- 0, 2, 4 -- in this case third argument would be a step

To diplay the range we can use `list()` function:
```python
list(range(5))
list(range(0,10))
list(range(4,16,2))

nums = range(10,0,-1)
list(nums)
```

---

## Mapping Type:	

### dict

is unordered list of key/value pairs like {'name':'Luke', 'surname':'Skywalker'}

---

## Set Types:	

### set

-- this one is unordered collection of unique records inside the curly brackets like {'a','b','c'} -- can't have {'a','a'}, Python will reduce it to {'a'}

<!-- frozenset -->
---

## Boolean Type:	

### bool

-- this one can only be `True` or `False`, very useful for keeping track of state with only 2 possible options -- true/false, on/off, yes/no, etc.

---

## Binary Types:	

### bytes, bytearray, memoryview

---

## None

There is a special type of value in Python to represent empty value and it is `None`. The data type for None is NoneType. We use it to give an empty value to some variable, let's say we describe a person:

```python
name = 'Bob'
age = '30'
cats_owned = None
```

Bob doesn't have a cat.

<img src="./pics/grumpy-cat-foto.jpg">

---

## type()

To determine a data type of some variable we use `type()` function. For example:

```
type('banana')
```

will return `<class 'str'>` showing that type of `"banana"` in quotes is a string. And for sure we can check data type of any variable:

```python
name = 'Bob'
age = 50
type(name)
# <class 'str'>
type(age)
# <class 'int'>
```

So far so good, let's move on to the next section! 🛫
