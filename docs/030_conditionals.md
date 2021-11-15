# Conditionals

We use conditionals to check if the given condition is met. If the condition is met then the code inside the block will run otherwise it will not.

```python
if 18 > 5 :
  print('18 is bigger than 5')
```
Notice how we use indent in the second line to move `print()` statement a bit to the right -- it is required in Python to have any indent (one or more spaces or tab) for the nested blocks of code. In this case `print()` is nested inside `if` so we have to make this indent, otherwise Python will complain! 

So this code will run because 18 > 5. However the code below will not because 18 is not less than 5 and we will not see anything from the `print()` statement:

```python
if 18 < 5:
  print('18 is smaller than 5')
```

So if the condition isn’t met simply nothing will happen, the code will not run.

Should we want some code to run also if the condition is not met we can use `else`

```python
age = 13
if age >= 18 :
  print("old enough to drive a car")
else :
  print("sorry, too young")

```

---

## Multiple conditionals

With only two options we can use if/else:

```python
canDrink = False
person = 'Peter'
if canDrink == True :
  print(f'{person} can drink')
else :
  print(f'{person} cannot drink')
```

In case we want to check for more than 2 conditions like `if` and `else` we can use `elif`. Let’s say we want to check if a person is old enough to drive and if the person is old enough to drink, assuming that the respective ages are 16 and 21.

```python
age = 19;
if age >= 21 :
  print('can drink')
elif age >= 16 :
  print('can drive')
else :
  print('too young for either.')
```

With if/elfi/else only one of the conditions can trigger, everything else is ignored.

In the next example we ccheck if age is bigger or equal to 18, if not we print 'far too young'. If it is then we check if haveDrivingLicense is True or not and print corresponding message. We go to this block of nested conditionals only if the parent condition (agi is bigger or equal to 18) was true:

```python
age = 22;
haveDrivingLicense = False;
if age >= 18 :
  if haveDrivingLicense == True :
    print("good to drive")
  else :
    print("go to driving school")
else :
  print("far too young!")
```

In here we check if person has truthy value, and if it does we go into nested conditions. Any valid value would be truthy except for boolean `False`, empty objects, empty strings, None and 0:
```python
person_can_drive = None
person = 'mike'
personAge = 19
if person :
  if personAge >= 18 :
    person_can_drive = True
  if person_can_drive :
    print(f'{person} can drive')
#mike can drive
```

Another example:

```python
peterAge = 15
if peterAge >= 14 :
  print('peter can go to see an horror movie')
elif peterAge <14 :
  print('peter is too young to watch horror movies')
#peter can go to see an horror movie
```

We can check anything with conditionals, not just numbers:

```python
fruits = ['apple','orange','pineapple','banana']
if type(fruits) == list :
  if len(fruits)>3 :
    print(f"the variable fruit is of type {type(fruits)} and it's length is more than 3")
```

---

## Logical operators

We can combine our comparison operators with logics `and`, `or` and `not`

### Logical AND (`and`)

The following code shows examples of the `and` (logical AND) operator.

```python
name = "Luke"
surname = "Skywalker"
if name == 'Luke' and surname == 'Skywalker' :
  print('welcome Luke')
```

With the `and` operator we are checking multiple conditions and it evaluate to true only if both conditions are met. So for example the below code will not evaluate to true because not both conditions are true.

```python
name = "Luke"
surname = "Smith"
if name == 'Luke' and surname == 'Skywalker' :
    print('welcome Luke')
```

>We can chain more than two conditions with logical operators.

---

### Logical OR (`or`)

The following code shows examples of the `or` (logical OR) operator. Unlike the `and` operator with the `or` operator only one of the conditions need to be true in order for the statement to evaluate to true. So the below example will evaluate to true because at least one the conditions are true.

```python
name = "Luke"
surname = "Smith"
age    = 111
if name == 'Luke' or surname == 'Skywalker' or age ==35:
    print('Welcome, Luke')
```

---

### Logical NOT (`not`)**

The following code shows examples of the `not` (logical NOT) operator which reverts the value to the opposit for booleans and for truthy/falsy values which are not booleans it reverse to the opposite falsy/truthy value respectively:

```python
n1 = not True # it will be False
n2 = not False # it will be True
n3 = not 'Cat' # it will be False
```

We can also do this:

```python
name = "Darth"
surname = "Vader"
age    = 111
if name != 'Luke' or surname != 'Skywalker' or age is not 35:
    print('Welcome back Lord Vader') # only one condtion being true (age is not 35) is enough to pass it
```

Or to make it more concise:
```python
name = "Darth"
surname = "Vader"
age    = 111
lukes_age = 35
if not(name == 'Luke' and surname == 'Skywalker' and age is 35):
    print('Welcome back Lord Vader')
```
So we are saying, that name shouldn't be Luke, or surname shouldn't be Skywalker or age shouldn't be 35. We don't want Luke at the moment! 

We can also use logical operators during assignments of values:

Try this code:
```python
v1 = 1
v2 = None
v3 = v2 or v1
```

For assignment of v3 Python has a choice between empty v2 or v1 with truthy value of 1 and it will always choose the truthy one! 
