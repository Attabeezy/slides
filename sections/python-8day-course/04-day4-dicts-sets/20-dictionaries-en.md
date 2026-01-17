# Dictionaries in Python

## What are Dictionaries?

Dictionaries are **unordered** (ordered in Python 3.7+), **mutable** collections that store data as **key-value pairs**.

**Key characteristics:**
- Key-value pairs
- Keys must be unique and immutable (strings, numbers, tuples)
- Values can be any type
- Mutable (can be changed)
- Fast lookup by key

## Creating Dictionaries

### Empty Dictionaries

```python
# Method 1: Curly braces
empty_dict = {}

# Method 2: dict() constructor
empty_dict = dict()

print(len(empty_dict))  # 0
```

### Dictionaries with Initial Values

```python
# Simple dictionary
person = {
    'name': 'Alice',
    'age': 25,
    'city': 'Boston'
}

# Mixed value types
mixed = {
    'name': 'Bob',
    'age': 30,
    'scores': [85, 90, 78],
    'is_student': False
}

# Using dict() constructor
person2 = dict(name='Charlie', age=35, city='Seattle')
```

## Accessing Values

### Using Keys

```python
person = {'name': 'Alice', 'age': 25, 'city': 'Boston'}

# Access with bracket notation
print(person['name'])    # 'Alice'
print(person['age'])     # 25

# KeyError if key doesn't exist
# print(person['email'])  # KeyError!
```

### Using get() Method

```python
person = {'name': 'Alice', 'age': 25}

# Safely get values
print(person.get('name'))    # 'Alice'
print(person.get('email'))   # None (no error)

# With default value
print(person.get('email', 'not provided'))  # 'not provided'
```

## Modifying Dictionaries

### Adding/Updating Items

```python
person = {'name': 'Alice', 'age': 25}

# Add new key-value
person['city'] = 'Boston'
print(person)  # {'name': 'Alice', 'age': 25, 'city': 'Boston'}

# Update existing value
person['age'] = 26
print(person)  # {'name': 'Alice', 'age': 26, 'city': 'Boston'}
```

### Removing Items

```python
person = {'name': 'Alice', 'age': 25, 'city': 'Boston'}

# Remove and return value
age = person.pop('age')
print(age)      # 25
print(person)   # {'name': 'Alice', 'city': 'Boston'}

# Remove last inserted item (Python 3.7+)
last = person.popitem()
print(last)     # ('city', 'Boston')

# Delete by key
del person['name']
```

## Dictionary Methods

```python
person = {'name': 'Alice', 'age': 25, 'city': 'Boston'}

# Get all keys
print(person.keys())    # dict_keys(['name', 'age', 'city'])

# Get all values
print(person.values())  # dict_values(['Alice', 25, 'Boston'])

# Get all items (key-value pairs)
print(person.items())   # dict_items([('name', 'Alice'), ('age', 25), ('city', 'Boston')])

# Clear all items
person.clear()
print(person)  # {}
```

## Checking Membership

```python
person = {'name': 'Alice', 'age': 25}

# Check if key exists
print('name' in person)     # True
print('email' in person)    # False

# Check values (slower)
print('Alice' in person.values())  # True
```

## Looping Through Dictionaries

```python
person = {'name': 'Alice', 'age': 25, 'city': 'Boston'}

# Loop through keys
for key in person:
    print(key)

# Loop through values
for value in person.values():
    print(value)

# Loop through key-value pairs
for key, value in person.items():
    print(f"{key}: {value}")
```

## Nested Dictionaries

```python
employees = {
    'emp1': {'name': 'Alice', 'age': 25},
    'emp2': {'name': 'Bob', 'age': 30},
    'emp3': {'name': 'Charlie', 'age': 35}
}

# Access nested values
print(employees['emp1']['name'])  # 'Alice'
print(employees['emp2']['age'])   # 30
```

## Dictionary Comprehension

```python
# Create dictionary from range
squares = {x: x**2 for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# From lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
result = {k: v for k, v in zip(keys, values)}
print(result)  # {'a': 1, 'b': 2, 'c': 3}
```
