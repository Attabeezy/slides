# Functions in Python

## Defining Functions

```python
def greet():
    print("Hello, World!")

greet()  # Call the function
```

## Functions with Parameters

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")  # Hello, Alice!
greet("Bob")    # Hello, Bob!

# Multiple parameters
def add(a, b):
    result = a + b
    print(f"{a} + {b} = {result}")

add(5, 3)  # 5 + 3 = 8
```

## Return Values

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # 8

# Multiple return values
def get_name():
    return "Alice", "Smith"

first, last = get_name()
print(first)  # Alice
```

## Default Parameters

```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()          # Hello, Guest!
greet("Alice")   # Hello, Alice!

# Multiple defaults
def power(base, exponent=2):
    return base ** exponent

print(power(5))      # 25 (5^2)
print(power(5, 3))   # 125 (5^3)
```

## Docstrings

```python
def add(a, b):
    """
    Add two numbers and return the result.
    
    Args:
        a: First number
        b: Second number
    
    Returns:
        Sum of a and b
    """
    return a + b

print(add.__doc__)  # Print documentation
```

# Lambda Functions

```python
# Regular function
def square(x):
    return x ** 2

# Lambda (anonymous) function
square = lambda x: x ** 2

print(square(5))  # 25

# Multiple parameters
add = lambda a, b: a + b
print(add(3, 4))  # 7

# Common use with map/filter
numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16, 25]
```
