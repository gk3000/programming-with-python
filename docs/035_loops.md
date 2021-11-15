# Loops

---

<details>
    <summary>Loops</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/9_k2ysCQ6L8?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

Loops are a way to repeat a certain action(s) a given number of times or based on specified condition. 

Loops are used for all kinds of iterations allowing code to be executed repeatedly. After all this is what computers are really good at: repeat lots of things really fast!

To loop we need to have some iterable data, like list of elements, or a string or range of numbers. 

So let's start with the most basic loop to go through a string and print out all of it's characters one by one:

```python
for char in 'banana':
	print(char)
```

The output will be
```python
b
a
n
a
n
a
```
Of course we can loop on some variable instead of literal value, which is what we normally do:

```python
fruit = 'banana'
for char in fruit:
	print(char)
```

If we want to print every characer 5 times we can do it with this:
```python
fruit = 'banana'
for char in fruit:
	print(char*5)
```

If we want to print out numbers from 1 to 10 we can do it with a range of numbers:

```python
numbers = range(1,11)
for num in numbers:
	print(num)
```

Notice how the second value in the range IS NOT included in the output of the loop. 

---

## `for` loop

1. We start with the keyword `for`.
2. Then we give a custom name variable to be used as an item or iterator inside the loop
3. Then we add a colon and on a new line with an indent give instructions what to do for every iteration of a loop


So to print out numbers from 0 to 5 it would be

```python
numbers = range(0,6)
for num in numbers:
	print(num)
```

And to print our numbers from 5 to 0 we would a third argument -- step.

```python
numbers = range(5,-1,-1)
for num in numbers:
	print(num)
```

So this loop wil lstart from 5 and with step -1 iterate until it will reach -1.

For sure we can use a step for any range:
```python
numbers = range(1,11, 2)
for num in numbers:
	print(num)
```

This will give us:
```
1
3
5
7
9
```

And of course we can use variables in the loop to make them dynamic:
```python
start_range = 1
end_range = 11
range_step=2
numbers = range(start_range, end_range, range_step)
for num in numbers:
	print(num)
```

And with just one number in the range we will have a range from 0 till (exclusively) this given number:
```python
range(5)
# has number 0-4
```

Let's make a super basic program to ask for a number of drinks we want to have and serving it to us:
```python
drinks = input('How many drinks do you want? ');
drinks = int(drinks);
for drink in range(drinks):
	print('Cheers!')
```

And now classic FizzBuzz exercise where we loop through a range of numbers and if the current number is divisible by 3 we will FIZZ, if it is divisible by 5 we will BUZZ and if it is divisible by 3 and 5 we will FizzBuzz will look like that:
```python
for num in range (1,100):
	if num % 15 == 0 :
		print(f'{num} FizzBuzz')
	elif num % 3 == 0 :
		print(f'{num} Fizz')
	elif num % 5 == 0 :
		print(f'{num} Buzz')
```

---

## `while` Loop

The while statement creates a loop that executes a specified statement as long as the test condition evaluates to true. The condition is evaluated before executing the statement.

In other words the loop keeps running as long as what is inside the parentheses is true.

So if we write:

```python
while 10 > 5:
    #run forever

```

This will run forever because 10 will always bigger than 5.

```python
while condition:
    #statement

```

So in order to make our loop run a set amount of time we can do exactly the same thing we did with the `for` loop although the syntax isn’t identical.

```python
num = 0
while num < 10 :
    print(num)
    num += 1
print("Loop is finished")
```

Of course we can use `while` loop to do the same things as with `for` loop like printing out a range of numbers:

```python
numbers = range(0,6)
for num in numbers:
	print(num)
```
with `while` loop would be 

```python
num=0
while num < 6:
	print(num)
	num+=1
```

With `while` loop we can run a loop *unknown* number of times:
```python
color='black'
user_guess = input('What is my favorite color? ')
while user_guess != color:
	print('Nope!')
	user_guess = input('What is my favorite color? ')
print('You are right! It is black.')
```

---


## Breaking the loop

We can stop the loop (`for` or `while`) at any moment with a `break` keyword:
```python
color='black'
user_guess = input('What is my favorite color? ')
while user_guess != color:
	if user_guess == 'stop':
		break
	print('Nope!')
	user_guess = input('What is my favorite color? ')
```

---

## Looping through a list:

```python
fruits = ['banana', 'orange', 'pineapple', 'coke']

for fruit in fruits:
	print(fruit)
```

If we want to only print fruits which are shorter than 5 characters:

```python
fruits = ['banana', 'orange', 'pineapple', 'coke']

for fruit in fruits:
	if len(fruit) < 5:
		print(fruit)
```

And we can loop with `while` as well:
```python
fruits = ['banana', 'orange', 'pineapple', 'coke']
i=0

while i < len(fruits):
	print(fruits[i])
	i+=1
```

And the same backwards:
```python
fruits = ['banana', 'orange', 'pineapple', 'coke']
i=len(fruits)-1

while i >= 0:
	print(fruits[i])
	i-=1
```

We can also have access to the index and item from the same loop by using our iterator:

```python
fruits = ['banana', 'orange', 'pineapple', 'coke']
i=0

while i < len(fruits):
	print(f"Item number {i} is {fruits[i]}")
	i+=1
```

---

### Looping through a nested list

With nested lists we have nested loops, the first one is going through the top level items and the second one is looping through the current item untill it will finish.

So with nums = `[[1,2,3],['a','b','c'],[True, False,True]]` the parent loop will have first item which is `[1,2,3]` and then the nested loop will go through 1, 2, 3. After that the parent loop will go to the next item `['a','b','c']` and the nested loop wiil go through a, b, c and so on:

```python
nums = `[[1,2,3],['a','b','c'],[True, False,True]]
for ls in nums:
	for item in ls:
		print(item)
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


