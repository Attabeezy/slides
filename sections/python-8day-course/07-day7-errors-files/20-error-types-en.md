# Common Python Errors

## SyntaxError

```python
# Missing colon
# if x > 5
#     print(x)

# Incorrect indentation
# def hello():
# print("hi")
```

## NameError

```python
# Using undefined variable
# print(undefined_variable)  # NameError
```

## TypeError

```python
# Incompatible types
# result = "5" + 5  # TypeError

# Wrong number of arguments
# len(1, 2)  # TypeError
```

## ValueError

```python
# Invalid conversion
# int("abc")  # ValueError

# Wrong value
# int("12.5")  # ValueError (use float first)
```

## IndexError

```python
# Out of range
numbers = [1, 2, 3]
# print(numbers[5])  # IndexError
```

## KeyError

```python
# Missing key
person = {'name': 'Alice'}
# print(person['age'])  # KeyError
```

## ZeroDivisionError

```python
# Division by zero
# result = 10 / 0  # ZeroDivisionError
```

## FileNotFoundError

```python
# File doesn't exist
# file = open('nonexistent.txt')  # FileNotFoundError
```

## AttributeError

```python
# Method doesn't exist
text = "hello"
# text.nonexistent_method()  # AttributeError
```
