# Day 8 Exercises

## Level 1: Classes and Objects

1. Create a `Book` class with title, author, and pages attributes
2. Add a method to `Book` that returns a formatted string
3. Create a `Circle` class that calculates area and circumference
4. Create a `Temperature` class that converts between Celsius and Fahrenheit
5. Create a `Counter` class with increment, decrement, and reset methods

# Day 8 Exercises - Level 2

1. Create an `Animal` base class and `Dog`, `Cat` child classes with different `speak()` methods
2. Create a `Vehicle` hierarchy: `Vehicle` -> `Car` -> `ElectricCar`
3. Implement a `BankAccount` class with a `SavingsAccount` subclass
4. Create a `Shape` hierarchy with `Rectangle`, `Circle`, and `Triangle`
5. Build an `Employee` system with `Manager` and `Developer` subclasses

# Day 8 Exercises - Level 3

1. Create a simple library management system with `Library`, `Book`, and `Member` classes
2. Build a todo list application using OOP
3. Scrape quotes from http://quotes.toscrape.com and save to CSV
4. Create a contact manager that saves to JSON file
5. Analyze a CSV file with Pandas and create visualizations

# Day 8 Solutions - Level 1

```python
# 1. Book class
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages

    def __str__(self):
        return f"'{self.title}' by {self.author} ({self.pages} pages)"

book = Book('1984', 'George Orwell', 328)
print(book)  # '1984' by George Orwell (328 pages)

# 2. Circle class
import math

class Circle:
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

    def circumference(self):
        return 2 * math.pi * self.radius

    def __str__(self):
        return f"Circle(radius={self.radius})"

circle = Circle(5)
print(circle)                      # Circle(radius=5)
print(f"Area: {circle.area():.2f}")           # Area: 78.54
print(f"Circumference: {circle.circumference():.2f}")  # Circumference: 31.42

# 3. Temperature class
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    def to_fahrenheit(self):
        return (self.celsius * 9/5) + 32

    @classmethod
    def from_fahrenheit(cls, fahrenheit):
        celsius = (fahrenheit - 32) * 5/9
        return cls(celsius)

    def __str__(self):
        return f"{self.celsius}°C ({self.to_fahrenheit():.1f}°F)"

temp1 = Temperature(25)
print(temp1)  # 25°C (77.0°F)

temp2 = Temperature.from_fahrenheit(98.6)
print(temp2)  # 37.0°C (98.6°F)

# 4. Counter class
class Counter:
    def __init__(self, start=0):
        self.count = start
        self.initial = start

    def increment(self, amount=1):
        self.count += amount

    def decrement(self, amount=1):
        self.count -= amount

    def reset(self):
        self.count = self.initial

    def __str__(self):
        return f"Counter: {self.count}"

counter = Counter()
counter.increment()
counter.increment(5)
print(counter)  # Counter: 6
counter.decrement(2)
print(counter)  # Counter: 4
counter.reset()
print(counter)  # Counter: 0
```

# Day 8 Solutions - Level 2

```python
# 1. Animal hierarchy
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return "Some sound"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

dog = Dog('Buddy')
cat = Cat('Whiskers')
print(dog.speak())  # Buddy says Woof!
print(cat.speak())  # Whiskers says Meow!

# 2. Vehicle hierarchy
class Vehicle:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def info(self):
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    def __init__(self, brand, model, doors):
        super().__init__(brand, model)
        self.doors = doors

    def info(self):
        return f"{super().info()} ({self.doors} doors)"

class ElectricCar(Car):
    def __init__(self, brand, model, doors, battery_kwh):
        super().__init__(brand, model, doors)
        self.battery_kwh = battery_kwh

    def info(self):
        return f"{super().info()} - {self.battery_kwh}kWh battery"

car = ElectricCar('Tesla', 'Model 3', 4, 75)
print(car.info())  # Tesla Model 3 (4 doors) - 75kWh battery

# 3. BankAccount with SavingsAccount
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return f"Deposited ${amount}. Balance: ${self.balance}"
        return "Invalid amount"

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            return f"Withdrew ${amount}. Balance: ${self.balance}"
        return "Invalid amount or insufficient funds"

class SavingsAccount(BankAccount):
    def __init__(self, owner, balance=0, interest_rate=0.02):
        super().__init__(owner, balance)
        self.interest_rate = interest_rate

    def apply_interest(self):
        interest = self.balance * self.interest_rate
        self.balance += interest
        return f"Applied ${interest:.2f} interest. Balance: ${self.balance:.2f}"

savings = SavingsAccount('Alice', 1000, 0.05)
print(savings.deposit(500))      # Deposited $500. Balance: $1500
print(savings.apply_interest())  # Applied $75.00 interest. Balance: $1575.00

# 4. Shape hierarchy
import math

class Shape:
    def area(self):
        raise NotImplementedError

    def perimeter(self):
        raise NotImplementedError

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

    def perimeter(self):
        return 2 * math.pi * self.radius

class Triangle(Shape):
    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c

    def area(self):
        # Heron's formula
        s = (self.a + self.b + self.c) / 2
        return math.sqrt(s * (s - self.a) * (s - self.b) * (s - self.c))

    def perimeter(self):
        return self.a + self.b + self.c

shapes = [
    Rectangle(5, 3),
    Circle(4),
    Triangle(3, 4, 5)
]

for shape in shapes:
    print(f"{shape.__class__.__name__}:")
    print(f"  Area: {shape.area():.2f}")
    print(f"  Perimeter: {shape.perimeter():.2f}")

# 5. Employee system
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def get_bonus(self):
        return self.salary * 0.05

    def __str__(self):
        return f"{self.name} - ${self.salary}"

class Manager(Employee):
    def __init__(self, name, salary, team_size):
        super().__init__(name, salary)
        self.team_size = team_size

    def get_bonus(self):
        base_bonus = super().get_bonus()
        team_bonus = self.team_size * 1000
        return base_bonus + team_bonus

    def __str__(self):
        return f"Manager: {super().__str__()} (Team: {self.team_size})"

class Developer(Employee):
    def __init__(self, name, salary, language):
        super().__init__(name, salary)
        self.language = language

    def get_bonus(self):
        return self.salary * 0.10

    def __str__(self):
        return f"Developer: {super().__str__()} ({self.language})"

manager = Manager('Alice', 100000, 5)
developer = Developer('Bob', 80000, 'Python')

print(manager)
print(f"Bonus: ${manager.get_bonus():.2f}")

print(developer)
print(f"Bonus: ${developer.get_bonus():.2f}")
```

