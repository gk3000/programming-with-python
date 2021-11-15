# Strings, input()

---

<details>
    <summary>Strings</summary><div class='video-container'>
        <iframe src="https://www.youtube.com/embed/A3kBZdacsbg?rel=0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe></div>
</details>

---

Declaring a string means assigning a value inside double or single quotes to a variable, like:

```python
name ='Bob'
city ='Barcelona'
favorite_food = "pizza"
```

Strings also share the length property of the list and they have indexes as well:

```python
fruit = "banana"
len(fruit)
# 6
fruit[0]
# 'b'
```

Indexes are starting from 0 as usual, and if we will use negative indexes it will start counting fom the end of the string:

```python
fruit = "banana"
fruit[-1]
# 'a'
```

If we need to have quotes inside a string we can mix double and single quotes like this:

```python
full_name = "Bob 'Coder' Robinson"
```

As in other programming languages there are escape sequencies if you want to add something special inbto your string:
```
Escape Sequence		Meaning								Notes
\newline			Backslash and newline ignored
\\					Backslash (\)
\'					Single quote (')
\"					Double quote (")
\a					ASCII Bell (BEL)
\b					ASCII Backspace (BS)
\f					ASCII Formfeed (FF)
\n					ASCII Linefeed (LF)
\r					ASCII Carriage Return (CR)
\t					ASCII Horizontal Tab (TAB)
\v					ASCII Vertical Tab (VT)
\ooo				Character with octal value ooo		(1,3)
\xhh 				Character with hex value hh			(2,3)
```

So to print text with a new line break we can add `\n` into a string:
```python
with_line_break = 'Some text and \na new line'
with_line_break
# 'Some text and \na new line'
print(with_line_break)
# Some text and 
# a new line
```

---

## String concatenation

We can join or concatenate string with `+` operator and if we need space between them we add `' '`:

```python
name = 'Boba'
last_name = 'Fett'
full_name = name + ' ' + last_name
full_name
# 'Boba Fett'
```

We can also use `+=` operator to concatenate string:
```python
full_name = 'Boba'
full_name += ' Fett'
full_name
# 'Boba Fett'
```

---

## Interpolating strings

With f-strings we can embedd Python expressions into strings to combine some text with variables, for example.


```python
name    = "Boba"
surname = "Fett"
age     = 35
print(f'Mr.{name} {surname} is {age} years old')
# or
full_name = f'Mr.{name} {surname} is {age} years old'
print(full_name)
```

As you can see it's a convenient way to mix variables with text and we can also join string without having to worry about `+` and `' '` and also giving us a much more natural way to deal with spacing.

F-strings are straightforward to use, all we need to remember is to put `f` before the value and to inject a variable in the sentence we need to wrap it in curly brackets `{variable_goes_here}`.

Actually, in curly brackets we can add any valid Python expression and it will be avaluated properly:

```python
name    = "Boba"
surname = "Fett"
age     = 35
print(f'Mr.{name} {surname} is {age+100} years old')
# Mr.Boba Fett is 135 years old
```

---

## input()

Now with all this we can probably build a super simple code to interact with the user and to solve the common task of getting user input we are going to use `input()` built-in function. 

We want to greet user by name, but we do not know the name, so we will ask for it.

```python
print('Hello, stranger! what\'s your name?')
user_name = input()
print(f'Welcome back, {user_name}!')
```

---

## String methods

There are some useful string methods which allow us to manipulate string easily. 

### slicing a string

We can slice a string with slice syntax and return the removed characters. First value is for the starting index, second is for the index until which we want to slice. This doesn't modify the original string:

```python
my_str = "We are in this together!"
removed_chars = my_str[3:6]
print(removed_chars)
# are
# another way to do the same is
print(my_str[3:6])
# are
my_str
# 'We are in this together!'
```

With just one value provided we either print the entire string starting from the specified index if it's the first one or print the string up to specified index if it's the second one

```python
print(my_str[3:])
# are in this together!
print(my_str[:6])
# We are
```

With negative indexes we can slice from the end of a string:
```python
print(my_str[-13:-6])
# his tog
```

---

### .strip()

With this method we can easily remove empty spaces around our string: 
```python
my_name = " Boba Fett "
print(my_name.strip()) 
# 'Boba Fett'
```

But original string is not modified, to do so we need to reassign it's value:

```python
my_name = my_name.strip()
my_name
# 'Boba Fett'
```

---

### .lower() 
This method returns the string in lower case (it doesn't modify the original string):

```python
my_name
# 'Boba Fett'
my_name.lower()
# 'boba fett'
```

---

### .upper() 

This method returns the string in upper case (it doesn't modify the original string):

```python
my_name
# 'Boba Fett'
my_name.upper()
# 'BOBA FETT'
```

---

### .replace()

Returns a string with replaced character(s) in the string to another one(s) without modifying the original string:
```python
my_name.replace('Boba','Jango')
#'Jango Fett'
my_name
#'Boba Fett'
```

---

### .split()

Returns a list of values derived from splitting a given string with provided separator:

```python
myStr = "I-am-too-young-to-drive-a-car"
print(myStr.split('-'))
# ["I", "am", "too", "young", "to", "drive", "a", "car"]
print(myStr)
# I-am-too-young-to-drive-a-car
```

As you can see `string.split()` does not affect the original string, so should you want to use the “split” string you need to reassign it

```python
myStr = "I-am-too-young-to-drive-a-car"
myStr = myStr.split('-')
print(myStr)
# ["I", "am", "too", "young", "to", "drive", "a", "car"]
```

However our string still isn't very useful, in order to have a nicely formatted string we need to combine the method `split` with `string.join()` passing an empty space as argument.

---

### .join()

Let’s see in steps what is happening. 

```python
myString= "I_love_eating_apples"
print('Original string ==>', myString)
# Original string ==> I_love_eating_apples

mySplitString = myString.split("_")
print('Split by underscore string ==>', mySplitString)
# Split by underscore string ==> ['I', 'love', 'eating', 'apples']

mySplitAndStringJoinedWithNoArgument = ''.join(mySplitString)
print('Joined with no argument ==>', mySplitAndStringJoinedWithNoArgument)
# Joined with no argument ==> Iloveeatingapples

splitStringAndJoinedString = " ".join(mySplitString) 
print('Joined with space between elements ==>', splitStringAndJoinedString)
# Joined with space between elements ==> I love eating apples

# we can chain methods into a single line expression:
splitStringAndJoinedString = " ".join(myString.split("_"))
print('Split and joined in one-liner ==>', splitStringAndJoinedString)
# Split and joined in one-liner ==> I love eating apples
```

---

## String comprehension

Is also working for the strings:

```python
foo = 'force'
bar = [item.upper() for item in foo]
bar
# ['F', 'O', 'R', 'C', 'E']
bar = ''.join(bar)
bar
# 'FORCE'
```

Conditional logic can be also added into LC for string. What if we have a string and we want to get rid of unwanted characters like `#`, `_`, `*` and `%`:

```python
foo = 'He*ll_o f#ri%end%s'
foo = ''.join([item for item in foo if item not in "#_*%"])
foo
# 'Hello friends'
```

---

## Checking a string

To see if a string contains some specific character(s) we can use `in` keyword:
```python
quote = 'I am your father, Luke'
dad = 'father' in quote
print(dad)
```
And to check if character(s) are not in the string we use `not` keyword:
```python
quote = 'I am your father, Luke'
mom = 'mother' not in quote
print(mom)
```

<img src="./pics/darth.jpg">