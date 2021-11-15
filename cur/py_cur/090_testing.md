statement assert

```python
def add_positive_numbers(x, y):
    assert x > 0 and y > 0, "Both numbers must be positive!"
    return x + y

add_positive_numbers(1, 1) # 2
add_positive_numbers(1, -1) # AssertionError: Both numbers must be positive!
```
Run these tests with:
python3 YOUR_FILE_NAME.py

-O will ignore all the assertions, like `python -O your_file.py` 

doctests 

```python
def add(x, y):
    """sum together x and y which are numbers

    >>> add(1, 2)
    3

    >>> add(8, "hi")
    Traceback (most recent call last):
        ...
    TypeError: unsupported operand type(s) for +: 'int' and 'str'
    """
    return a * b
```

Run these tests with:
python3 -m doctest -v YOUR_FILE_NAME.py


# Built-in module unittest 




class SomeTests(unittest.TestCase):

    def setUp(self):
        # do setup here
        pass

    def test_first(self):
        # setUp runs before
        # tearDown runs after
        pass

    def test_second(self):
        # setUp runs before
        # tearDown runs after
        pass

    def tearDown(self):
        # do teardown here
        pass





