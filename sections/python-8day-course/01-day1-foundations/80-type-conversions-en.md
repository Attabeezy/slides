# Type Conversions

## Why Type Conversion?

Sometimes you need to convert data from one type to another, especially when:
- Performing calculations with user input
- Concatenating numbers with strings
- Working with different data formats

## Explicit Type Conversion

### Converting to Integer: int()

```python
# Float to int (truncates decimal)
print(int(3.14))        # 3
print(int(9.99))        # 9

# String to int
print(int("42"))        # 42
print(int("100"))       # 100

# Boolean to int
print(int(True))        # 1
print(int(False))       # 0
```

**Common Error:**

```python
# This will cause an error:
# int("3.14")  # ValueError: invalid literal
# Fix: convert to float first
int(float("3.14"))  # 3
```

# Converting to Float and String

```python
# Int to float
print(float(42))        # 42.0
print(float(10))        # 10.0

# String to float
print(float("3.14"))    # 3.14
print(float("99.99"))   # 99.99

# Boolean to float
print(float(True))      # 1.0
print(float(False))     # 0.0
```

### Converting to String: str()

```python
# Int to string
print(str(42))          # "42"

# Float to string
print(str(3.14))        # "3.14"

# Boolean to string
print(str(True))        # "True"

# List to string
print(str([1, 2, 3]))   # "[1, 2, 3]"
```

# Converting to Boolean: bool()

```python
# Numbers to boolean
print(bool(0))          # False
print(bool(42))         # True
print(bool(-1))         # True

# Strings to boolean
print(bool(""))         # False (empty string)
print(bool("hello"))    # True

# Collections to boolean
print(bool([]))         # False (empty list)
print(bool([1, 2]))     # True
print(bool(None))       # False
```

# Practical Type Conversion Examples

### User Input Calculations

```python
# Input returns strings, need conversion for math
age_str = input("Enter your age: ")
age = int(age_str)
next_year_age = age + 1
print(f"Next year you will be {next_year_age}")
```

### Mixed Type Operations

```python
# Concatenating numbers with strings
score = 95
message = "Your score is: " + str(score)
print(message)  # Your score is: 95

# Or use f-strings (easier!)
print(f"Your score is: {score}")
```

### Calculating with Strings

```python
# Convert string numbers for calculation
price1 = "19.99"
price2 = "25.50"
total = float(price1) + float(price2)
print(f"Total: ${total}")  # Total: $45.49
```

## Type Conversion Chart

| From → To | Function | Example | Result |
|-----------|----------|---------|--------|
| str → int | `int()` | `int("42")` | `42` |
| str → float | `float()` | `float("3.14")` | `3.14` |
| int → str | `str()` | `str(42)` | `"42"` |
| float → str | `str()` | `str(3.14)` | `"3.14"` |
| float → int | `int()` | `int(3.14)` | `3` |
| int → float | `float()` | `float(42)` | `42.0` |
| any → bool | `bool()` | `bool(0)` | `False` |

## Common Pitfalls

```python
# Can't convert invalid strings
# int("hello")  # ValueError

# Can't convert floats with decimals directly to int from string
# int("3.14")  # ValueError
# Solution:
int(float("3.14"))  # 3

# Division always returns float in Python 3
result = 10 / 2
print(type(result))  # <class 'float'>
print(result)        # 5.0
```

