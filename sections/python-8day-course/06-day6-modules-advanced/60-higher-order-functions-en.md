# Higher-Order Functions

## map() - Transform Items

```python
# Double each number
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x*2, numbers))
# [2, 4, 6, 8, 10]

# Multiple iterables
list1 = [1, 2, 3]
list2 = [10, 20, 30]
sums = list(map(lambda x, y: x+y, list1, list2))
# [11, 22, 33]
```

## filter() - Filter Items

```python
# Filter even numbers
numbers = [1, 2, 3, 4, 5, 6]
evens = list(filter(lambda x: x%2==0, numbers))
# [2, 4, 6]

# Filter by length
words = ['hi', 'hello', 'world', 'python']
long_words = list(filter(lambda w: len(w)>4, words))
# ['hello', 'world', 'python']
```

## reduce() - Aggregate Values

```python
from functools import reduce

# Sum all numbers
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x+y, numbers)
# 15

# Find maximum
maximum = reduce(lambda x, y: x if x>y else y, numbers)
# 5
```

## Functions as Arguments

```python
def apply_operation(numbers, operation):
    return [operation(n) for n in numbers]

numbers = [1, 2, 3, 4, 5]
squares = apply_operation(numbers, lambda x: x**2)
cubes = apply_operation(numbers, lambda x: x**3)
```