# Day 8 Solutions - Level 3

```python
# 1. Library Management System
class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.is_borrowed = False

    def __str__(self):
        status = "Borrowed" if self.is_borrowed else "Available"
        return f"{self.title} by {self.author} [{status}]"

class Member:
    def __init__(self, name, member_id):
        self.name = name
        self.member_id = member_id
        self.borrowed_books = []

    def borrow_book(self, book):
        if not book.is_borrowed:
            book.is_borrowed = True
            self.borrowed_books.append(book)
            return f"{self.name} borrowed '{book.title}'"
        return f"'{book.title}' is not available"

    def return_book(self, book):
        if book in self.borrowed_books:
            book.is_borrowed = False
            self.borrowed_books.remove(book)
            return f"{self.name} returned '{book.title}'"
        return f"{self.name} doesn't have '{book.title}'"

class Library:
    def __init__(self, name):
        self.name = name
        self.books = []
        self.members = []

    def add_book(self, book):
        self.books.append(book)
        return f"Added '{book.title}' to {self.name}"

    def register_member(self, member):
        self.members.append(member)
        return f"Registered {member.name}"

    def list_available_books(self):
        available = [book for book in self.books if not book.is_borrowed]
        return available

# Usage
library = Library('City Library')

book1 = Book('1984', 'George Orwell', '123456')
book2 = Book('To Kill a Mockingbird', 'Harper Lee', '234567')
library.add_book(book1)
library.add_book(book2)

member = Member('Alice', 'M001')
library.register_member(member)

print(member.borrow_book(book1))  # Alice borrowed '1984'
print(book1)                      # 1984 by George Orwell [Borrowed]

print("\nAvailable books:")
for book in library.list_available_books():
    print(f"  {book}")

# 2. Todo List Application
import json
from datetime import datetime

class Task:
    def __init__(self, title, description='', priority='medium'):
        self.title = title
        self.description = description
        self.priority = priority
        self.completed = False
        self.created_at = datetime.now().isoformat()

    def mark_complete(self):
        self.completed = True

    def to_dict(self):
        return {
            'title': self.title,
            'description': self.description,
            'priority': self.priority,
            'completed': self.completed,
            'created_at': self.created_at
        }

    def __str__(self):
        status = '✓' if self.completed else ' '
        return f"[{status}] {self.title} ({self.priority})"

class TodoList:
    def __init__(self, filename='todos.json'):
        self.filename = filename
        self.tasks = []
        self.load()

    def add_task(self, task):
        self.tasks.append(task)
        self.save()
        return f"Added: {task.title}"

    def remove_task(self, index):
        if 0 <= index < len(self.tasks):
            task = self.tasks.pop(index)
            self.save()
            return f"Removed: {task.title}"
        return "Invalid index"

    def complete_task(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index].mark_complete()
            self.save()
            return f"Completed: {self.tasks[index].title}"
        return "Invalid index"

    def list_tasks(self):
        if not self.tasks:
            return "No tasks"
        return "\n".join(f"{i}. {task}" for i, task in enumerate(self.tasks))

    def save(self):
        data = [task.to_dict() for task in self.tasks]
        with open(self.filename, 'w') as f:
            json.dump(data, f, indent=4)

    def load(self):
        try:
            with open(self.filename, 'r') as f:
                data = json.load(f)
                for task_dict in data:
                    task = Task(
                        task_dict['title'],
                        task_dict['description'],
                        task_dict['priority']
                    )
                    task.completed = task_dict['completed']
                    task.created_at = task_dict['created_at']
                    self.tasks.append(task)
        except FileNotFoundError:
            pass

# Usage
todo = TodoList()
todo.add_task(Task('Learn Python OOP', 'Complete Day 8', 'high'))
todo.add_task(Task('Build a project', 'Use what I learned', 'medium'))
print(todo.list_tasks())
todo.complete_task(0)
print("\n" + todo.list_tasks())

# 3. Web Scraping
import requests
from bs4 import BeautifulSoup
import csv

def scrape_quotes():
    """Scrape quotes and save to CSV"""
    url = 'http://quotes.toscrape.com/'
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    quotes = []
    for div in soup.find_all('div', class_='quote'):
        quote = {
            'text': div.find('span', class_='text').text,
            'author': div.find('small', class_='author').text,
            'tags': ', '.join([tag.text for tag in div.find_all('a', class_='tag')])
        }
        quotes.append(quote)

    # Save to CSV
    with open('quotes.csv', 'w', newline='', encoding='utf-8') as f:
        writer = csv.DictWriter(f, fieldnames=['text', 'author', 'tags'])
        writer.writeheader()
        writer.writerows(quotes)

    return f"Scraped {len(quotes)} quotes to quotes.csv"

print(scrape_quotes())

# 4. Contact Manager
import json

class Contact:
    def __init__(self, name, email, phone):
        self.name = name
        self.email = email
        self.phone = phone

    def to_dict(self):
        return {
            'name': self.name,
            'email': self.email,
            'phone': self.phone
        }

    def __str__(self):
        return f"{self.name} - {self.email} - {self.phone}"

class ContactManager:
    def __init__(self, filename='contacts.json'):
        self.filename = filename
        self.contacts = []
        self.load()

    def add_contact(self, contact):
        self.contacts.append(contact)
        self.save()
        return f"Added {contact.name}"

    def find_contact(self, name):
        for contact in self.contacts:
            if contact.name.lower() == name.lower():
                return contact
        return None

    def list_contacts(self):
        if not self.contacts:
            return "No contacts"
        return "\n".join(str(contact) for contact in self.contacts)

    def save(self):
        data = [contact.to_dict() for contact in self.contacts]
        with open(self.filename, 'w') as f:
            json.dump(data, f, indent=4)

    def load(self):
        try:
            with open(self.filename, 'r') as f:
                data = json.load(f)
                for contact_dict in data:
                    contact = Contact(
                        contact_dict['name'],
                        contact_dict['email'],
                        contact_dict['phone']
                    )
                    self.contacts.append(contact)
        except FileNotFoundError:
            pass

# Usage
manager = ContactManager()
manager.add_contact(Contact('Alice Smith', 'alice@example.com', '555-0001'))
manager.add_contact(Contact('Bob Jones', 'bob@example.com', '555-0002'))
print(manager.list_contacts())

# 5. Data Analysis with Pandas
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Create sample data
np.random.seed(42)
data = {
    'Date': pd.date_range('2024-01-01', periods=100),
    'Sales': np.random.randint(100, 500, 100),
    'Expenses': np.random.randint(50, 300, 100)
}

df = pd.DataFrame(data)
df['Profit'] = df['Sales'] - df['Expenses']

# Analysis
print("=== Summary Statistics ===")
print(df[['Sales', 'Expenses', 'Profit']].describe())

print(f"\nTotal Profit: ${df['Profit'].sum():,.2f}")
print(f"Average Daily Profit: ${df['Profit'].mean():.2f}")

# Visualization
fig, axes = plt.subplots(2, 2, figsize=(12, 10))

# Line plot
df.plot(x='Date', y=['Sales', 'Expenses'], ax=axes[0, 0])
axes[0, 0].set_title('Sales vs Expenses Over Time')
axes[0, 0].set_ylabel('Amount ($)')

# Profit over time
df.plot(x='Date', y='Profit', ax=axes[0, 1], color='green')
axes[0, 1].set_title('Profit Over Time')
axes[0, 1].set_ylabel('Profit ($)')

# Distribution
axes[1, 0].hist(df['Profit'], bins=20, edgecolor='black')
axes[1, 0].set_title('Profit Distribution')
axes[1, 0].set_xlabel('Profit ($)')
axes[1, 0].set_ylabel('Frequency')

# Box plot
df[['Sales', 'Expenses', 'Profit']].boxplot(ax=axes[1, 1])
axes[1, 1].set_title('Box Plot Comparison')
axes[1, 1].set_ylabel('Amount ($)')

plt.tight_layout()
plt.savefig('analysis.png')
print("\nVisualization saved to analysis.png")
```

# Challenge: Complete Project

Build a **Student Management System** that:

1. Has classes for `Student`, `Course`, and `Grade`
2. Allows enrolling students in courses
3. Records and calculates grades
4. Saves/loads data from JSON
5. Generates reports (average grades, student rankings)
6. Creates visualizations of grade distributions

This combines everything you've learned: OOP, file I/O, data structures, and potentially Pandas/Matplotlib!
