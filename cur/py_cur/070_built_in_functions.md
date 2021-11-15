# Lambdas

---

<details>
    <summary>Built-in functions</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/X2wmtQuLRRc?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

Let's say we have a function which return a sum of two numbers:

```python
def sum(a, b):
	return(a + b);

sum(10, 5)
# 15
```

We can have the same results with lambda which is essentially an anonymous function without a name:

```python
lambda a,b: a + b
```

So in this case we start with a keyword `lambda` then follow with parameters divided by coma and after semicolon we can have just one expression which would be implicitely returned. 

The syntax for lambda is:
```python
lambda argument(s) : expression
```

We can assign lambda to a variable and execute it although it's not how we normally would use lambda:

```python
sum = lambda a,b : a + b
sum(2,3)
# 5
```

The most common use of lambdas is when we want to pass a function as an argument into another function and the function itself is never needed to be called by name, so lambda is the best way to go. 

# map()

This function is taking two arguments -- a function (which would be lambda) and an iterable item like a list, string, dictionary, etc... Then `map()` will run this function for every item of iterable item and return a new map object which could be converted to something else if you need to. 

For example, we want a function which will multiply every number in a list by 5:

```python
numbers = [1,2,3,4,5]
fiver = map( lambda item:item*5, numbers )
fiver
# <map object at 0x100dc8f90>
list(fiver)
# [5, 10, 15, 20, 25]
```

Another example of `map` -- we have a list of objects for every pet and we want to get their names only: 
```python
my_pets = [
{'type':'cat', 'name':'cookie'},
{'type':'dog', 'name':'mudface'},
{'type':'goldfish', 'name':'fish fillet'}
]
names_only = list( map(lambda pet:pet['name'], my_pets) )

names_only
# ['cookie', 'mudface', 'fish fillet']
```


# filter()

`filter()` is used in the same way as `map()` but what it does is going through the iterable item and returns a filter object with values passing through a condition in the filter:

```python
filter(lambda element: expression evaluating to true or false, iterable object)
```

For example, let's find all the values from the list which are even numbers:
```python
numbers = [1,2,3,4,5]
even_nums = filter( lambda item:item%2==0, numbers )
even_nums
# <filter object at 0x100dd1150>
list(even_nums)
# [2, 4]
```

Another example -- we have list of orders and we want to filter out only those, which are not delivered yet:
```python
orders = [
{'order_num': 123, 'order_status':'delivered','order_content':['black tshirt','black hat','black shoes']},
{'order_num': 321, 'order_status':'recieved','order_content':['black tshirt','black hat','black shoes']},
{'order_num': 456, 'order_status':'processing','order_content':['black tshirt','black hat','black shoes']},
{'order_num': 654, 'order_status':'cancelled','order_content':['black tshirt','black hat','black shoes']},
{'order_num': 123, 'order_status':'delivered','order_content':['black tshirt','black hat','black shoes']}
]

not_delivered = list( filter(lambda order: order['order_status'] != 'delivered', orders) )
print(not_delivered)
# [{'order_num': 321, 'order_status': 'recieved', 'order_content': ['black tshirt', 'black hat', 'black shoes']}, {'order_num': 456, 'order_status': 'processing', 'order_content': ['black tshirt', 'black hat', 'black shoes']}, {'order_num': 654, 'order_status': 'cancelled', 'order_content': ['black tshirt', 'black hat', 'black shoes']}]
```


Of course we can combine `map()` with `filter()`. Lets display a message 'Your pet is PET_NAME' but only if list of pets contain a cat(s):

```python
my_pets = [
{'type':'cat', 'name':'cookie'},
{'type':'dog', 'name':'mudface'},
{'type':'goldfish', 'name':'fish fillet'},
{'type':'cat', 'name':'hairy'}
]
cats_only = list( map(lambda pet:f'Your pet is {pet["name"]}', 
	filter( lambda cat:cat["type"]=='cat', my_pets ) # this line first gives object of only cats
))

cats_only
# ['Your pet is cookie', 'Your pet is hairy']
```

> What about list comprehensions? 

For sure we can do the similar things with lists comprehensions, which are far more easier to write and are preferred way for most of the developers but it's important to know that lambdas do exist and being able to use them if/when needed:

```python
[f"Your pet is {petname['name']}" for petname in my_pets if petname['type']=='cat' ] 
# ['Your pet is cookie', 'Your pet is hairy']
```

# all()

This built-in function takes an *iterable* item and returns True if **all** of the elements are truthy or the iterable is empty. 

Example:
```python
all([1,2,3,4]) 
# True
all([0,1,2,3,4]) 
# False since 0 is falsy, remember?
my_pets = [
{'type':'cat', 'name':'cookie'},
{'type':'dog', 'name':'mudface'},
{'type':'goldfish', 'name':'fish fillet'},
{'type':'cat', 'name':'hairy'}
]
all(my_pets)
# True
all([])
# True
```

We can put Python expressions as an argument for `all()` and then it will evaluate the results. Let's say we want to check if age of all the pets is bigger than 2:

```python
my_pets = [
{'type':'cat', 'name':'cookie', 'age': 3},
{'type':'dog', 'name':'mudface', 'age': 5},
{'type':'goldfish', 'name':'fish fillet', 'age': 7},
{'type':'cat', 'name':'hairy', 'age': 9}
]
all([pet['age'] > 2 for pet in my_pets])
True
```


# any()

This built-in function takes an *iterable* item and returns True if **any** of the elements is/are truthy, returns False for the empty iterable. 

