# Debugging and handling errors

---

<details>
    <summary>Debugging / handling errors</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/9w2EIASrUvQ?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

We all make mistakes and in programming we have some tools to catch them. Those errors could be syntax errors (`SyntaxError`), in which case we should check the reference to see what is the proper use of Python we are trying to do. 

There could be name errors (`NameError`) when we are trying to access something (variable or a function for example) which was not defined or we misspell the name of it. 

We can also have a `TypeError` when we are trying to use some method on the inappropriate data type, like looping on non-iterable item for example. 

`IndexError` occurs when we are trying to access something from a string or a list with index which is outside of the range of indexes for this item. 

`ValueError` can arise if a built-in operation or function gets an argument of valid data type but with inappropriate value, like if we calling `int('banana')` function but provide a string as an argument which can not be converted into a number. 

`KeyError` arises when trying to get something from a dictionary with a key which doesn't exist there. 

`AttributeError` is thrown when we are trying to use an attribute on a variable which doesn't exist, like `'banana'.foo`, this string doesn't have an attribute `foo`. 

There are more types of errors in Python and most of them are very much self-explainatory, feel free to check [the official docs](https://docs.python.org/3/library/exceptions.html).

## Raising your own errors

To create a custom error you can use `raise` keyword. It can make a custom error of certain type to be thrown by your code in case of some specific condition. 

For example, we can make a custom error of `ValueError` with our custom error message 'Bad value provided' just like this:

```python
raise ValueError('Bad value provided')
```

For example we have a simple function 'divide' which takes 2 numbers and returns results of division of num1 by num2. We will have a custom error raised in case second number is 0:

```python
def divide(n1,n2):
     if n2 == 0:
             raise ValueError('Can not divide by 0!!!')
     return n1 / n2
 
divide(4,2) # call it with valid numbers
2.0 # get back the results 

divide(4,0) # call it with second argument 0
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
#   File "<stdin>", line 3, in divide
# ValueError: Can not divide by 0!!!   
# ↑↑↑ get back our own custom error message ↑↑↑
```
# Handling errors

Every time we have an error our code breaks and stops, we do not want it to happen so we can prepare for a possible error to arise with try/except blocks to catch the errors/exceptions and do something with them. 

## try / except

Let's say we want to use our `divide()` function and in case of error we want to catch it and not break the code: 

```python
def divide(n1,n2):
	if n2 == 0:
		raise ValueError('Can not divide by 0!!!')
	return n1 / n2
 
try:
	divide(1,0)
except ValueError as err:
	print(err)
 
# Can not divide by 0!!!

# We have our custom error message and the code doesn't break
```

Another example could be if let's say we have a function which returns a value from the dictionary by it's key, in case the key doesn't exist in the object we will have an error, so we can use try/except to prepare for this situation:

```python
def getValbyKey(dict, key): 
	try:
	        # if this key is in the dictionary we will return it's value
	        return dict[key]
	except KeyError:
	        print(f'The key {key} does not exist in provided dictionary')
	        return None


getValbyKey({'name':'Morty','age':14},'name') # trying with the key which exists
# 'Morty'

getValbyKey({'name':'Morty','age':14},'lastname') # trying with key which doesnt exist
# The key lastname doesnt exist in provided dictionary
```

We can extend our logic of treating the possible errors by adding `else` and `finally` to our try/except statements:

```python
try:
	# do some code here
except:
	# will run if there was an error
else:
	# will run if there was not an error
finally:
	# will run in any case 
```

So now we can have something like this:

```python
def getValbyKey(dict, key): 
	try:
		print (dict[key])
	except KeyError:
		print(f'The key {key} does not exist in provided dictionary')
	else:
		print('No errors and you see you value for the key')
	finally:
		print('Will run in any case')


getValbyKey({'name':'Morty','age':14},'name') # trying with the key which exists
# Morty   <<< This is from try
# No errors and you see you value for the key   <<< this is from else
# Will run in any case   <<< this is from finally

getValbyKey({'name':'Morty','age':14},'lastname') # trying with key which doesnt exist
# The key lastname does not exist in provided dictionary   << this is from except
# Will run in any case   <<< this is from finally 
```

And we can have more than one exceptions:

```python
def divide(n1,n2):
	try:
		return n1 / n2
	except ZeroDivisionError:
		return ('Can not divide by 0!!!')
	except TypeError:
		return ('n1 and n2 both should be numbers')

divide(2,3)
# 0.6666666666666666
divide(2,0)
# 'Can not divide by 0!!!'
divide(2,'banana')
# 'n1 and n2 both should be numbers'
```

Or we can put the possible errors we handle in the `except` into a tuple and print the error dynamically:

```python
def divide(n1,n2):
	try:
		return n1 / n2
	except (ZeroDivisionError, TypeError) as err:
		print(f'Something went wrong. Error: {err}')

divide(2,3)
# 0.6666666666666666
divide(2,0)
# Something went wrong. Error:  division by zero
divide(2,'banana')
# Something went wrong. Error:  unsupported operand type(s) for /: 'int' and 'str'
```


# Debugging with pdb 

pdb stand for Python Debugger and to use it we need to import it first.

```python
import pdb
# now we can use it:
pdb.set_trace()
```

If we will put pdb into our code Python will pause at the position of debugger and in the terminal we will be able to go through the rest of the code line by line:

```python
import pdb
def doSomeMath(num):
	pdb.set_trace()
	add = num + 1
	subtr = add -10
	div = subtr / 5
	multy = div * 50
	return multy

doSomeMath(99)
```

We will see this:
```
-> add = num + 1
(Pdb) 
```

The commands for debugger are:
l - list
n - move to next line
p = print
c - continue executing code and finish debugging
q - quit debugger

So if we type 'n' now we will go to the next line and when type 'l':
```
-> add = num + 1
(Pdb) n
> /Users/gk/sandbox/python_exercises/debugging.py(5)doSomeMath()
-> subtr = add -10
(Pdb) l
  1  	import pdb
  2  	def doSomeMath(num):
  3  		pdb.set_trace()
  4  		add = num + 1
  5  ->		subtr = add -10
  6  		div = subtr / 5
  7  		multy = div * 50
  8  		return multy
  9  	
 10  	doSomeMath(99)
[EOF]
(Pdb) 
```
We can check the value of 'add' inside our function now: 
```
(Pdb) p add
100
(Pdb) 
```

So in this way we can execute code line by line and see all the values we have inside our code during the execution. 





