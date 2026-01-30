# Loops in Python

## While Loop

```python
# Basic while loop
count = 0
while count < 5:
    print(count)
    count += 1

# User input until valid
while True:
    answer = input("Enter 'quit' to exit: ")
    if answer == 'quit':
        break
```

## For Loop

```python
# Loop through range
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# Loop through list
fruits = ['apple', 'banana', 'orange']
for fruit in fruits:
    print(fruit)

# Loop through string
for char in "Python":
    print(char)

# Loop through dictionary
person = {'name': 'Alice', 'age': 25}
for key, value in person.items():
    print(f"{key}: {value}")
```

## Range Function

```python
# range(stop)
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# range(start, stop)
for i in range(2, 6):
    print(i)  # 2, 3, 4, 5

# range(start, stop, step)
for i in range(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8

# Reverse range
for i in range(5, 0, -1):
    print(i)  # 5, 4, 3, 2, 1
```

# Enumerate and Zip

```python
fruits = ['apple', 'banana', 'orange']

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
# 0: apple
# 1: banana
# 2: orange

# Start index from 1
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}: {fruit}")
```

## Zip

```python
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]

for name, age in zip(names, ages):
    print(f"{name} is {age} years old")
```
