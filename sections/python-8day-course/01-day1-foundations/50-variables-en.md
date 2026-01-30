# Variables in Python

## What are Variables?

Variables store data in computer memory. Think of them as labeled containers that hold values.

```python
name = "Alice"
age = 25
height = 1.68
```

## Variable Naming Rules

### Valid Names

- Must start with a letter (a-z, A-Z) or underscore (_)
- Can contain letters, digits (0-9), and underscores
- Case-sensitive (`age` and `Age` are different)

```python
firstname = "John"
last_name = "Doe"
age2 = 30
_private = "hidden"
CONSTANT = 3.14
```

### Invalid Names

```python
# 2fast = 100        # Cannot start with number
# first-name = "Jo"  # Cannot use hyphens
# first name = "Jo"  # Cannot use spaces
# for = 5            # Cannot use reserved keywords
```

# Naming Conventions

### Snake Case (Recommended)

Use lowercase with underscores for variables and functions:

```python
first_name = "Alice"
total_price = 99.99
user_age = 25
```

### Other Conventions

```python
# UPPERCASE for constants
MAX_SIZE = 100
PI = 3.14159

# PascalCase for classes (you'll learn this later)
MyClass = "example"
```

# Assigning Values

### Single Assignment

```python
x = 5
name = "Python"
is_valid = True
```

### Multiple Assignment

```python
# Assign same value to multiple variables
x = y = z = 0

# Assign different values
a, b, c = 1, 2, 3
name, age = "Alice", 25
```

### Swapping Variables

```python
x = 10
y = 20
x, y = y, x  # Swap values
print(x)  # 20
print(y)  # 10
```

## Variable Examples

```python
# Personal information
first_name = "John"
last_name = "Doe"
age = 30
country = "USA"
city = "New York"
is_married = True

# Numeric calculations
width = 10
height = 20
area = width * height

# Collections (you'll learn more about these later)
fruits = ['apple', 'banana', 'orange']
person = {'name': 'Alice', 'age': 25}
```

## Best Practices

1. **Use descriptive names:** `user_age` instead of `ua`
2. **Be consistent:** Stick to snake_case
3. **Avoid reserved words:** Don't use `list`, `str`, `int`, etc.
4. **Make names meaningful:** `total_price` instead of `tp`

