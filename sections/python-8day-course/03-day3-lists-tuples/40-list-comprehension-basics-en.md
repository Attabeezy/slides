# List Comprehension Basics

## What is List Comprehension?

A concise way to create lists using a single line of code.

**Syntax:**
```python
new_list = [expression for item in iterable]
```

## Traditional vs List Comprehension

### Creating Lists Traditionally

```python
# Traditional approach
numbers = []
for i in range(5):
    numbers.append(i)
print(numbers)  # [0, 1, 2, 3, 4]

# Using list comprehension
numbers = [i for i in range(5)]
print(numbers)  # [0, 1, 2, 3, 4]
```

## Basic List Comprehensions

### From Range

```python
# Squares of numbers
squares = [x**2 for x in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Even numbers
evens = [x for x in range(20) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

### From Existing List

```python
# Convert to uppercase
fruits = ['apple', 'banana', 'orange']
upper_fruits = [fruit.upper() for fruit in fruits]
print(upper_fruits)  # ['APPLE', 'BANANA', 'ORANGE']

# Get lengths
names = ['Alice', 'Bob', 'Charlie']
lengths = [len(name) for name in names]
print(lengths)  # [5, 3, 7]
```

# List Comprehension with Conditions

### If Condition

```python
# Only positive numbers
numbers = [-2, -1, 0, 1, 2, 3]
positives = [x for x in numbers if x > 0]
print(positives)  # [1, 2, 3]

# Words longer than 5 characters
words = ['hi', 'hello', 'world', 'python', 'code']
long_words = [word for word in words if len(word) > 5]
print(long_words)  # ['python']
```

### If-Else (Conditional Expression)

```python
# Convert negatives to 0
numbers = [-2, -1, 0, 1, 2]
result = [x if x > 0 else 0 for x in numbers]
print(result)  # [0, 0, 0, 1, 2]

# Even or odd labels
numbers = [1, 2, 3, 4, 5]
labels = ['even' if x % 2 == 0 else 'odd' for x in numbers]
print(labels)  # ['odd', 'even', 'odd', 'even', 'odd']
```

## Transforming Data

```python
# Multiply each by 10
numbers = [1, 2, 3, 4, 5]
multiplied = [x * 10 for x in numbers]
print(multiplied)  # [10, 20, 30, 40, 50]

# Convert strings to integers
string_numbers = ['1', '2', '3', '4']
int_numbers = [int(x) for x in string_numbers]
print(int_numbers)  # [1, 2, 3, 4]

# Extract first character
words = ['apple', 'banana', 'orange']
first_letters = [word[0] for word in words]
print(first_letters)  # ['a', 'b', 'o']
```

# Nested Loops and Practical Comprehensions

```python
# Cartesian product
colors = ['red', 'blue']
sizes = ['S', 'M', 'L']
combinations = [(color, size) for color in colors for size in sizes]
print(combinations)
# [('red', 'S'), ('red', 'M'), ('red', 'L'), 
#  ('blue', 'S'), ('blue', 'M'), ('blue', 'L')]

# Flatten matrix
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
print(flattened)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Practical Examples

### Filter and Transform

```python
# Get squares of even numbers only
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_squares = [x**2 for x in numbers if x % 2 == 0]
print(even_squares)  # [4, 16, 36, 64, 100]
```

### String Manipulation

```python
# Remove vowels
sentence = "Hello World"
no_vowels = [char for char in sentence if char.lower() not in 'aeiou']
result = ''.join(no_vowels)
print(result)  # 'Hll Wrld'
```

### Working with Multiple Lists

```python
# Pair elements from two lists
names = ['Alice', 'Bob', 'Charlie']
scores = [85, 90, 78]
pairs = [(name, score) for name, score in zip(names, scores)]
print(pairs)  # [('Alice', 85), ('Bob', 90), ('Charlie', 78)]
```

## Comparison: Traditional vs Comprehension

```python
# Traditional approach (more lines)
squares = []
for x in range(10):
    if x % 2 == 0:
        squares.append(x**2)

# List comprehension (one line)
squares = [x**2 for x in range(10) if x % 2 == 0]

# Both produce: [0, 4, 16, 36, 64]
```

## When to Use List Comprehension

**Use list comprehension when:**
- Creating simple lists with transformation
- Filtering items based on condition
- Code remains readable

**Use traditional loops when:**
- Logic is complex
- Multiple operations needed
- Readability would suffer

**Good:**
```python
squares = [x**2 for x in range(10)]
```

**Too complex (use traditional loop):**
```python
# Hard to read
result = [x**2 if x % 2 == 0 else x**3 if x % 3 == 0 else x for x in range(20) if x > 5]
```

