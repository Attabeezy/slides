# Advanced List Comprehension

## Nested Comprehensions

```python
# 2D matrix
matrix = [[i+j for j in range(3)] for i in range(3)]
# [[0,1,2], [1,2,3], [2,3,4]]

# Flatten list
nested = [[1,2], [3,4], [5,6]]
flat = [item for sublist in nested for item in sublist]
# [1, 2, 3, 4, 5, 6]
```

## Dict Comprehension

```python
# Create dictionary
squares = {x: x**2 for x in range(5)}
# {0:0, 1:1, 2:4, 3:9, 4:16}

# Swap keys and values
original = {'a': 1, 'b': 2}
swapped = {v: k for k, v in original.items()}
# {1: 'a', 2: 'b'}
```

## Set Comprehension

```python
# Unique squares
numbers = [1, -1, 2, -2, 3, -3]
squares = {x**2 for x in numbers}
# {1, 4, 9}
```
