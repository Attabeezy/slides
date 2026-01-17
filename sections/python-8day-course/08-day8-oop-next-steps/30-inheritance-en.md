# Inheritance

## What is Inheritance?

**Inheritance** allows a class to inherit attributes and methods from another class:

- **Parent class** (superclass, base class): The class being inherited from
- **Child class** (subclass, derived class): The class that inherits

Benefits:

- Code reusability
- Logical hierarchy
- Easier maintenance

## Basic Inheritance Syntax

```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return "Some sound"

# Child class
class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

dog = Dog('Buddy')
cat = Cat('Whiskers')

print(dog.name)    # Buddy (inherited from Animal)
print(dog.speak()) # Woof! (overridden in Dog)
print(cat.speak()) # Meow! (overridden in Cat)
```

# The `super()` Function

## Extending Parent Functionality

```python
class Vehicle:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def info(self):
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    def __init__(self, brand, model, doors):
        super().__init__(brand, model)  # Call parent constructor
        self.doors = doors

    def info(self):
        parent_info = super().info()  # Call parent method
        return f"{parent_info} with {self.doors} doors"

car = Car('Toyota', 'Camry', 4)
print(car.info())  # Toyota Camry with 4 doors
```

## Why Use `super()`?

- Maintains the inheritance chain
- Avoids hardcoding parent class name
- Essential for multiple inheritance
- Makes code more maintainable

# Method Overriding

## Replacing Parent Methods

```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def get_details(self):
        return f"Employee: {self.name}, Salary: ${self.salary}"

    def calculate_bonus(self):
        return self.salary * 0.05  # 5% bonus

class Manager(Employee):
    def __init__(self, name, salary, department):
        super().__init__(name, salary)
        self.department = department

    # Override method
    def get_details(self):
        return f"Manager: {self.name}, Department: {self.department}, Salary: ${self.salary}"

    # Override method with different logic
    def calculate_bonus(self):
        return self.salary * 0.15  # 15% bonus for managers

employee = Employee('Alice', 50000)
manager = Manager('Bob', 80000, 'IT')

print(employee.get_details())          # Employee: Alice, Salary: $50000
print(employee.calculate_bonus())      # 2500.0

print(manager.get_details())           # Manager: Bob, Department: IT, Salary: $80000
print(manager.calculate_bonus())       # 12000.0
```

# Real-World Example: Shape Hierarchy

## Building a Shape System

```python
class Shape:
    """Base class for all shapes"""

    def __init__(self, color):
        self.color = color

    def area(self):
        raise NotImplementedError("Subclass must implement area()")

    def perimeter(self):
        raise NotImplementedError("Subclass must implement perimeter()")

    def describe(self):
        return f"A {self.color} {self.__class__.__name__}"

class Rectangle(Shape):
    def __init__(self, color, width, height):
        super().__init__(color)
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    def __init__(self, color, radius):
        super().__init__(color)
        self.radius = radius

    def area(self):
        import math
        return math.pi * self.radius ** 2

    def perimeter(self):
        import math
        return 2 * math.pi * self.radius

class Square(Rectangle):
    def __init__(self, color, side):
        super().__init__(color, side, side)

    def __str__(self):
        return f"{self.describe()} with side {self.width}"

# Usage
shapes = [
    Rectangle('red', 5, 3),
    Circle('blue', 4),
    Square('green', 6)
]

for shape in shapes:
    print(f"{shape.describe()}")
    print(f"  Area: {shape.area():.2f}")
    print(f"  Perimeter: {shape.perimeter():.2f}")
```

# Multiple Inheritance

## Inheriting from Multiple Classes

```python
class Flyer:
    def fly(self):
        return "Flying through the air"

class Swimmer:
    def swim(self):
        return "Swimming through water"

class Duck(Flyer, Swimmer):
    def __init__(self, name):
        self.name = name

    def quack(self):
        return "Quack!"

duck = Duck('Donald')
print(duck.fly())    # Flying through the air
print(duck.swim())   # Swimming through water
print(duck.quack())  # Quack!
```

## Method Resolution Order (MRO)

```python
class A:
    def method(self):
        return "A"

class B(A):
    def method(self):
        return "B"

class C(A):
    def method(self):
        return "C"

class D(B, C):
    pass

d = D()
print(d.method())  # B (follows MRO: D -> B -> C -> A)
print(D.mro())     # Shows the method resolution order
```

# Practical Example: E-commerce System

## Building a Product Hierarchy

