# Lists

---

<details>
    <summary>Lists</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/oO2sJXIDBL8?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

In Python list is a special type of variable, which can hold more than one value at a time. List is basically a list of items separated by a comma.

If you have a list of items (a list of names, for example), storing the names in separate variables could look like this:

```python
name1 = "Luke"
name2 = "Han"
name3 = "Kylo"
```

Declaring these names in the list, as a list of names, is simple as that:

```python
names = ["Luke","Han","Kylo"]
```

The values inside a list could be of different data types: `[1, 'Luke', True]`

Lists have several properties, the most commonly used are **length** and **index**.

In Python we can quickly create a list of numbers with `range`, such as 
```python
numbs = list(range(0,11))
numbs
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

---

## Length

The **len** property tells us how many elements are inside the list, for example:

```python
words = [ "zero", "one","two" ]
len(words) #3
```

---

## Index

The **index** is the position of an element inside the list, starting from zero.


```python
fruits = ["banana", "orange", "strawberry"]

print(fruits[0]) # banana
print(fruits[1]) # orange
print(fruits[2])  # strawberry
```

You can use the index property of the list to replace elements in the list

```python
fruits = ["banana", "orange", "strawberry"]
fruits[0]= "apple"
# our previously empty list has now one element inside it at the index of 0.
# now try:
print(fruits)
```

---

## List methods

Lists have various built-in methods which are handy to manipulate them and do some common operations we do on a daily basis. 

Methods applied after the name of a given list with a `.` before:

---

### .append()

In order to add new elements to the list without worrying about the index we can use the built-in method `list.append()`.

The `append()` method adds new items to the end of an list:

```python
fruits = [];
fruits.append('apple')
```

`.append()` method takes exactly one argument so at a single time we can add just one item to the list, this item can be of any data type. 

```python
fruits = ['orange'];
fruits.append(10)
```

---

### .extend()

If we want to add several items at once then we can use `.extend()` method:

```python
fruits = ['orange'];
fruits.extend(['kiwi', 'banana'])
```

---

### .insert()

With `.insert()` method we can add an item into the list at some specific index. 

```python
fruits = ["banana", "orange", "strawberry"]
fruits.insert(1,'kiwi')
fruits
# ['banana', 'kiwi', 'orange', 'strawberry']
```

So the first argument in `insert()` method would be the desired index and the secon one is the item itself. 

With negative indexes it will calculate the position before changing the list so -1 will always put th item next to the last one:

```python
fruits = ["banana", "orange", "strawberry"]
fruits.insert(-1,'kiwi')
fruits
# ['banana', 'orange', 'kiwi', 'strawberry']
```

---

### .clear()

To remove items from the list we can use method `clear()` which will remove everything from the list:

```python
fruits = ["banana", "orange", "strawberry"]
fruits.clear()
fruits
# []
```

In case we want to remove a single item from the list we can use `.pop()`

---

### .pop()

With `.pop()` we can specify an index for the item to be removed and it will be deleted from the list and returned back:

```python
fruits = ["banana", "orange", "strawberry"]
removed_one = fruits.pop(1)
fruits
# ['banana', 'strawberry']
removed_one
# 'orange'
```

Without any arguments `.pop()` will delete the last item in the list:
```python
fruits = ["banana", "orange", "strawberry"]
fruits.pop()
fruits
# ['banana', 'orange']
```

---

### .remove()

With this method we can delete an item from the list by value, not index. It will find the first instance of provided value and delete it:

```python
fruits = ["banana", "orange", "strawberry", "banana"]
fruits.remove("banana")
fruits
# ['orange', 'strawberry', 'banana']
```
If item is not in the list it will throw an error:


```python
fruits = ["banana", "orange", "strawberry", "banana"]
fruits.remove("kiwi")
# ValueError: list.remove(x): x not in list
```

Of course we can use variables with all these methodes:
```python
fruits = ["banana", "orange", "strawberry", "banana"]
to_remove = "banana"
fruits.remove(to_remove)
fruits
# ['orange', 'strawberry', 'banana']
```

and for indexes as well:

```python
fruits = ["banana", "orange", "strawberry", "banana"]
to_remove = 1
fruits.pop(to_remove)
fruits
# ['banana', 'strawberry', 'banana']
```

---

### .index()

If we know the value of the item but do not know it's index we can find it with `.index()` method which returns the index of found item or error if item is not in the list:

```python
fruits = ["banana", "orange", "strawberry", "banana"]
fruit_x = 'orange'
fruits.index(fruit_x)
# 1
```

```python
fruits = ["banana", "orange", "strawberry", "banana"]
fruit_x = 'kiwi'
fruits.index(fruit_x)
# ValueError: 'kiwi' is not in list
```

We can also specify starting index and ending index to look for the item in question between them:

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana"]
fruit_x = 'orange'
fruits.index(fruit_x, 1) #search only after index 1
# 2
```

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana", "orange"]
fruit_x = 'orange'
fruits.index(fruit_x, 1, 4) #search only between indexes 1 and 4
# 2
```

By using indexes we can also swap items in the list for maybe shuffling or sorting them:

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana", "orange"]
fruits[0], fruits[1] = fruits[1], fruits[0]
fruits
# ['banana', 'orange', 'orange', 'strawberry', 'banana', 'orange']
```

