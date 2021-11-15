# Functions

---

<details>
    <summary>Functions</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/brHZgM0e4Z0?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

## Defining a function

Functions are a way for us to minimise repetition in our code. We use them to execute the same piece of code multiple times without rewriting it. We can have a block of code, put it inside a function and then reuse as many times as we want by calling that function by name. 

A function can take some input data which is called arguments and return some output, a pure function is a function without any side effects and which is returning the same output if the same input data is providede and the pure functions are considered to be the best type of functions we can write 🤓

Another way to think about a function is as a predefined set of steps to do with or without input data provided. Like a function which adds 2 numbers and returns the sum of them -- no matter what numbers we will pass into it it will always to the same task -- add them together and return a sum. 

Let’s see a very basic example of a function:

```python
def say_hello():
	print('Hello world!')
```

Here we have defined a function called say_hello that when executed will print out the phrase Hello world!. This is known as function declaration, we defined the function and now it can be used or called.

Keep in mind that the code inside it will not be executed until the function is called.

In order to call our function we need to write the name of the function followed by parentheses.

```python
say_hello()
```

Here we are executing, or calling our function.

---


## Arguments

Functions can take arguments (also called parameters). Arguments are data that comes from outside the function and can be used inside it. Arguments in the definition of a function are just placeholders which would be substituted by actual data within a function call:

```python
def say_something(something):
	print(something)
```

Now this function expects some data in a function call and inside it this data would be known by the name of `something` and this something would be printed out. Now let's call the function and pass something to say:

```python
saySomething('Are you talking to me?')
# the value of our argument something is now 'Are you talking to me?'

saySomething(2+2)
# the value of our argument something is now 4
```

You can pass as many arguments as you like to your function, let’s see an example where we create a super basic calculator that only adds two numbers.

```python
def calculator(a, b):
	print(a + b);

calculator(10, 5)
# 15
```

> Arguments or parameters? In a function definition you define parameters, in a function call the data you pass to the parameters is arguments.

## Default parameters

Default parameters allows you to set default values for your function parameters if no value is passed or if undefined is passed. 

If a function expects arguments and we call it without passing the data in it will throw an error:

```python
def sum( num1, num2):
	print(num1+num2)

sum()

# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# TypeError: sum() missing 2 required positional arguments: 'num1' and 'num2'
```

So to prevent this in case our function would be executed without actual data passed we can define the default parameters:

```python
def sum( num1 = 10, num2 = 20):
	print(num1+num2)

sum()
# 30

sum(50)
# 70
# in this case num1 would be 50 from the function call and num2 would be 20 from the default parameter
```

> The order of arguments matters, so if your function expects 2 arguments but you call it with only one, it will be always the first argument with data and the second one would be empty (or it will use default parameter if defined).

> Arguments only exist inside a function, so num1 and num2 from the function above will not be available by this names outside this function.

### Keyword arguments

As by default the arguments in the function call are taken in order for parameters in the functon definition there is a special way to change that with keyword arguments, take a look at this example:

```python
def fullname(first_name,last_name):
	print(f'Hello Mrs/Mr {last_name}, can we call you {first_name}?')

fullname('Mary','Jane')
# Hello Mrs/Mr Jane, can we call you Mary?
# Makes total sense, right???

fullname('Jane','Mary')
# Hello Mrs/Mr Mary, can we call you Jane?
# This doesn't make any sense, because the order or parameters and arguments is not matching

fullname(first_name = 'Mary', last_name= 'Jane')
# Hello Mrs/Mr Jane, can we call you Mary?
# PErfect again

fullname(last_name = 'Jane', first_name= 'Mary')
# Hello Mrs/Mr Jane, can we call you Mary?
# Also perfect, the keyword arguments order can be different from the order of parameters
```

## Return

So far all we did was to log the result of our function, but if we do it this way, our functions has no output because it returns nothing. Normally we want a function to return or give back the output so we can use it later in our code. 

Simply seeing something in the terminal from runnin `print()` for example is not actually returning anything, so we can't get that output of the function, let’s see what it means…

```python
def sum(num1,num2):
	print(num1+num2)
sum(1,4)
# 5
```

So now if we will try to save the results in a variable, we will see that it is empty:

```python
results = sum(1,4)
print(results)
# None
```

To save the output of the function `sum` in the variable `results` our function should return the sum of these 2 numbers like that:

```python
def sum(num1,num2):
	print(num1+num2)
	return(num1+num2)

results = sum(1,4)
print(results)
# 5
```

Yay! So with `return` keyword we can return some output from a function. 

**Important to remember**:

–– `return` stops the function, any code inside the function after `return` which triggered would be ignored

```python
def sum(num1,num2):
	print(num1+num2)
	return(num1+num2)
	print('I will never trigger since return before me will stop the function')
```

