# Classes and Objects

## What is Object-Oriented Programming?

**Object-Oriented Programming (OOP)** is a programming paradigm based on the concept of "objects" that contain:

- **Data** (attributes/properties)
- **Code** (methods/functions)

OOP helps organize code in a way that models real-world entities.

## Why Use OOP?

- **Modularity**: Break complex programs into smaller, manageable pieces
- **Reusability**: Write code once, use it many times
- **Maintainability**: Easier to update and debug
- **Real-world modeling**: Code structure mirrors real-world objects

# Creating a Class

## Basic Class Syntax

```python
class Person:
    pass  # Empty class for now

# Create an object (instance) of the class
person1 = Person()
print(type(person1))  # <class '__main__.Person'>
```

## Class with Attributes

```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age

# Create instances
person1 = Person('Alice', 30)
person2 = Person('Bob', 25)

print(person1.name)  # Alice
print(person2.age)   # 25
```

# The `__init__` Method

## Constructor Method

The `__init__` method is a **constructor** - it's automatically called when creating a new object.

```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year
        self.odometer = 0  # Default value

car1 = Car('Toyota', 'Camry', 2020)
print(f"{car1.year} {car1.brand} {car1.model}")
# 2020 Toyota Camry
```

## The `self` Parameter

- `self` refers to the **current instance** of the class
- It's the first parameter of every instance method
- Used to access attributes and methods within the class
- Python passes it automatically (you don't include it when calling)

# Instance Methods

## Adding Behavior to Classes

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old"

    def have_birthday(self):
        self.age += 1
        return f"Happy birthday! Now {self.age} years old"

person = Person('Alice', 30)
print(person.introduce())      # Hi, I'm Alice and I'm 30 years old
print(person.have_birthday())  # Happy birthday! Now 31 years old
print(person.age)              # 31
```

# Class Attributes vs Instance Attributes

## Understanding the Difference

```python
class Dog:
    # Class attribute (shared by all instances)
    species = 'Canis familiaris'

    def __init__(self, name, breed):
        # Instance attributes (unique to each instance)
        self.name = name
        self.breed = breed

dog1 = Dog('Buddy', 'Golden Retriever')
dog2 = Dog('Max', 'German Shepherd')

print(dog1.species)  # Canis familiaris
print(dog2.species)  # Canis familiaris
print(dog1.name)     # Buddy
print(dog2.name)     # Max
```

## Modifying Class Attributes

```python
class Counter:
    count = 0  # Class attribute

    def __init__(self):
        Counter.count += 1  # Increment class attribute

c1 = Counter()
c2 = Counter()
c3 = Counter()

print(Counter.count)  # 3
```

# Real-World Example: Bank Account

## Complete Class Implementation

```python
class BankAccount:
    """A simple bank account class"""

    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
        self.transactions = []

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transactions.append(f"Deposit: +${amount}")
            return f"Deposited ${amount}. New balance: ${self.balance}"
        return "Invalid deposit amount"

    def withdraw(self, amount):
        if amount > 0:
            if amount <= self.balance:
                self.balance -= amount
                self.transactions.append(f"Withdrawal: -${amount}")
                return f"Withdrew ${amount}. New balance: ${self.balance}"
            return "Insufficient funds"
        return "Invalid withdrawal amount"

    def get_balance(self):
        return f"Current balance: ${self.balance}"

    def get_transaction_history(self):
        if not self.transactions:
            return "No transactions yet"
        return "\n".join(self.transactions)

# Usage
account = BankAccount('Alice', 1000)
print(account.deposit(500))        # Deposited $500. New balance: $1500
print(account.withdraw(200))       # Withdrew $200. New balance: $1300
print(account.get_balance())       # Current balance: $1300
print(account.get_transaction_history())
```

# String Representation: `__str__` and `__repr__`

## Making Objects Readable

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        # For print() - user-friendly
        return f"{self.name}, {self.age} years old"

    def __repr__(self):
        # For debugging - unambiguous
        return f"Person('{self.name}', {self.age})"

person = Person('Alice', 30)
print(person)          # Alice, 30 years old
print(repr(person))    # Person('Alice', 30)
print([person])        # [Person('Alice', 30)]
```

# Practical Example: Student Management

## Building a Student Class

```python
class Student:
    """Represents a student with grades"""

    # Class attribute
    school_name = 'Python Academy'

    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.grades = []

    def add_grade(self, grade):
        if 0 <= grade <= 100:
            self.grades.append(grade)
            return f"Added grade: {grade}"
        return "Invalid grade (must be 0-100)"

    def get_average(self):
        if not self.grades:
            return "No grades yet"
        return sum(self.grades) / len(self.grades)

    def get_letter_grade(self):
        avg = self.get_average()
        if avg == "No grades yet":
            return avg

        if avg >= 90:
            return 'A'
        elif avg >= 80:
            return 'B'
        elif avg >= 70:
            return 'C'
        elif avg >= 60:
            return 'D'
        else:
            return 'F'

    def __str__(self):
        avg = self.get_average()
        if avg == "No grades yet":
            return f"{self.name} (ID: {self.student_id}) - {avg}"
        return f"{self.name} (ID: {self.student_id}) - Average: {avg:.1f}"

# Usage
student = Student('Bob', 'S001')
student.add_grade(85)
student.add_grade(92)
student.add_grade(88)

print(student)                        # Bob (ID: S001) - Average: 88.3
print(f"Average: {student.get_average():.1f}")  # Average: 88.3
print(f"Grade: {student.get_letter_grade()}")   # Grade: B
```

# Private Attributes and Encapsulation

## Protecting Data

```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner
        self.__balance = balance  # Private attribute (name mangling)

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False

    def get_balance(self):
        return self.__balance

account = BankAccount('Alice', 1000)
print(account.get_balance())  # 1000

# This won't work (attribute is private)
# print(account.__balance)  # AttributeError

# Can still access (but shouldn't) via name mangling
print(account._BankAccount__balance)  # 1000 (not recommended)
```

## Naming Conventions

- `attribute`: Public attribute
- `_attribute`: Protected (convention - internal use)
- `__attribute`: Private (name mangling)

# Class Methods and Static Methods

## Different Method Types

```python
class Pizza:
    def __init__(self, ingredients):
        self.ingredients = ingredients

    # Instance method
    def __str__(self):
        return f"Pizza with {', '.join(self.ingredients)}"

    # Class method
    @classmethod
    def margherita(cls):
        return cls(['mozzarella', 'tomatoes', 'basil'])

    @classmethod
    def pepperoni(cls):
        return cls(['mozzarella', 'pepperoni'])

    # Static method
    @staticmethod
    def is_vegetarian(ingredients):
        meat = ['pepperoni', 'sausage', 'bacon', 'ham']
        return not any(item in meat for item in ingredients)

# Using class methods as factories
pizza1 = Pizza.margherita()
pizza2 = Pizza.pepperoni()

print(pizza1)  # Pizza with mozzarella, tomatoes, basil
print(Pizza.is_vegetarian(['tomatoes', 'basil']))  # True
print(Pizza.is_vegetarian(['pepperoni']))          # False
```

# Key Concepts Summary

## Classes and Objects

| Concept                | Description                    | Example               |
| ---------------------- | ------------------------------ | --------------------- |
| **Class**              | Blueprint for creating objects | `class Dog:`          |
| **Object**             | Instance of a class            | `dog = Dog()`         |
| **`__init__`**         | Constructor method             | `def __init__(self):` |
| **self**               | Reference to current instance  | `self.name = name`    |
| **Instance attribute** | Unique to each object          | `self.age = 25`       |
| **Class attribute**    | Shared by all objects          | `species = 'Dog'`     |
| **Method**             | Function defined in a class    | `def bark(self):`     |
| **Encapsulation**      | Hiding internal details        | `self.__balance`      |

## When to Use Classes

- When you have **data + behavior** together
- When you need **multiple instances** of similar things
- When you want to **organize complex code**
- When you need **state that persists** across function calls