---

### .count()

This method returns the number of times a given item appears in the list or in other words number of instances of a given value:

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana", "orange"]
fruit_x = 'orange'
fruits.count(fruit_x) 
# 3
```

---

### .reverse()

This method reveres the list backwards:

```python
nums = [1,2,3,4,5,6]
nums.reverse() 
nums
# [6, 5, 4, 3, 2, 1]
```


---

### .sort()

We can sort our lists with `.sort()` method:

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana", "orange"]
fruits.sort() 
# ['banana', 'banana', 'orange', 'orange', 'orange', 'strawberry']
```

By default it is sorting in alphabetical/ascending order. To change the sorting order to descending	 we can add `reverse` parameter with value `True`:

```python
fruits = ["orange", "banana", "orange", "strawberry", "banana", "orange"]
fruits.sort(reverse=True) 
fruits
# ['strawberry', 'orange', 'orange', 'orange', 'banana', 'banana']
```

One more method for this block is `.join()`

---

### .join()

`.join()` is actually a string method but we can use it on lists to join all the items from the list into a string:

```python
fruits = ["banana", "orange", "strawberry"]
results = ' '.join(fruits)
```

In this case all the items from the list would be combined into a string with a space between them.

We cna use anything instead of a space to add between list items while joining into a string:

```python
fruits = ["banana", "orange", "strawberry"]
results = ' and '.join(fruits)
results
# 'banana and orange and strawberry'
```

---

## slicing

With slicing we can remove items from the list with starting and ending positions and optional step as the third argument. In a sense the logic here is very similar to `range`. The first argument is the starting index included into the slicing, the second argument is the index untill which we are slicing, it is excluded from the slicing itself.

The syntax for slicing would be `name_of_list[start:end:step]`:

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple"]
results = fruits[1:3]
results
# ['orange', 'strawberry']
fruits
# ['banana', 'orange', 'strawberry', 'kiwi', 'apple']
```

As you can see slicing is not modifying the original list but returns the removed items. 

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
results = fruits[1:6:2]
results
# ['orange', 'kiwi', 'pineapple']
fruits
# ['banana', 'orange', 'strawberry', 'kiwi', 'apple', 'pineapple', 'mango', 'pear']
```

You can see that here with step 2 we go from orange to kiwi skipping strawberry and to pineapple skipping apple. 

If we want to slice and modify the list itself then we have to reassign sliced out elements to be the value of the current list:

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
fruits = fruits[1:6:2]
fruits 
# ['orange', 'kiwi', 'pineapple']
```

With only one argument Python will slice everything starting with provided start position:

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
sliced_out = fruits[2:]
sliced_out 
# ['strawberry', 'kiwi', 'apple', 'pineapple', 'mango', 'pear']
```

With only start index and a step providede we will slice everything starting with the starting position untill the end of list with a given step:

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
sliced_out = fruits[2::2]
sliced_out 
# ['strawberry', 'apple', 'mango']
```

We can also modify portions of a list with slices:

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
fruits[2:4] = ['pizza','pasta','vino']
fruits
# ['banana', 'orange', 'pizza', 'pasta', 'vino', 'apple', 'pineapple', 'mango', 'pear']
```

To **actually** remove items from the list with slicing we can do this:

```python
names = ['Luke', 'Leia', 'Kylo', 'Han', 'Grogo', 'Darth', 'Chewbacca', 'Boba Fett']
names[1:4]=[] #replacing items with indexes from 1 to 4 with empty values is deleting them
names 
#['Luke', 'Grogo', 'Darth', 'Chewbacca', 'Boba Fett']
```


---

## Lists comprehensions

A list comprehension is a syntactic construct used for creating a list based on existing lists. Let's say we have a list of numbers and we want to have a new list based on that with all the numbers multyplied by 2:

