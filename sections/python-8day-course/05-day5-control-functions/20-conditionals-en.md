# Conditional Statements

## if Statement

```python
age = 18
if age >= 18:
    print("You are an adult")
```

## if-else Statement

```python
age = 16
if age >= 18:
    print("You are an adult")
else:
    print("You are a minor")
```

## if-elif-else Statement

```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: F")
```

## Nested Conditions

```python
age = 20
has_license = True

if age >= 18:
    if has_license:
        print("You can drive")
    else:
        print("You need a license")
else:
    print("You are too young")
```

## Short-hand (Ternary) Operator

```python
age = 20
status = "adult" if age >= 18 else "minor"
print(status)  # "adult"

# Nested ternary
score = 85
grade = "A" if score >= 90 else "B" if score >= 80 else "C"
```

## Comparison Operators in Conditions

```python
x = 10

# Multiple conditions
if x > 0 and x < 20:
    print("x is between 0 and 20")

# Using or
if x < 0 or x > 100:
    print("x is out of range")

# Using not
if not (x < 0):
    print("x is positive or zero")
```

## Truthy and Falsy Values

```python
# Falsy values: False, None, 0, "", [], {}, ()
if []:
    print("Won't print")  # Empty list is falsy

if [1, 2, 3]:
    print("Will print")  # Non-empty list is truthy
```
