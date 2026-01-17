# Python Modules

## What are Modules?

Modules are Python files containing functions, classes, and variables that can be imported and reused.

## Creating a Module

**my_module.py:**
```python
def greet(name):
    return f"Hello, {name}!"

PI = 3.14159

def circle_area(radius):
    return PI * radius ** 2
```

## Importing Modules

```python
# Import entire module
import my_module
print(my_module.greet("Alice"))
print(my_module.circle_area(5))

# Import specific items
from my_module import greet, PI
print(greet("Bob"))
print(PI)

# Import with alias
import my_module as mm
print(mm.greet("Charlie"))

# Import all (not recommended)
from my_module import *
```

## Module Search Path

```python
import sys
print(sys.path)  # List of directories Python searches
```
