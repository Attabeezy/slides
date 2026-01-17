# List Methods

## Adding Items

### append() - Add Single Item to End

```python
fruits = ['apple', 'banana']
fruits.append('orange')
print(fruits)  # ['apple', 'banana', 'orange']

# Append any data type
numbers = [1, 2, 3]
numbers.append(4)
numbers.append([5, 6])  # Adds list as single item
print(numbers)  # [1, 2, 3, 4, [5, 6]]
```

### insert() - Add Item at Specific Position

```python
fruits = ['apple', 'orange']
fruits.insert(1, 'banana')  # Insert at index 1
print(fruits)  # ['apple', 'banana', 'orange']

# Insert at beginning
fruits.insert(0, 'grape')
print(fruits)  # ['grape', 'apple', 'banana', 'orange']
```

### extend() - Add Multiple Items

```python
fruits = ['apple', 'banana']
more_fruits = ['orange', 'grape']

fruits.extend(more_fruits)
print(fruits)  # ['apple', 'banana', 'orange', 'grape']

# Extend with any iterable
fruits.extend(['kiwi', 'mango'])
fruits.extend('XY')  # Adds 'X' and 'Y' separately
print(fruits)  # [..., 'kiwi', 'mango', 'X', 'Y']
```

## Removing Items

### remove() - Remove First Occurrence of Value

```python
fruits = ['apple', 'banana', 'orange', 'banana']
fruits.remove('banana')  # Removes first 'banana'
print(fruits)  # ['apple', 'orange', 'banana']

# Raises ValueError if not found
# fruits.remove('grape')  # ValueError!
```

### pop() - Remove and Return Item by Index

```python
fruits = ['apple', 'banana', 'orange']

# Remove last item (default)
last = fruits.pop()
print(last)    # 'orange'
print(fruits)  # ['apple', 'banana']

# Remove by index
first = fruits.pop(0)
print(first)   # 'apple'
print(fruits)  # ['banana']
```

### del - Delete Items by Index or Slice

```python
fruits = ['apple', 'banana', 'orange', 'grape']

# Delete single item
del fruits[1]
print(fruits)  # ['apple', 'orange', 'grape']

# Delete slice
fruits = ['apple', 'banana', 'orange', 'grape', 'kiwi']
del fruits[1:3]
print(fruits)  # ['apple', 'grape', 'kiwi']

# Delete entire list
del fruits
# print(fruits)  # NameError: fruits not defined
```

### clear() - Remove All Items

```python
fruits = ['apple', 'banana', 'orange']
fruits.clear()
print(fruits)  # []
print(len(fruits))  # 0
```

## Organizing Lists

### sort() - Sort List In-Place

```python
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# Reverse sort
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]

# Sort strings
fruits = ['banana', 'apple', 'orange']
fruits.sort()
print(fruits)  # ['apple', 'banana', 'orange']
```

### sorted() - Return New Sorted List

```python
numbers = [3, 1, 4, 1, 5]
sorted_numbers = sorted(numbers)
print(numbers)         # [3, 1, 4, 1, 5] (unchanged)
print(sorted_numbers)  # [1, 1, 3, 4, 5]
```

### reverse() - Reverse List In-Place

```python
fruits = ['apple', 'banana', 'orange']
fruits.reverse()
print(fruits)  # ['orange', 'banana', 'apple']

# Using slicing (creates new list)
fruits = ['apple', 'banana', 'orange']
reversed_fruits = fruits[::-1]
print(reversed_fruits)  # ['orange', 'banana', 'apple']
```

## Copying Lists

### Shallow Copy Methods

```python
original = [1, 2, 3, 4, 5]

# Method 1: copy()
copy1 = original.copy()

# Method 2: list() constructor
copy2 = list(original)

# Method 3: slicing
copy3 = original[:]

# All create independent copies
copy1[0] = 999
print(original)  # [1, 2, 3, 4, 5] (unchanged)
print(copy1)     # [999, 2, 3, 4, 5]
```

### Assignment vs Copy

```python
# Assignment doesn't copy!
original = [1, 2, 3]
reference = original  # Both point to same list

reference[0] = 999
print(original)    # [999, 2, 3] (changed!)
print(reference)   # [999, 2, 3]

# Use copy() for independent list
original = [1, 2, 3]
true_copy = original.copy()
true_copy[0] = 999
print(original)    # [1, 2, 3] (unchanged)
print(true_copy)   # [999, 2, 3]
```

## Finding Items

### index() - Find First Index of Value

```python
fruits = ['apple', 'banana', 'orange', 'banana']

print(fruits.index('banana'))  # 1 (first occurrence)
print(fruits.index('orange'))  # 2

# Specify start position
print(fruits.index('banana', 2))  # 3 (search from index 2)

# Raises ValueError if not found
# print(fruits.index('grape'))  # ValueError!
```

### count() - Count Occurrences

```python
numbers = [1, 2, 3, 2, 4, 2, 5]
print(numbers.count(2))  # 3
print(numbers.count(9))  # 0

fruits = ['apple', 'banana', 'apple']
print(fruits.count('apple'))  # 2
```

## List Methods Summary

| Method | Description | Example |
|--------|-------------|---------|
| `append(x)` | Add item to end | `list.append(5)` |
| `insert(i, x)` | Insert at index | `list.insert(0, 'first')` |
| `extend(iter)` | Add multiple items | `list.extend([1, 2, 3])` |
| `remove(x)` | Remove first occurrence | `list.remove('apple')` |
| `pop(i)` | Remove & return by index | `list.pop()` or `list.pop(0)` |
| `clear()` | Remove all items | `list.clear()` |
| `index(x)` | Find first index | `list.index('banana')` |
| `count(x)` | Count occurrences | `list.count(5)` |
| `sort()` | Sort in-place | `list.sort()` |
| `reverse()` | Reverse in-place | `list.reverse()` |
| `copy()` | Shallow copy | `new_list = list.copy()` |

