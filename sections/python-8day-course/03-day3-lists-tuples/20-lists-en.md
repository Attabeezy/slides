# Lists in Python

## What are Lists?

Lists are **ordered**, **mutable** (changeable) collections that can hold items of different types.

**Key characteristics:**
- Ordered: Items maintain their position
- Mutable: Can be modified after creation
- Allow duplicates
- Can contain mixed data types

## Creating Lists

### Empty Lists

```python
# Method 1: Square brackets
empty_list = []

# Method 2: list() constructor
empty_list = list()

print(len(empty_list))  # 0
```

### Lists with Initial Values

```python
# List of integers
numbers = [1, 2, 3, 4, 5]

# List of strings
fruits = ['apple', 'banana', 'orange']

# Mixed data types
mixed = [1, 'hello', 3.14, True, None]

# Nested lists
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

## Accessing List Items

### Positive Indexing

Index starts at 0 for the first item.

```python
fruits = ['apple', 'banana', 'orange', 'mango']

print(fruits[0])    # 'apple' (first item)
print(fruits[1])    # 'banana'
print(fruits[3])    # 'mango' (last item)

# Last item using length
last_index = len(fruits) - 1
print(fruits[last_index])  # 'mango'
```

### Negative Indexing

Negative indices count from the end: -1 is the last item.

```python
fruits = ['apple', 'banana', 'orange', 'mango']

print(fruits[-1])   # 'mango' (last item)
print(fruits[-2])   # 'orange' (second to last)
print(fruits[-4])   # 'apple' (first item)
```

## Slicing Lists

Extract portions of a list using `[start:stop:step]`.

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Basic slicing
print(numbers[2:5])     # [2, 3, 4]
print(numbers[:4])      # [0, 1, 2, 3]
print(numbers[5:])      # [5, 6, 7, 8, 9]
print(numbers[:])       # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] (copy)

# With step
print(numbers[::2])     # [0, 2, 4, 6, 8] (every 2nd item)
print(numbers[1::2])    # [1, 3, 5, 7, 9] (odd numbers)

# Reverse
print(numbers[::-1])    # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

# Negative indices
print(numbers[-3:])     # [7, 8, 9]
print(numbers[:-3])     # [0, 1, 2, 3, 4, 5, 6]
```

## Modifying Lists

Lists are mutable - you can change their contents.

```python
fruits = ['apple', 'banana', 'orange']

# Change single item
fruits[0] = 'pear'
print(fruits)  # ['pear', 'banana', 'orange']

# Change multiple items
fruits[1:3] = ['grape', 'kiwi']
print(fruits)  # ['pear', 'grape', 'kiwi']

# Change last item
fruits[-1] = 'mango'
print(fruits)  # ['pear', 'grape', 'mango']
```

## Checking Membership

Use `in` and `not in` operators.

```python
fruits = ['apple', 'banana', 'orange']

print('apple' in fruits)        # True
print('grape' in fruits)        # False
print('grape' not in fruits)    # True

# In conditional
if 'banana' in fruits:
    print("We have bananas!")
```

## Unpacking Lists

Assign list items to variables.

```python
# Basic unpacking
fruits = ['apple', 'banana', 'orange']
first, second, third = fruits
print(first)   # 'apple'
print(second)  # 'banana'
print(third)   # 'orange'

# Unpacking with * (rest)
numbers = [1, 2, 3, 4, 5]
first, second, *rest = numbers
print(first)   # 1
print(second)  # 2
print(rest)    # [3, 4, 5]

# Multiple * positions
first, *middle, last = numbers
print(first)   # 1
print(middle)  # [2, 3, 4]
print(last)    # 5
```

## List Concatenation and Repetition

```python
# Concatenation with +
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)  # [1, 2, 3, 4, 5, 6]

# Repetition with *
numbers = [0, 1]
repeated = numbers * 3
print(repeated)  # [0, 1, 0, 1, 0, 1]
```

## Common List Operations

```python
fruits = ['apple', 'banana', 'orange', 'banana']

# Length
print(len(fruits))              # 4

# Count occurrences
print(fruits.count('banana'))   # 2

# Find index
print(fruits.index('orange'))   # 2

# Check if empty
if fruits:
    print("List is not empty")
```

## Lists vs Strings

Both are sequences, but lists are mutable.

```python
# Convert string to list
text = "Python"
letters = list(text)
print(letters)  # ['P', 'y', 't', 'h', 'o', 'n']

# Split string into list
sentence = "Hello World Python"
words = sentence.split()
print(words)  # ['Hello', 'World', 'Python']
```

