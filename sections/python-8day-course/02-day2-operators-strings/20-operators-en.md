# Python Operators

## Boolean Values

Boolean represents one of two values: `True` or `False`.

```python
print(True)   # True
print(False)  # False

# Note: Must be capitalized!
# true   # NameError
# false  # NameError
```

## Assignment Operators

The `=` operator assigns values to variables.

```python
x = 5
name = "Python"
is_valid = True
```

### Compound Assignment

```python
x = 10
x += 5   # x = x + 5  →  15
x -= 3   # x = x - 3  →  12
x *= 2   # x = x * 2  →  24
x /= 4   # x = x / 4  →  6.0
x //= 2  # x = x // 2 →  3.0
x %= 2   # x = x % 2  →  1.0
x **= 3  # x = x ** 3 →  1.0
```

# Arithmetic Operators

Perform mathematical calculations.

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `5 - 3` | `2` |
| `*` | Multiplication | `5 * 3` | `15` |
| `/` | Division | `5 / 2` | `2.5` |
| `%` | Modulus | `5 % 2` | `1` |
| `//` | Floor Division | `5 // 2` | `2` |
| `**` | Exponentiation | `5 ** 2` | `25` |

### Examples

```python
# Basic operations
print(10 + 5)   # 15
print(10 - 5)   # 5
print(10 * 5)   # 50
print(10 / 5)   # 2.0 (always returns float)

# Modulus - remainder after division
print(10 % 3)   # 1
print(17 % 5)   # 2

# Floor division - integer division
print(10 // 3)  # 3
print(17 // 5)  # 3

# Exponentiation
print(2 ** 3)   # 8 (2 * 2 * 2)
print(5 ** 2)   # 25
```

### Practical Calculations

```python
# Calculate circle area
radius = 10
pi = 3.14
area = pi * radius ** 2
print(f"Area: {area}")  # Area: 314.0

# Calculate rectangle area
length = 15
width = 8
area = length * width
print(f"Rectangle area: {area}")  # 120

# Convert temperature
celsius = 25
fahrenheit = (celsius * 9/5) + 32
print(f"{celsius}°C = {fahrenheit}°F")  # 25°C = 77.0°F
```

# Comparison Operators

Compare two values and return Boolean result.

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `==` | Equal | `5 == 5` | `True` |
| `!=` | Not equal | `5 != 3` | `True` |
| `>` | Greater than | `5 > 3` | `True` |
| `<` | Less than | `5 < 3` | `False` |
| `>=` | Greater or equal | `5 >= 5` | `True` |
| `<=` | Less or equal | `3 <= 5` | `True` |

### Examples

```python
print(3 > 2)      # True
print(3 >= 2)     # True
print(3 < 2)      # False
print(2 <= 3)     # True
print(3 == 2)     # False
print(3 != 2)     # True

# Comparing strings
print('mango' == 'mango')     # True
print('apple' != 'orange')    # True

# Comparing lengths
print(len('hello') == 5)      # True
print(len('python') > len('py'))  # True
```

# Logical Operators

Combine conditional statements.

| Operator | Description | Example |
|----------|-------------|---------|
| `and` | True if both are true | `x > 0 and x < 10` |
| `or` | True if at least one is true | `x < 0 or x > 10` |
| `not` | Reverses the result | `not(x > 5)` |

### Examples

```python
# and operator
print(True and True)    # True
print(True and False)   # False
print(3 > 2 and 10 > 5) # True

# or operator
print(True or False)    # True
print(False or False)   # False
print(3 < 2 or 10 > 5)  # True

# not operator
print(not True)         # False
print(not False)        # True
print(not 3 > 2)        # False
```

### Practical Examples

```python
# Check if number is in range
age = 25
is_adult = age >= 18 and age < 65
print(is_adult)  # True

# Check multiple conditions
score = 85
passed = score >= 60 and score <= 100
print(passed)  # True

# Weekend check
day = "Saturday"
is_weekend = day == "Saturday" or day == "Sunday"
print(is_weekend)  # True
```

# Membership and Identity Operators

Check if a value exists in a sequence.

| Operator | Description |
|----------|-------------|
| `in` | True if value exists in sequence |
| `not in` | True if value doesn't exist |

```python
# String membership
print('P' in 'Python')        # True
print('x' in 'Python')        # False
print('thon' in 'Python')     # True

# List membership
fruits = ['apple', 'banana', 'orange']
print('apple' in fruits)      # True
print('grape' in fruits)      # False
print('grape' not in fruits)  # True
```

## Identity Operators

Check if two variables refer to the same object.

| Operator | Description |
|----------|-------------|
| `is` | True if same object |
| `is not` | True if different objects |

```python
x = [1, 2, 3]
y = [1, 2, 3]
z = x

print(x == y)     # True (same content)
print(x is y)     # False (different objects)
print(x is z)     # True (same object)

# Common use with None
value = None
print(value is None)      # True
print(value is not None)  # False
```