```python
nums = [1,2,3]
double_nums = [num*2 for num in nums]
double_nums
# [2, 4, 6]
```

or

```python
fruits = ["banana", "orange", "strawberry", "kiwi", "apple", "pineapple", "mango", "pear"]
to_be_healthy = ['eat '+fruit for fruit in fruits]
to_be_healthy
# ['eat banana', 'eat orange', 'eat strawberry', 'eat kiwi', 'eat apple', 'eat pineapple', 'eat mango', 'eat pear']
```

Checking for falsy/truthy values in a list with comprehensions is also possible:

```python
assortments = ["banana", [], 0, 10]
booleans = [bool(item) for item in assortments]
booleans
# [True, False, False, True]
```

---

## Conditional logic in list comprehensions

There is a way to add a condition into LC and only do specified action if condition is met. For example, we want to take only even numbers form the list:

```python
nums = [1,2,3,4,5,6]
even_nums = [num for num in nums if num % 2 == 0]
even_nums
# [2, 4, 6]
```

Now we want to take only even numbers and multiply them by 10:
```python
nums = [1,2,3,4,5,6]
even_nums = [num*10 for num in nums if num % 2 == 0]
even_nums
# [20, 40, 60]
```

To modify the original list itself we reassign results of LC to the given list:
```python
nums = [1,2,3,4,5,6]
nums = [num*10 for num in nums if num % 2 == 0]
nums
# [20, 40, 60]
```

---

### if/else in the LC

So let's do the same as in a previous example but now for odd numbers we will miltyply them by 2:

```python
nums = [1,2,3,4,5,6]
nums = [num*10 if num % 2 == 0 else num*2 for num in nums]
nums
# [2, 20, 6, 40, 10, 60]
```

If we want to keep some items as they are and only modify others with a condition, like keep odd numbers unchanged but multiply even numbers by 10 we do it as following:

```python
nums = [1,2,3,4,5,6]
nums = [num*10 if num % 2 == 0 else num for num in nums]
nums
# [[1, 20, 3, 40, 5, 60]
```

---

## Nested lists

With more complex data we can have lists there some (or all) items are lists themselves, like:

`nums = [[1,2,3],['a','b','c'],[True, False,True]]`

The syntax to get item from the nested list is that first we use index for the top level item/list and then we add an index for the item inside the nested list. For example, to get 2 from this list we go with `nums[0][1]`, to get `'b'` we use `nums[1][1]`

---

## Nested lists comprehensions

We can use LC to do the same as with loops:

```python
nums = [[1,2,3],['a','b','c'],[True, False,True]]
[ [print(item) for item in ls] for ls in nums ]
# 1
# 2
# 3
# a
# b
# c
# True
# False
# True
```

Another example to create a list of nested lists with numbers and print odd or even from the LC:

```python
nums = [ [num for num in range(0,5)] for ele in range(1,4) ]
[ [print(f'{num} is even') if num % 2 == 0 else print(f'{num} is odd') for num in item] for item in nums  ]
```

<img src="./py_cur/pics/mitch.gif">








<!-- 
There are several methods used to remove items from an list, one of the most useful is **list.splice()**.

list.splice takes up to 2 arguments, the first is the **index that you want to start removing from** and the second is **how many elements you want to remove.**

So for instance in the below example we want to stat from index 1 (element “two”) and we want to remove 2 elements:

```python
list = ["one", "two", "three", "car", "banana"];
list.splice(1,2)
print(list)
//["one", "car", "banana"]
```

If you want to remove all elements in the list, you can start from the zero index (which is the first element) and pass `list.length` as the second argument like so:

```python
list = ["one", "two", "three", "car", "banana"];
list.splice(0, list.length)
print(list)
//[]
```

Another way to achieve the same result is starting from 0 and not passing the second argument at all, in which case it will default to list.length.

```python
list = ["one", "two", "three", "car", "banana"];
list.splice(0)
print(list)
//[]
```

If you just want to remove the last element of the list you can just pass one argument `-1`
```python
arr = ['tv','dvd','cd','vhs','minidisc']
arr.splice(-1)
print(arr)
//["tv", "dvd", "cd", "vhs"]
```

In the same way you can remove any number of items to remove starting from the last one by giving a number of items with `-` sign as an argument:
```python
arr = ['tv','dvd','cd','vhs','minidisc']
arr.splice(-2)
print(arr)
//["tv", "dvd", "cd"]
```




## list.concat()

The `**concat()**` method is used to merge two or more lists. This method does not change the existing lists, but instead returns a new list.

