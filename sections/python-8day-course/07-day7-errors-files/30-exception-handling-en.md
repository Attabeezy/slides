# Exception Handling

## try-except

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    number = int(input("Enter number: "))
    result = 10 / number
except ValueError:
    print("Invalid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

## try-except-else

```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Error!")
else:
    print(f"Result: {result}")  # Runs if no error
```

## try-except-finally

```python
try:
    file = open('data.txt', 'r')
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("This always runs")
    # file.close()  # Close file if opened
```

## Catching All Exceptions

```python
try:
    # Some code
    pass
except Exception as e:
    print(f"An error occurred: {e}")
```

## Raising Exceptions

```python
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

try:
    divide(10, 0)
except ValueError as e:
    print(e)
```

## Custom Exceptions

```python
class NegativeNumberError(Exception):
    pass

def sqrt(x):
    if x < 0:
        raise NegativeNumberError("Cannot take sqrt of negative")
    return x ** 0.5
```
