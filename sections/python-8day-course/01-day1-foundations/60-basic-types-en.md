# Basic Data Types

## Overview

Python has several built-in data types. Understanding these is fundamental to programming.

## Numeric Types

### Integer (int)

Whole numbers, positive or negative, without decimals:

```python
age = 25
temperature = -5
population = 1000000
```

### Float

Numbers with decimal points:

```python
price = 19.99
pi = 3.14159
temperature = -3.5
```

### Complex

Numbers with real and imaginary parts (less common):

```python
z = 2 + 3j
w = complex(1, 4)  # 1 + 4j
```

# Text Type

### String (str)

Sequence of characters enclosed in quotes:

```python
name = "Alice"
message = 'Hello, World!'
paragraph = """This is a
multi-line string"""
```

# Boolean Type

### Boolean (bool)

Represents True or False:

```python
is_active = True
is_valid = False
has_access = True
```

**Note:** Capitalization matters! `True` and `False` must be capitalized.

## None Type

### None

Represents the absence of a value:

```python
result = None
middle_name = None
```

# Collection Types (Preview)

You'll learn these in detail later:

### List

Ordered, mutable collection:

```python
fruits = ['apple', 'banana', 'orange']
numbers = [1, 2, 3, 4, 5]
mixed = [1, 'hello', True, 3.14]
```

### Tuple

Ordered, immutable collection:

```python
coordinates = (10, 20)
rgb = (255, 0, 128)
```

### Dictionary (dict)

Key-value pairs:

```python
person = {
    'name': 'Alice',
    'age': 25,
    'city': 'New York'
}
```

### Set

Unordered collection of unique items:

```python
unique_numbers = {1, 2, 3, 4, 5}
vowels = {'a', 'e', 'i', 'o', 'u'}
```

## Type Comparison

| Type | Example | Mutable | Ordered |
|------|---------|---------|---------|
| int | `42` | No | - |
| float | `3.14` | No | - |
| str | `"hello"` | No | Yes |
| bool | `True` | No | - |
| list | `[1, 2, 3]` | Yes | Yes |
| tuple | `(1, 2, 3)` | No | Yes |
| dict | `{'a': 1}` | Yes | Yes (3.7+) |
| set | `{1, 2, 3}` | Yes | No |