```python
arr1 = ['a', 'b', 'c'];
arr2 = ['d', 'e', 'f'];

arr3 = arr1.concat(arr2);

// arr3 is a new list [ "a", "b", "c", "d", "e", "f" ]
```

While `push` alters the list that invoked it, `concat` returns a new list with the original list joined with the list/s or value/s that were provided as arguments. There are a couple of things to note about `concat` and how it creates the returned list. Both strings and numbers are copied into the list, which means that if the original value is changed, the value in the new list will be unaffected.

```python
arr = []
arr.push('hello')
//1
print(arr)
//["hello"]
arr2 = []
arr2.concat('hi')
//["hi"]
print(arr2)
//[]
arr2 = arr2.concat('hey there')
//["hey there"]
print(arr2)
//["hey there"]
arr = ['Hello', 'How', 'are', 'you', '?']
arr2 = arr.concat()
print('arr',arr)
print('arr2',arr2)
//arr (5) ["Hello", "How", "are", "you", "?"]
//arr2 (5) ["Hello", "How", "are", "you", "?"]
arr2[0]='banana'
print('arr',arr)
print('arr2',arr2)
//arr (5) ["Hello", "How", "are", "you", "?"]
//arr2 (5) ["banana", "How", "are", "you", "?"]
```

## list.indexOf()

The `indexOf` method is used to fetch the index of the list’s element by it’s name.

```python
arr  = ['mike', 'Darth', 'peter']
print('index of mike',arr.indexOf('mike'))
print('index of Darth',arr.indexOf('Darth'))
print('index of peter',arr.indexOf('peter'))
//index of mike  0
//index of Darth 1
//index of peter 2
```

Not only we can use the `indexOf` method to find out the index of a specific element by its name, but we can also use it to find out if the element is in the list at all.

When we call the `indexOf` method it returns the index of the element if it finds it, and if it doesn't it will **always** return -1:
   
```python 
arr = ['mike','peter','john']
print(arr.indexOf('i am not in the list'))
print(arr.indexOf('mike'))
print(arr.indexOf('banana'))
print(arr.indexOf('coca cola'))
print(arr.indexOf('john'))
print(arr.indexOf('peter'))

//-1
// 0
//-1
//-1
// 2
// 1
```

## list.includes()

Similarly to `indexOf` we have the method `list.includes`, which is used to determine whether the element is present in the list or not.

```python
arr = ['Darth', 'Kylo', 'Luke']
arr.includes('Luke')
//true

arr = ['zero','one','two','three','four','five']
print(!arr.includes('zero'))
print(arr.includes('zero'))
print(arr.includes('banana'))
print(arr.includes('five'))
//false
//true
//false
//true
```

## **arr.sort()**

`list.sort` is a built-in JS method that allows effortlessly to sort the elements of the list alphabetically.

In order to use it all we need to to is to call the `.sort` method on our list.

```python
arr = ["f","h","z","t","q","a","s","f","g","o",]
arr.sort()
//["a", "f", "f", "g", "h", "o", "q", "s", "t", "z"]
```
















You can add as many elements as you'd like using this syntax:
```python
mylist = [];
mylist[0] = "new element"
mylist[1] = "banana"
mylist[2] = "car"
print(mylist)
```

Bare in mind that if you try adding an element to an index that you have previously assigned to another element it will overwrite it. 
```python
mylist = [];
mylist[0] = "new element"
print(`mylist after adding the first element to index 0 ${mylist}`)
mylist[0] = "banana"
print(`mylist after adding the second element to index 0 ${mylist}`)
```

## Destructuring lists

Destructuring is an elegant way of extracting data from lists and objects in python.

Destructuring lists is based on the index or position of the items inside lists. In the below example we are taking the first property from the list and assigning to a variable called `one`.

The reason we are grabbing the first element of the list is because we are passing only one in the const `one` declaration.

```python
const people = ['Peter','Robert','Jenny']
const [one] = people;  
print(one);
```

In the following example we will `print` the second element of the same list.

```python
const people = ['Peter','Robert','Jenny']
const [one, two] = people;  
print(two);
//Robert
```

Of course the fact that we called them `one` and `two` has no effect on how it works.

```python
    const people = ['Peter','Robert','Jenny']
    const [banana, orange] = people;  
    print(orange);
    //Robert
```

## list methods

# Strings

Strings also share the length property of the list
```python
fruit = "banana"
print(fruit.length)
print(fruit[0])
print(fruit[1])
print(fruit[2])
print(fruit[3])
print(fruit[4])
print(fruit[5])
//6
//b
//a
//n
//a
//n
//a
```
 -->