```python
class Product:
    """Base class for all products"""

    def __init__(self, name, price):
        self.name = name
        self.price = price

    def get_details(self):
        return f"{self.name}: ${self.price}"

    def calculate_discount(self, percentage):
        return self.price * (1 - percentage / 100)

class Book(Product):
    def __init__(self, name, price, author, pages):
        super().__init__(name, price)
        self.author = author
        self.pages = pages

    def get_details(self):
        base = super().get_details()
        return f"{base} by {self.author} ({self.pages} pages)"

class Electronics(Product):
    def __init__(self, name, price, warranty_years):
        super().__init__(name, price)
        self.warranty_years = warranty_years

    def get_details(self):
        base = super().get_details()
        return f"{base} - {self.warranty_years} year warranty"

    def extend_warranty(self, years):
        self.warranty_years += years
        return f"Warranty extended to {self.warranty_years} years"

class Laptop(Electronics):
    def __init__(self, name, price, warranty_years, ram_gb, storage_gb):
        super().__init__(name, price, warranty_years)
        self.ram_gb = ram_gb
        self.storage_gb = storage_gb

    def get_details(self):
        base = super().get_details()
        return f"{base}\n  Specs: {self.ram_gb}GB RAM, {self.storage_gb}GB Storage"

# Usage
products = [
    Book('Python Crash Course', 39.99, 'Eric Matthes', 544),
    Electronics('Smart Watch', 299.99, 2),
    Laptop('Dell XPS 13', 1299.99, 1, 16, 512)
]

for product in products:
    print(product.get_details())
    print(f"  20% off: ${product.calculate_discount(20):.2f}")
    print()
```

# Checking Inheritance

## `isinstance()` and `issubclass()`

```python
class Animal:
    pass

class Dog(Animal):
    pass

class Cat(Animal):
    pass

dog = Dog()
cat = Cat()

# isinstance() - check if object is instance of class
print(isinstance(dog, Dog))      # True
print(isinstance(dog, Animal))   # True (Dog inherits from Animal)
print(isinstance(dog, Cat))      # False

# issubclass() - check if class is subclass of another
print(issubclass(Dog, Animal))   # True
print(issubclass(Cat, Animal))   # True
print(issubclass(Dog, Cat))      # False
```

# Polymorphism

## Same Interface, Different Behavior

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

class Cow(Animal):
    def speak(self):
        return "Moo!"

# Polymorphism in action
def animal_sound(animal):
    print(animal.speak())

animals = [Dog(), Cat(), Cow()]

for animal in animals:
    animal_sound(animal)
# Output:
# Woof!
# Meow!
# Moo!
```

# Abstract Base Classes

## Enforcing Method Implementation

```python
from abc import ABC, abstractmethod

class PaymentMethod(ABC):
    """Abstract base class for payment methods"""

    @abstractmethod
    def process_payment(self, amount):
        """Must be implemented by subclasses"""
        pass

    @abstractmethod
    def refund(self, amount):
        """Must be implemented by subclasses"""
        pass

class CreditCard(PaymentMethod):
    def __init__(self, card_number):
        self.card_number = card_number

    def process_payment(self, amount):
        return f"Processing ${amount} via Credit Card ending in {self.card_number[-4:]}"

    def refund(self, amount):
        return f"Refunding ${amount} to Credit Card"

class PayPal(PaymentMethod):
    def __init__(self, email):
        self.email = email

    def process_payment(self, amount):
        return f"Processing ${amount} via PayPal ({self.email})"

    def refund(self, amount):
        return f"Refunding ${amount} to PayPal account"

# This won't work - can't instantiate abstract class
# payment = PaymentMethod()  # TypeError

# These work
cc = CreditCard('1234567812345678')
pp = PayPal('user@example.com')

print(cc.process_payment(100))  # Processing $100 via Credit Card ending in 5678
print(pp.process_payment(50))   # Processing $50 via PayPal (user@example.com)
```

# Composition vs Inheritance

## "Has-a" vs "Is-a" Relationships

```python
# Inheritance (Is-a): Car IS-A Vehicle
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

class Car(Vehicle):
    pass

# Composition (Has-a): Car HAS-AN Engine
class Engine:
    def __init__(self, horsepower):
        self.horsepower = horsepower

    def start(self):
        return "Engine started"

class Car:
    def __init__(self, brand, horsepower):
        self.brand = brand
        self.engine = Engine(horsepower)  # Composition

    def start(self):
        return f"{self.brand}: {self.engine.start()}"

car = Car('Toyota', 200)
print(car.start())  # Toyota: Engine started
```

## When to Use Each

| Use Inheritance When      | Use Composition When       |
| ------------------------- | -------------------------- |
| Clear "is-a" relationship | "Has-a" relationship       |
| Need to override behavior | Need flexibility           |
| Stable hierarchy          | Components may change      |
| Example: Dog is-a Animal  | Example: Car has-an Engine |

# Key Concepts Summary

## Inheritance Essentials

| Concept          | Description                        | Example                      |
| ---------------- | ---------------------------------- | ---------------------------- |
| **Inheritance**  | Child class inherits from parent   | `class Dog(Animal):`         |
| **super()**      | Access parent class methods        | `super().__init__()`         |
| **Override**     | Replace parent method              | Define method with same name |
| **Extend**       | Add to parent functionality        | Call `super()` + add more    |
| **isinstance()** | Check object type                  | `isinstance(dog, Animal)`    |
| **issubclass()** | Check class relationship           | `issubclass(Dog, Animal)`    |
| **Polymorphism** | Same interface, different behavior | `animal.speak()`             |
| **ABC**          | Abstract base class                | `from abc import ABC`        |
| **Composition**  | Object contains other objects      | `self.engine = Engine()`     |

## Best Practices

1. **Keep hierarchies shallow** - Avoid deep inheritance chains
2. **Use composition when possible** - More flexible than inheritance
3. **Follow Liskov Substitution** - Child should work wherever parent works
4. **Don't override methods unnecessarily** - Only when needed
5. **Use abstract classes** - To define interfaces
