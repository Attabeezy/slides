# Tuples in Python

## What are Tuples?

Tuples are **ordered**, **immutable** (unchangeable) collections that can hold items of different types.

**Key characteristics:**
- Ordered: Items maintain their position
- Immutable: Cannot be modified after creation
- Allow duplicates
- Can contain mixed data types
- Generally faster than lists

## Creating Tuples

### Empty Tuples

```python
# Method 1: Parentheses
empty_tuple = ()

# Method 2: tuple() constructor
empty_tuple = tuple()

print(len(empty_tuple))  # 0
```

### Tuples with Values

```python
# Simple tuple
fruits = ('apple', 'banana', 'orange')

# Mixed data types
mixed = (1, 'hello', 3.14, True)

# Nested tuples
nested = ((1, 2), (3, 4), (5, 6))

# Single item tuple (note the comma!)
single = (42,)  # Comma is required
not_tuple = (42)  # This is just an int!
print(type(single))      # <class 'tuple'>
print(type(not_tuple))   # <class 'int'>
```

### Tuple Packing

```python
# Without parentheses (tuple packing)
coordinates = 10, 20, 30
print(coordinates)  # (10, 20, 30)
print(type(coordinates))  # <class 'tuple'>
```

# Accessing Tuple Items

Tuples use indexing just like lists.

### Positive Indexing

```python
fruits = ('apple', 'banana', 'orange', 'mango')

print(fruits[0])    # 'apple'
print(fruits[2])    # 'orange'
print(fruits[3])    # 'mango'
```

### Negative Indexing

```python
fruits = ('apple', 'banana', 'orange', 'mango')

print(fruits[-1])   # 'mango'
print(fruits[-2])   # 'orange'
print(fruits[-4])   # 'apple'
```

## Slicing Tuples

```python
numbers = (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

print(numbers[2:5])     # (2, 3, 4)
print(numbers[:4])      # (0, 1, 2, 3)
print(numbers[5:])      # (5, 6, 7, 8, 9)
print(numbers[::2])     # (0, 2, 4, 6, 8)
print(numbers[::-1])    # (9, 8, 7, 6, 5, 4, 3, 2, 1, 0)
```

## Immutability

Tuples cannot be modified after creation.

```python
fruits = ('apple', 'banana', 'orange')

# These will cause errors:
# fruits[0] = 'pear'        # TypeError!
# fruits.append('grape')    # AttributeError!
# fruits.remove('banana')   # AttributeError!
# del fruits[0]             # TypeError!
```

# Tuple Operations

### Concatenation

```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
combined = tuple1 + tuple2
print(combined)  # (1, 2, 3, 4, 5, 6)
```

### Repetition

```python
tuple1 = (1, 2)
repeated = tuple1 * 3
print(repeated)  # (1, 2, 1, 2, 1, 2)
```

### Membership

```python
fruits = ('apple', 'banana', 'orange')

print('apple' in fruits)       # True
print('grape' in fruits)       # False
print('grape' not in fruits)   # True
```

## Tuple Methods

Tuples have only 2 methods (because they're immutable).

### count() - Count Occurrences

```python
numbers = (1, 2, 3, 2, 4, 2, 5)
print(numbers.count(2))  # 3
print(numbers.count(9))  # 0
```

### index() - Find First Index

```python
fruits = ('apple', 'banana', 'orange', 'banana')
print(fruits.index('banana'))  # 1 (first occurrence)
print(fruits.index('orange'))  # 2

# Raises ValueError if not found
# print(fruits.index('grape'))  # ValueError!
```

# Tuple Unpacking

Assign tuple items to variables.

```python
# Basic unpacking
point = (10, 20)
x, y = point
print(x)  # 10
print(y)  # 20

# Multiple values
person = ('Alice', 25, 'Engineer')
name, age, job = person
print(name)  # 'Alice'
print(age)   # 25
print(job)   # 'Engineer'

# Swap variables
a = 5
b = 10
a, b = b, a  # Swap using tuple packing/unpacking
print(a)  # 10
print(b)  # 5
```

### Unpacking with *

```python
numbers = (1, 2, 3, 4, 5)

# First, rest pattern
first, *rest = numbers
print(first)  # 1
print(rest)   # [2, 3, 4, 5] (note: becomes list!)

# First, middle, last
first, *middle, last = numbers
print(first)   # 1
print(middle)  # [2, 3, 4]
print(last)    # 5
```

# Converting Between Lists and Tuples

### Tuple to List

```python
my_tuple = (1, 2, 3, 4, 5)
my_list = list(my_tuple)
print(my_list)  # [1, 2, 3, 4, 5]
print(type(my_list))  # <class 'list'>

# Now you can modify it
my_list.append(6)
my_list[0] = 99
print(my_list)  # [99, 2, 3, 4, 5, 6]
```

### List to Tuple

```python
my_list = [1, 2, 3, 4, 5]
my_tuple = tuple(my_list)
print(my_tuple)  # (1, 2, 3, 4, 5)
print(type(my_tuple))  # <class 'tuple'>
```

### Modifying Tuples Indirectly

```python
# Convert to list, modify, convert back
fruits = ('apple', 'banana', 'orange')
fruits_list = list(fruits)
fruits_list.append('grape')
fruits = tuple(fruits_list)
print(fruits)  # ('apple', 'banana', 'orange', 'grape')
```

## Deleting Tuples

You can delete entire tuples, but not individual items.

```python
fruits = ('apple', 'banana', 'orange')

# Delete entire tuple
del fruits
# print(fruits)  # NameError: fruits not defined

# Can't delete items
fruits = ('apple', 'banana', 'orange')
# del fruits[0]  # TypeError!
```

## Joining Tuples

```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
tuple3 = (7, 8, 9)

# Join multiple tuples
joined = tuple1 + tuple2 + tuple3
print(joined)  # (1, 2, 3, 4, 5, 6, 7, 8, 9)
```

# Common Use Cases for Tuples

### Function Return Values

```python
def get_coordinates():
    return (10, 20)  # Return tuple

x, y = get_coordinates()
print(f"x={x}, y={y}")  # x=10, y=20
```

### Dictionary Keys

```python
# Tuples can be dictionary keys (lists cannot!)
locations = {
    (0, 0): 'origin',
    (1, 0): 'right',
    (0, 1): 'up'
}
print(locations[(0, 0)])  # 'origin'
```

### Data That Shouldn't Change

```python
# Constants or configuration
WEEKDAYS = ('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')
RGB_COLORS = ((255, 0, 0), (0, 255, 0), (0, 0, 255))
```

## Tuple vs List Summary

| Feature | Tuple | List |
|---------|-------|------|
| Syntax | `()` | `[]` |
| Mutable | No | Yes |
| Methods | 2 (count, index) | Many (append, remove, etc.) |
| Speed | Faster | Slower |
| Memory | Less | More |
| Use case | Fixed data | Changing data |

