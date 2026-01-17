# Loop Control Statements

## break - Exit Loop

```python
# Stop when found
for i in range(10):
    if i == 5:
        break
    print(i)  # 0, 1, 2, 3, 4

# Search and exit
fruits = ['apple', 'banana', 'orange']
for fruit in fruits:
    if fruit == 'banana':
        print("Found banana!")
        break
```

## continue - Skip Iteration

```python
# Skip even numbers
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # 1, 3, 5, 7, 9

# Skip specific items
fruits = ['apple', 'banana', 'orange', 'grape']
for fruit in fruits:
    if fruit == 'banana':
        continue
    print(fruit)  # apple, orange, grape
```

## else with Loops

```python
# else executes if loop completes normally
for i in range(5):
    print(i)
else:
    print("Loop completed")

# else doesn't execute if break used
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("Won't print")
```

## pass - Placeholder

```python
# Empty loop (for future implementation)
for i in range(5):
    pass  # TODO: implement later

# Empty condition
if True:
    pass  # Do nothing
```

## Nested Loops

```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} x {j} = {i*j}")

# Break outer loop
for i in range(3):
    for j in range(3):
        if i == 1 and j == 1:
            break
        print(f"i={i}, j={j}")
```
