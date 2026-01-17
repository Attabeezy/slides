# Sets in Python

## What are Sets?

Sets are **unordered**, **mutable** collections of **unique** items.

**Key characteristics:**
- No duplicate items
- Unordered (no indexing)
- Mutable (can add/remove items)
- Fast membership testing

## Creating Sets

```python
# Using curly braces
fruits = {'apple', 'banana', 'orange'}

# Using set() constructor
numbers = set([1, 2, 3, 4, 5])

# Empty set (must use set())
empty_set = set()  # NOT {} which creates dict
```

## Removing Duplicates

```python
numbers = [1, 2, 2, 3, 3, 3, 4, 5]
unique = set(numbers)
print(unique)  # {1, 2, 3, 4, 5}
```

## Set Operations

### Union (|)

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 | set2)  # {1, 2, 3, 4, 5}
```

### Intersection (&)

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
print(set1 & set2)  # {2, 3}
```

### Difference (-)

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
print(set1 - set2)  # {1}
```

### Symmetric Difference (^)

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
print(set1 ^ set2)  # {1, 4}
```

## Set Methods

```python
fruits = {'apple', 'banana'}

# Add item
fruits.add('orange')

# Remove item (error if not found)
fruits.remove('banana')

# Remove item (no error)
fruits.discard('grape')

# Remove and return random item
item = fruits.pop()
```
