# Tuples and sets

---

<details>
    <summary>Tuples and sets</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/uPP5l-lppXY?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

Tuple is an orderd immutable sequence of records inside parenthesis like `('luke', 100, 'force', 5.5)`. So the main difference between tuples and lists is that tuple is immutable, it can not be changed. Once defined, we can't update or delete an item in the tuple. 

Why do we want to use them? Same as constants in other programming languages we might want to define a list of value which should not be modified. Like an alphabet for example, we can't change it to our liking, right? Or a list of months in the year... 

```python
>>> alphabet = ('a','b','c')
>>> alphabet[0]
'a'
>>> alphabet[0] = 'z'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

Mainly the reasons to use tuples are:
* they are faster than the lists, since once defined Python doesn't need to check them everytime they are invoked, it knows that it is the same tuple as when it was defined
* safer for code since it can't be modified intentionally or unintentionally which leads to more predictability
* tuple could be a valid key in a dictionaly
* some methods return them, like .items() for the dictionaries

To create a tuple we use `()` or `tuple` function:

```python
alphabet = ('a','b','c')
# or
alphabet = tuple(['a','b','c'])
```

Accessing tuples is absolutely same as a list:

```python
alphabet[1]
# b
```

---

Iterating through the tuples is exactly the same as through the lists:
```python
alphabet = ('a','b','c')
for item in alphabet:
	print(item)
# a
# b 
# c 
```

Using tuples in dictionaries sometimes could be also very handy when the key is composed out of more than one item:
```python
heroes = [
{('John','Snow'):'GoT'},
{('Kylo','Ren'):'Star Wars'}
]
```

With these keys we can not only access the value directly like `heroes[0][('John','Snow')]` but also since tuples are nothing but the list we can also iterate through those keys! Here is how:

```python
heroes = [
{('John','Snow'):'GoT'},
{('Kylo','Ren'):'Star Wars'}
]

for item in heroes:
	for key in item:
		for kp in key:
			print(kp)
# John
# Snow
# Kylo
# Ren
```

---

## Tuple methods

### count

This one returns the number of times an item appears in tuple:

```python
nums = (1,2,3,4,4,5,4)
nums.count(4)
# 3
```

---

### index

Same as with the lists it returns the the index of the item in the tuple, if there are several same items it will give the index of the first one, if hte item is not htere it will throw an error:
```python
nums = (1,2,3,4,4,5,4)
nums.index(4)
# 3
nums.index(6)
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# ValueError: tuple.index(x): x not in tuple
```

> We can have nested tuples and they behave exactly the same as nested lists. 

---

# Sets

This one is unordered collection of **unique** records inside the curly brackets like {'a','b','c'} -- can't have {'a','a'}, Python will reduce it to {'a'}

You can't access items in the set by index because there is no index, these lists are **unordered**. 

Declaring sets involves using curly brackets or `set()` function:

```python
alphabet = {'a','b','c'}
# or
alphabet = set(['a','b','c'])
```

No indexes here but we can check if something is inside a set:

```python
alphabet = {'a','b','c'}
"a" in alphabet
# True
```

Of course we can iterate via set with a loop:
```python
alphabet = {'a','b','c'}
for item in alphabet:
	print(item)
# c
# a
# b
```

Notice the order of letters printed is absolutely unpredictable 🤷‍♀️. 

Usecase for sets is if we have a list of items and we want it to be unique we can simply convert it to set:
```python
possible_names_for_my_new_pet = ['Kylo','Cookie','Fur','Kylo','Cookie']
unique_options = set(possible_names_for_my_new_pet)
print(unique_options)
# {'Fur', 'Cookie', 'Kylo'}

# and convert it back to a list
possible_names_for_my_new_pet = list(unique_options)
print(possible_names_for_my_new_pet)
# ['Fur', 'Cookie', 'Kylo']
```

---

## Sets methods

### add

This one adds an element to a set, if the same element is already in there it does nothing:

```python
possible_names_for_my_new_pet = {'Fur', 'Cookie', 'Kylo'}
possible_names_for_my_new_pet.add('Pet')
print(possible_names_for_my_new_pet)
# {'Fur', 'Cookie', 'Kylo', 'Pet'}
#  'Pet' is added to the set

possible_names_for_my_new_pet.add('Kylo')
print(possible_names_for_my_new_pet)
# {'Fur', 'Cookie', 'Kylo', 'Pet'}
# 'Kylo is not added to the set since it's already there
```

---

### remove

As the name suggest this method allows us to remove an item from a set:
```python
possible_names_for_my_new_pet = {'Fur', 'Cookie', 'Kylo'}
possible_names_for_my_new_pet.remove('Kylo')
print(possible_names_for_my_new_pet)
# {'Fur', 'Cookie'} -- goodbye Kylo

# trying to remove something that is not there will throw an error:
possible_names_for_my_new_pet.remove('Pet')
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# KeyError: 'Pet'
```

> To avoid getting errors while removing non-existent item we can use `.discard()` method

---

### copy

This method creates a copy of a set:

```python
possible_names_for_my_new_pet = {'Fur', 'Cookie', 'Kylo'}
possible_child_names = possible_names_for_my_new_pet.copy()
print(possible_child_names)
possible_child_names == possible_names_for_my_new_pet
# True
possible_names_for_my_new_pet is possible_child_names
# False
```

### clear 

Method with this name can only do one thing -- clear set entirely:

```python
possible_names_for_my_new_pet = {'Fur', 'Cookie', 'Kylo'}
possible_names_for_my_new_pet.clear()
print(possible_names_for_my_new_pet)
# set()
```

## Set math

With set math we can do different merging of sets based on the selected logic.

### Set union

We can combine to sets to have only unique items from both. For example, let's say we (me and you) are adopting a kitty and both have their lists of possible names, now you want to merge them together but stil have them unique, so:
```python
my_ideas = {'Fur', 'Cookie', 'Kylo','Shadow'}
your_ideas = {'Cookie', 'Bro', 'Arya','Tooth'}
combined_ideas = my_ideas | your_ideas
print(combined_ideas)
# {'Tooth', 'Cookie', 'Fur', 'Arya', 'Bro', 'Kylo', 'Shadow'}
# as you can see Cookie was only added once
```

Now we do the same but we want to only keep the names which are the same in our lists so we will have a shortlis:
```python
my_ideas = {'Fur', 'Cookie', 'Kylo','Shadow'}
your_ideas = {'Cookie', 'Bro', 'Arya','Tooth'}
combined_ideas = my_ideas & your_ideas
print(combined_ideas)
# {'Cookie'}
# as you can see Cookie was in both lists so that's the name of our new pet!!!
```

<img src="./pics/cookie_cat.jpg">


## Set comprehension

Similar to lists we can do set comprehensions on set:
```python
nums = {1,4,8,12}
{num*2 for num in nums}
# {16, 8, 2, 24}
```

And in the same way as with lists we can modify set:
```python
nums = {1,4,8,12}
nums = {num*2 for num in nums}
print(nums)
# {16, 8, 2, 24}
```

Or look how we can quickly find all the unique even numbers in a list of numbers, for example:
```python
nums = [1,2,3,4,5,6,7,8,1,2,3,4,5,6,7,8,1,2,3,4,5,6,7,8]
unique_even_numbers = {num for num in nums if num%2==0} # <-- here we only take even numbers AND put them into a set to make unique only
print(unique_even_numbers)
# {8, 2, 4, 6}
```





