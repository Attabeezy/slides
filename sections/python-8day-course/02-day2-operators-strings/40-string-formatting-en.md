# String Formatting

## Why String Formatting?

Combine strings with variables for dynamic output.

## Method 1: Old Style (% Operator)

Legacy method, still works but less preferred.

### Basic Syntax

```python
name = "Alice"
age = 25

# %s for strings
message = "Hello, %s!" % name
print(message)  # Hello, Alice!

# %d for integers
message = "I am %d years old" % age
print(message)  # I am 25 years old

# Multiple values (use tuple)
message = "My name is %s and I am %d years old" % (name, age)
print(message)  # My name is Alice and I am 25 years old
```

### Format Specifiers

| Specifier | Type | Example |
|-----------|------|---------|
| `%s` | String | `"Name: %s" % name` |
| `%d` | Integer | `"Age: %d" % 25` |
| `%f` | Float | `"Pi: %f" % 3.14` |
| `%.2f` | Float (2 decimals) | `"Price: %.2f" % 19.99` |

```python
# Float formatting
pi = 3.14159
print("Pi is approximately %f" % pi)      # Pi is approximately 3.141590
print("Pi is approximately %.2f" % pi)    # Pi is approximately 3.14

# Multiple values
radius = 5
area = 3.14 * radius ** 2
print("Circle with radius %d has area %.2f" % (radius, area))
# Circle with radius 5 has area 78.50
```

## Method 2: .format() Method

Introduced in Python 3, more flexible.

### Basic Usage

```python
name = "Bob"
age = 30

# Positional arguments
message = "Hello, {}!".format(name)
print(message)  # Hello, Bob!

# Multiple arguments
message = "My name is {} and I am {} years old".format(name, age)
print(message)  # My name is Bob and I am 30 years old
```

### Indexed Arguments

```python
# Use indices to specify order
message = "{1} is {0} years old".format(30, "Bob")
print(message)  # Bob is 30 years old

# Reuse arguments
message = "{0} loves {1}. {0} is learning {1}!".format("Alice", "Python")
print(message)  # Alice loves Python. Alice is learning Python!
```

### Named Arguments

```python
message = "Hello, {name}! You are {age} years old".format(name="Charlie", age=35)
print(message)  # Hello, Charlie! You are 35 years old

# Mix with positional
message = "{0}, your score is {score}".format("Dave", score=95)
print(message)  # Dave, your score is 95
```

### Formatting Numbers

```python
# Float precision
pi = 3.14159
print("Pi: {:.2f}".format(pi))        # Pi: 3.14
print("Pi: {:.4f}".format(pi))        # Pi: 3.1416

# Padding and alignment
print("{:10}".format("Python"))       # 'Python    ' (left-aligned, width 10)
print("{:>10}".format("Python"))      # '    Python' (right-aligned)
print("{:^10}".format("Python"))      # '  Python  ' (centered)
print("{:*^10}".format("Hi"))         # '****Hi****' (centered with padding)

# Number formatting
print("{:,}".format(1000000))         # 1,000,000 (thousands separator)
```

## Method 3: f-Strings (Recommended)

Introduced in Python 3.6, most readable and efficient.

### Basic Syntax

Prefix string with `f` or `F` and use `{variable}` syntax:

```python
name = "Emma"
age = 28
city = "New York"

# Simple f-string
message = f"Hello, {name}!"
print(message)  # Hello, Emma!

# Multiple variables
message = f"My name is {name}, I am {age} years old, and I live in {city}"
print(message)  # My name is Emma, I am 28 years old, and I live in New York
```

### Expressions Inside f-Strings

```python
a = 10
b = 5

# Arithmetic expressions
print(f"{a} + {b} = {a + b}")         # 10 + 5 = 15
print(f"{a} * {b} = {a * b}")         # 10 * 5 = 50
print(f"{a} / {b} = {a / b}")         # 10 / 5 = 2.0

# Function calls
name = "python"
print(f"Uppercase: {name.upper()}")   # Uppercase: PYTHON
print(f"Length: {len(name)}")         # Length: 6

# Conditional expressions
score = 85
print(f"Result: {'Pass' if score >= 60 else 'Fail'}")  # Result: Pass
```

### Formatting with f-Strings

```python
# Float precision
pi = 3.14159
print(f"Pi: {pi:.2f}")                # Pi: 3.14
print(f"Pi: {pi:.4f}")                # Pi: 3.1416

# Padding and alignment
name = "Python"
print(f"{name:10}")                   # 'Python    '
print(f"{name:>10}")                  # '    Python'
print(f"{name:^10}")                  # '  Python  '

# Number formatting
number = 1000000
print(f"{number:,}")                  # 1,000,000
```

### Multi-Line f-Strings

```python
name = "Alice"
age = 25
city = "Boston"

message = f"""
Name: {name}
Age: {age}
City: {city}
Next year you'll be {age + 1}
"""
print(message)
```

## Comparison

```python
name = "John"
age = 30
score = 95.678

# Old style
print("Name: %s, Age: %d, Score: %.2f" % (name, age, score))

# .format()
print("Name: {}, Age: {}, Score: {:.2f}".format(name, age, score))

# f-string (RECOMMENDED)
print(f"Name: {name}, Age: {age}, Score: {score:.2f}")

# All produce: Name: John, Age: 30, Score: 95.68
```

## Practical Examples

```python
# Invoice
item = "Book"
quantity = 3
price = 15.99
total = quantity * price

print(f"""
{'='*30}
         INVOICE
{'='*30}
Item:     {item}
Quantity: {quantity}
Price:    ${price:.2f}
{'='*30}
Total:    ${total:.2f}
{'='*30}
""")

# Progress bar
progress = 75
bar_length = 20
filled = int(progress / 100 * bar_length)
bar = '█' * filled + '-' * (bar_length - filled)
print(f"Progress: [{bar}] {progress}%")
```