Example:
```python
any([1,2,3,4]) 
# True
any([0,1,0,0,0]) 
# True
my_pets = [
{'type':'cat', 'name':'cookie'},
{'type':'dog', 'name':'mudface'},
{'type':'goldfish', 'name':'fish fillet'},
{'type':'cat', 'name':'hairy'}
]
any(my_pets)
# True
any([])
# False
```

Is there any pet older than 5? 

```python
my_pets = [
{'type':'cat', 'name':'cookie', 'age': 3},
{'type':'dog', 'name':'mudface', 'age': 5},
{'type':'goldfish', 'name':'fish fillet', 'age': 7},
{'type':'cat', 'name':'hairy', 'age': 9}
]
any([pet['age'] > 5 for pet in my_pets])
# True
```

> Do we need a new list? 

In case we pass a list comprehension into some function, like in `any([pet['age'] > 5 for pet in my_pets])` we can omit the square brackets since we do not want to generate a new list, we only want to temporary use it inside our `any()` function, so to make it more lightweight and save space in memory we can do it like this: `any(pet['age'] > 5 for pet in my_pets)`. This syntax is called generator expressions, we will see it later in more details. 

# sorted()

Takes an iterable, including lists and anything else (but not limited to lists as `.sort()`) and returns a **new** sorted *list* from the items of iterable:

```python
nums = [10,2,16,8]
sorted(nums)
# [2, 8, 10, 16] 
nums
# [10, 2, 16, 8] nums is not modified
sorted_nums = sorted(nums) # make a new variable to keep the sorted results
sorted_nums
# [2, 8, 10, 16] and now we have a new copy of nums but sorted! 
```

> Another difference from `.sort()` is that `sorted()` DOES NOT modify the initial data.

Now let's sort a more complec data structure, let's say we want to sort this list of pets by age of pet in ascending order:

```python
my_pets = [
{'type':'cat', 'name':'cookie', 'age': 9},
{'type':'dog', 'name':'mudface', 'age': 5},
{'type':'goldfish', 'name':'fish fillet', 'age': 7},
{'type':'cat', 'name':'hairy', 'age': 3}
]
sorted_pets = sorted(my_pets,key=lambda pet: pet['age'])
sorted_pets 
# [{'type': 'cat', 'name': 'hairy', 'age': 3}, {'type': 'dog', 'name': 'mudface', 'age': 5}, {'type': 'goldfish', 'name': 'fish fillet', 'age': 7}, {'type': 'cat', 'name': 'cookie', 'age': 9}]
```

As you can see we are using our old friend lambda here to tell that the key of sorting would be 'age' inside every dictionary of this list. 

And to change the order of sorting we add `reverse=True` parameter into the `sorted()` function:


```python
my_pets = [
{'type':'cat', 'name':'cookie', 'age': 9},
{'type':'dog', 'name':'mudface', 'age': 5},
{'type':'goldfish', 'name':'fish fillet', 'age': 7},
{'type':'cat', 'name':'hairy', 'age': 3}
]
sorted_pets = sorted(my_pets,key=lambda pet: pet['age'], reverse=True)
sorted_pets 
# [{'type': 'cat', 'name': 'cookie', 'age': 9}, {'type': 'goldfish', 'name': 'fish fillet', 'age': 7}, {'type': 'dog', 'name': 'mudface', 'age': 5}, {'type': 'cat', 'name': 'hairy', 'age': 3}]
```

# max()

This one returns the biggest item from an iterable passed into it or the biggest one out of the two or more arguments passed into it:

Iterable:

```python
nums = [1,2,3,4,5,66,55,44,33]
max(nums)
# 66
```

Several separate arguments:
```python
max(5,1,9)
# 9
foo = 10
bar = 5
zoo = 6
max(foo,bar,zoo)
# 10
max('banana','kiwi','orange')
# 'orange' <<-- the 'biggest' in alphabetical sense
```

We can do more useful things with `max()` as well, like finding the length of the longest word in a list:
```python
max(len(fruit) for fruit in ['banana','kiwi','watermelon', 'orange'])
# 10 <<-- the length of the longest word in this list
```

What if we want to get the actual value with the biggest length? Here comes lambda again:
```python
fruits = ['banana','kiwi','watermelon', 'orange']
max(fruits, key=lambda fruit : len(fruit))
# 'watermelon' <<-- the item with the biggest length in this list
```


# min()

`min()` works exactly as `max()` but is looking for the smallest value possible. Let's find the youngest pet in this list:

```python
my_pets = [
{'type':'cat', 'name':'cookie', 'age': 9},
{'type':'dog', 'name':'mudface', 'age': 5},
{'type':'goldfish', 'name':'fish fillet', 'age': 7},
{'type':'cat', 'name':'hairy', 'age': 3}
]
min(my_pets, key=lambda pet : pet['age'])
# {'type': 'cat', 'name': 'hairy', 'age': 3}
# To get the name of this pet:
(min(my_pets, key=lambda pet : pet['age']))['name']
# 'hairy'
```


# reversed()

Similar to the list method `.reverse()`, built-in function `reversed()`  takes an iterable collection and returns reversed object, it works on strings, lists, etc.
```python
bar = reversed('banana')
bar 
# <reversed object at 0x10f219d50>
```

We can loop on this reversed object:
```python
for char in reversed('banana'):
     print(char)
 
# a
# n
# a
# n
# a
# b
```

Or join it back to string:
```python
bar = ''.join( list(reversed('banana')) )
bar 
# 'ananab'
```

> Remember that for strings it's easier to use slice: `'banana'[::-1]` !

# abs()

This function gives back the absolute value of a number, the absolute number is a real number disregarding the sign:

```python
abs(5)
# 5
abs(-5)
# 5
```



