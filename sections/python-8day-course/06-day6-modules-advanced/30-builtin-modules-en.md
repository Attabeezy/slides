# Built-in Modules

## math Module

```python
import math

print(math.pi)          # 3.141592653589793
print(math.sqrt(16))    # 4.0
print(math.ceil(4.2))   # 5
print(math.floor(4.8))  # 4
print(math.pow(2, 3))   # 8.0
```

## random Module

```python
import random

print(random.random())           # Random float 0.0-1.0
print(random.randint(1, 10))     # Random int 1-10
print(random.choice([1,2,3,4]))  # Random item

# Shuffle list
items = [1, 2, 3, 4, 5]
random.shuffle(items)
print(items)
```

## datetime Module

```python
from datetime import datetime, date, timedelta

# Current date and time
now = datetime.now()
print(now)

# Create specific date
birthday = date(1990, 5, 15)

# Date arithmetic
tomorrow = date.today() + timedelta(days=1)
```

## os Module

```python
import os

print(os.getcwd())        # Current directory
print(os.listdir('.'))    # List files
# os.mkdir('new_folder')  # Create directory
# os.rename('old', 'new') # Rename file
```
