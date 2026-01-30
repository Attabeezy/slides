# Built-in Functions

## What are Built-in Functions?

Python provides many built-in functions that are always available without importing.

## Common Built-in Functions

### Output: print()

Display output to the console:

```python
print("Hello, World!")
print("Python", "is", "awesome")  # Multiple arguments
print("Number:", 42)

# Separator and end
print("A", "B", "C", sep="-")  # A-B-C
print("Hello", end=" ")
print("World")  # Hello World
```

### Input: input()

Get user input (returns a string):

```python
name = input("What is your name? ")
print("Hello", name)

age = input("How old are you? ")
print("You are", age, "years old")
```

## Type Checking: type()

Check the data type of a value:

```python
print(type(42))           # <class 'int'>
print(type(3.14))         # <class 'float'>
print(type("hello"))      # <class 'str'>
print(type(True))         # <class 'bool'>
print(type([1, 2, 3]))    # <class 'list'>
```

### Length: len()

Get the length of a collection or string:

```python
print(len("Python"))         # 6
print(len([1, 2, 3, 4, 5]))  # 5
print(len({'a': 1, 'b': 2})) # 2
```

# Mathematical Functions

```python
# Absolute value
print(abs(-10))        # 10
print(abs(-3.14))      # 3.14

# Maximum and minimum
print(max(1, 5, 3, 9, 2))     # 9
print(min(1, 5, 3, 9, 2))     # 1
print(max([10, 20, 30]))      # 30

# Sum
print(sum([1, 2, 3, 4, 5]))   # 15

# Power
print(pow(2, 3))       # 8 (2^3)

# Round
print(round(3.14159, 2))  # 3.14
```

# Range and Help Functions

Generate a sequence of numbers:

```python
# Single argument (stop)
list(range(5))         # [0, 1, 2, 3, 4]

# Two arguments (start, stop)
list(range(2, 7))      # [2, 3, 4, 5, 6]

# Three arguments (start, stop, step)
list(range(0, 10, 2))  # [0, 2, 4, 6, 8]
```

### Help Functions

```python
# Get help on a function
help(print)

# List attributes and methods
dir(str)
```

## Summary Table

| Function | Purpose | Example |
|----------|---------|---------|
| `print()` | Display output | `print("Hello")` |
| `input()` | Get user input | `name = input("Name: ")` |
| `type()` | Check data type | `type(42)` |
| `len()` | Get length | `len("Python")` |
| `int()` | Convert to integer | `int("42")` |
| `float()` | Convert to float | `float("3.14")` |
| `str()` | Convert to string | `str(42)` |
| `abs()` | Absolute value | `abs(-10)` |
| `max()` | Maximum value | `max(1, 5, 3)` |
| `min()` | Minimum value | `min(1, 5, 3)` |
| `sum()` | Sum of items | `sum([1, 2, 3])` |
| `round()` | Round number | `round(3.14, 1)` |
| `help()` | Get documentation | `help(print)` |

