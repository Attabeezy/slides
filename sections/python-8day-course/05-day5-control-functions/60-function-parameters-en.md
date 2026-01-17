# Function Parameters

## Positional Arguments

```python
def describe_pet(animal, name):
    print(f"I have a {animal} named {name}")

describe_pet("dog", "Buddy")  # Order matters
```

## Keyword Arguments

```python
def describe_pet(animal, name):
    print(f"I have a {animal} named {name}")

describe_pet(name="Buddy", animal="dog")  # Order doesn't matter
describe_pet(animal="cat", name="Whiskers")
```

## *args - Variable Positional Arguments

```python
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3))        # 6
print(sum_all(1, 2, 3, 4, 5))  # 15

def make_pizza(size, *toppings):
    print(f"Making {size}-inch pizza with:")
    for topping in toppings:
        print(f"  - {topping}")

make_pizza(12, "pepperoni", "mushrooms", "olives")
```

## **kwargs - Variable Keyword Arguments

```python
def build_profile(**info):
    return info

user = build_profile(name="Alice", age=25, city="Boston")
print(user)  # {'name': 'Alice', 'age': 25, 'city': 'Boston'}

def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Bob", age=30, occupation="Engineer")
```

## Combining All Parameter Types

```python
def function(pos, default="value", *args, **kwargs):
    print(f"Positional: {pos}")
    print(f"Default: {default}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

function(1, "custom", 2, 3, 4, a=5, b=6)
```