–– we normally return just one item unless we are using tuple to return several items at once:

```python
def sum(num1,num2):
	print(num1+num2)
    return( (num1+num2,'banana') )
 
sum(1,2)
# 3
# (3, 'banana')
```

–– return pops the function off the call stack where it's added once called. We will explore that later. 

---

Now let's create a function which is using everything from what we've seen in this block so far. We will have a function to randomly pick one of the names from the list of names:

```python
# first we import the random module to generate a random number
import random

# then we have a list of names
players = ['mia','bob','jake']

# defining a function which takes one argument -- it will be list of our names
def chosen(names):
# make a random index within the range of 0 to length of the list minus one
	idx = random.randint(0, len(names)-1)
# print out the message
	print(f'{names[idx]}, you are chosen!' )
# return the chosen name
	return(names[idx])

# execute the function
chosen(players) 
```

## Common mistakes:

–– returning too soon before executing the code you need to execute, in this case return is the last statement in the function

–– returning inside the loop: if you need to loop through something and then return, make sure your return is AFTER the loop ends

---

Of course we can do all the logic we did so far inside the functions, like looping:

```python
def check_list (some_list):
	for item in some_list:
		print(type(item) )

random_list = [12,4,5,True,'orange']

check_list(random_list)
# <class 'int'>
# <class 'int'>
# <class 'int'>
# <class 'bool'>
# <class 'str'>
```

Now our function can check the type of each element of whichever list we pass as an argument!

---

## Functions inside functions!

We have seen that we can have conditionals and loops inside our functions, but can we also have a function call inside a function???

Well actually we already did!

Every time we use `print()` inside a function we are calling this built-in function! 

But we may also call a custom function from inside our function.

```python
def sayHi(word):
	print(word)

def fun():
	sayHi('Hello')

fun()
# Hello


def fun():
	return 1

def fun2():
	x = fun()
	print(x)

fun2()
# 1
```

> It's important if we want to use the output from `fun()` in `fun2()` then `fun()` should `return` it.

```python
def mySonExpenses(games, sodas):
	return games + sodas

def myExpenses(rent, grocery):
	return rent + grocery

def getTotal():
	mySonExp = mySonExpenses(100, 30)
	myExp    = myExpenses(1200, 230)
	return mySonExp + myExp

getTotal()
# 1560
```
Now we can improve these functions and make them shorter by not assigning the return value to variables (by the way, this process of improving your code is called refactoring):

```python
def mySonExpenses(games, sodas):
	return games + sodas

def myExpenses(rent, grocery):
	return rent + grocery

def getTotal(games, sodas, rent, grocery):
	return mySonExpenses(games, sodas) +  myExpenses(rent, grocery)

getTotal(100, 30, 1200, 230)
# 1560
```

## Scope

In Python we have two types scopes – global and local. Any variable declared outside of a function belongs to the global scope, and is therefore accessible from anywhere in your code. 

Each function has its own scope, and any variable declared within that function is only accessible from that function and any nested functions. 

```python
age = 19
name ="Jason"

def tell():
	secret = "super mega secret"
	print(f'Mr.{name} is {age} years old and the secret is {secret}')


print(secret)
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# NameError: name 'secret' is not defined
tell()
# Mr.Jason is 19 years old and the secret is super mega secret
```

It's always from the inside to the outside, from function we have access to variables inside it's own scope and in a global scope, if we have an inner function it has access to it's own scope, parent function's scope and global scope, but the parent function doesnt have access to the inner function's scope:

```python
age = 19
name ="Jason"

def tell():
	secret = "super mega secret"
	print(f'Mr.{name} is {age} years old and the secret is {secret}')
	print(f'Trying to get the inner secret {inner_secret} but instead got an error')
	def inner_func():
		inner_secret = 'nobody will know'
		print(f'I know your secret, it is {secret}, but you can not get mine')
	inner_func()

tell()
# Mr.Jason is 19 years old and the secret is super mega secret
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
#   File "<stdin>", line 4, in tell
# NameError: name 'inner_secret' is not defined
```

Removing reference to inner_secret from our `tell()` function will eliminate an error:
```python
age = 19
name ="Jason"

def tell():
	secret = "super mega secret"
	print(f'Mr.{name} is {age} years old and the secret is {secret}')
	# print(f'Trying to get the inner secret {inner_secret} but instead got an error')
	def inner_func():
		inner_secret = 'nobody will know'
		print(f'I know your secret, it is {secret}, but you can not get mine')
	inner_func()

tell()
# Mr.Jason is 19 years old and the secret is super mega secret
# I know your secret, it is super mega secret, but you can not get mine
```

If we are trying to manipulate a global variable inside a function's local scope (not just print, but change it) we need to refer to it with keyword `global` before:

```python
age = 19
name ="Jason"

def grow_older():
	age += 1
	print(f'{name} is {age} now, time flies!')

grow_older()
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
#   File "<stdin>", line 2, in grow_older
# UnboundLocalError: local variable 'age' referenced before assignment
```

So the fix is:

```python
age = 19
name ="Jason"

def grow_older():
	global age
	age += 1
	print(f'{name} is {age} now, time flies!')

grow_older()
# Jason is 20 now, time flies!
grow_older()
# Jason is 21 now, time flies!
grow_older()
# Jason is 22 now, time flies!
```

The logic is the same for modifying variables inside the parent's function from the child function:

```python
def parent():
	count = 0
	def child():
		nonlocal count
		count+=1
		return count
	return child()

parent()
# 1
```

## Comments 

If we put comments into our functions we can easily get them to see with `.__doc__` method:
```python
def my_func():
	""" This function is sending starships to space """
	return('Starship is send')

# and now we can see the comments describing this function with
my_func.__doc__
# 'This function is sending starships to space'
```

> And it works for the built-in functions as well, try running `print.__doc__`

## * and ** operators

Star operator -- `*` -- is a special type of operator we can pass into a function, if done so it gathers remaining arguments as a tuple. 

Conventionally we use it as `*args` but it can be any word, 'args' is just a convention.

Let's see a simple example. Let's say we want to have a function which takes several arguments and returns their sum, but we do not want to define initially how many arguments we will pass, it could be two numbers or 50 numbers or 10 numbers, etc. 

So with `*args` we can do it easily:

```python
def sum_all(*args):
	print(args)
	# we will see tht args here becomes a tuple of all the numbers passed as arguments
	# now we can iterate through it normally and get the sum:
	total = 0
	for num in args:
		total+=num
	return total

sum_all(1,2,3,4)
# (1, 2, 3, 4)
# 10
sum_all(5,6,7,8,9,1)
# (5, 6, 7, 8, 9, 1)
# 36
```

For sure we can pass individual arguments combined with `*args`:
```python
def sum_all(message, *args):
	total = 0
	for num in args:
		total+=num
	return f'{message} {total}'

sum_all('Here are your results',1,2,3,4)
# 'Here are your results 10'
```

Another special operator would be `**` which conventionally followd by `kwargs` word: `**kwargs`. 

This one gathers remaining arguments into a dictionary, not a tuple as `*`:

```python
def pets_names(**kwargs):
	for pet in kwargs:
		print(f'Pet: {pet}, name: {kwargs[pet]}')

pets_names(cat='cookie', dog='mudface', goldfish='fish fillet')
# Pet: cat, name: cookie
# Pet: dog, name: mudface
# Pet: goldfish, name: fish fillet
```

Now with this in mind we need to mention the order of parameters while defining a function in case we are using all of them should be the following:

* Normal parameters
* `*args`
* Default parameters
* `**kwargs`

Even if you do not use *all* of them in the same function still the order of those, which are being used, should follow this pattern. 

## Upacking 

If we will pass a start `*` as an argument into a function it will unpack the values from the arguments, in other languages it is called destructuring but the principle is the same -- we can extract individual values from iterable data item like a list, or tuple or set or dictionary. If we will pass a list with numbers into this function it will complain:

```python
def sum_all(*args):
	print(args)
	# we will see tht args here becomes a tuple of all the numbers passed as arguments
	# now we can iterate through it normally and get the sum:
	total = 0
	for num in args:
		total+=num
	return total

sum_all([1,2,3,4])
# number expected
```

So we can unpack this list (or it can also be a tuple) by adding `*` before it in a function call:
```python
def sum_all(*args):
	print(args)
	# we will see tht args here becomes a tuple of all the numbers passed as arguments
	# now we can iterate through it normally and get the sum:
	total = 0
	for num in args:
		total+=num
	return total

sum_all(*[1,2,3,4])
# 10
```

To unpack a dictionary we use two stars `**`:

```python
```python
def pets_names(**kwargs):
	for pet in kwargs:
		print(f'Pet: {pet}, name: {kwargs[pet]}')

my_pets = {'cat':'cookie', 'dog':'mudface', 'goldfish':'fish fillet'}
pets_names(my_pets) # throws error
pets_names(**my_pets) # works
# Pet: cat, name: cookie
# Pet: dog, name: mudface
# Pet: goldfish, name: fish fillet
```

Or, let's say we have a function expecting 2 arguments and instead we pass a dictionary with these 2 arguments inside, with unpacking it's still going to work:

```python
def greeting(first_name, last_name):
	print(f'Hello {first_name} {last_name}')

guest1 = {'first_name':'Kylo', 'last_name':'Ren'}
greeting(guest1) # throws error
greeting(**guest1) # works
# Hello Kylo Ren
```

> Key names in the object should match the names of variables or parameters like here we are extracting them into. 


