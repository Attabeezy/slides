# Day 7 Exercises

## Level 1: Exception Handling

1. Write code with try-except for division by zero
2. Handle ValueError when converting string to int
3. Try to open a non-existent file and handle the error
4. Create a function that validates user input (age > 0)
5. Use try-except-finally to ensure cleanup

# Day 7 Exercises - Level 2

1. Read a text file and print its contents
2. Write a list of strings to a file
3. Count lines in a file
4. Copy content from one file to another
5. Append text to an existing file

# Day 7 Exercises - Level 3

1. Create a program to read/write JSON config files
2. Parse CSV file and calculate averages
3. Create a log file with timestamps
4. Search for text patterns in files using regex
5. Build a contact manager that saves to JSON

# Day 7 Solutions

### Level 1 Solutions

```python
# 1. Division by zero
def safe_divide(a, b):
    try:
        result = a / b
        return result
    except ZeroDivisionError:
        return "Error: Cannot divide by zero!"

print(safe_divide(10, 2))   # 5.0
print(safe_divide(10, 0))   # Error message

# 2. String to int conversion
def convert_to_int(value):
    try:
        return int(value)
    except ValueError:
        return f"Error: '{value}' is not a valid integer"

print(convert_to_int("123"))    # 123
print(convert_to_int("abc"))    # Error message

# 3. File handling
try:
    with open('nonexistent.txt', 'r') as f:
        content = f.read()
except FileNotFoundError:
    print("Error: File not found!")

# 4. Input validation
def validate_age(age):
    try:
        age_int = int(age)
        if age_int <= 0:
            raise ValueError("Age must be positive")
        return age_int
    except ValueError as e:
        return f"Invalid age: {e}"

print(validate_age("25"))   # 25
print(validate_age("-5"))   # Error message
print(validate_age("abc"))  # Error message

# 5. Try-except-finally
def process_file(filename):
    file = None
    try:
        file = open(filename, 'r')
        content = file.read()
        print(content)
    except FileNotFoundError:
        print("File not found")
    finally:
        if file:
            file.close()
            print("File closed")
```

# Day 7 Level 2 Solutions

```python
# 1. Read file
try:
    with open('example.txt', 'r') as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("File not found")

# 2. Write list to file
names = ['Alice', 'Bob', 'Charlie', 'Diana']
with open('names.txt', 'w') as file:
    for name in names:
        file.write(name + '\n')

# 3. Count lines
def count_lines(filename):
    try:
        with open(filename, 'r') as file:
            lines = file.readlines()
            return len(lines)
    except FileNotFoundError:
        return "File not found"

print(f"Lines: {count_lines('example.txt')}")

# 4. Copy file
def copy_file(source, destination):
    try:
        with open(source, 'r') as src:
            content = src.read()
        with open(destination, 'w') as dst:
            dst.write(content)
        print(f"Copied {source} to {destination}")
    except FileNotFoundError:
        print("Source file not found")

copy_file('original.txt', 'copy.txt')

# 5. Append to file
with open('log.txt', 'a') as file:
    file.write('New log entry\n')
```

# Day 7 Level 3 Solutions

```python
# 1. JSON config manager
import json

def save_config(filename, config):
    with open(filename, 'w') as file:
        json.dump(config, file, indent=4)

def load_config(filename):
    try:
        with open(filename, 'r') as file:
            return json.load(file)
    except FileNotFoundError:
        return {}

# Usage
config = {
    'username': 'admin',
    'theme': 'dark',
    'language': 'en'
}
save_config('config.json', config)
loaded = load_config('config.json')
print(loaded)

# 2. CSV averages
import csv

def calculate_csv_averages(filename):
    try:
        with open(filename, 'r') as file:
            reader = csv.DictReader(file)
            totals = {}
            counts = {}

            for row in reader:
                for key, value in row.items():
                    try:
                        num_value = float(value)
                        totals[key] = totals.get(key, 0) + num_value
                        counts[key] = counts.get(key, 0) + 1
                    except ValueError:
                        pass

            averages = {key: totals[key] / counts[key]
                       for key in totals}
            return averages
    except FileNotFoundError:
        return "File not found"

# 3. Log file with timestamps
from datetime import datetime

def write_log(message, filename='app.log'):
    timestamp = datetime.now().strftime('%Y-%m-%d %H:%M:%S')
    log_entry = f"[{timestamp}] {message}\n"

    with open(filename, 'a') as file:
        file.write(log_entry)

write_log('Application started')
write_log('User logged in')
write_log('Error occurred')

# 4. Search with regex
import re

def search_in_files(pattern, filename):
    try:
        with open(filename, 'r') as file:
            matches = []
            for line_num, line in enumerate(file, 1):
                if re.search(pattern, line):
                    matches.append((line_num, line.strip()))
            return matches
    except FileNotFoundError:
        return []

# Search for email patterns
results = search_in_files(r'\b[\w.-]+@[\w.-]+\.\w+\b', 'data.txt')
for line_num, line in results:
    print(f"Line {line_num}: {line}")

# 5. Contact manager
import json
from datetime import datetime

class ContactManager:
    def __init__(self, filename='contacts.json'):
        self.filename = filename
        self.contacts = self.load_contacts()

    def load_contacts(self):
        try:
            with open(self.filename, 'r') as file:
                return json.load(file)
        except FileNotFoundError:
            return []

    def save_contacts(self):
        with open(self.filename, 'w') as file:
            json.dump(self.contacts, file, indent=4)

    def add_contact(self, name, email, phone):
        contact = {
            'name': name,
            'email': email,
            'phone': phone,
            'created': datetime.now().isoformat()
        }
        self.contacts.append(contact)
        self.save_contacts()
        print(f"Added contact: {name}")

    def find_contact(self, name):
        for contact in self.contacts:
            if contact['name'].lower() == name.lower():
                return contact
        return None

    def list_contacts(self):
        if not self.contacts:
            print("No contacts found")
        else:
            for i, contact in enumerate(self.contacts, 1):
                print(f"{i}. {contact['name']} - {contact['email']}")

# Usage
manager = ContactManager()
manager.add_contact('Alice Smith', 'alice@example.com', '555-0001')
manager.add_contact('Bob Jones', 'bob@example.com', '555-0002')
manager.list_contacts()
```

# Challenge: Log File Analyzer

Create a program that:

- Reads a log file with timestamps
- Counts errors, warnings, and info messages
- Finds the time range of logs
- Extracts unique error messages
- Saves a summary report as JSON

```python
import re
from datetime import datetime
from collections import Counter
import json

def analyze_log(filename):
    try:
        with open(filename, 'r') as file:
            lines = file.readlines()

        if not lines:
            return "Empty log file"

        # Parse logs
        log_pattern = r'\[(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2})\] (\w+): (.+)'

        timestamps = []
        levels = []
        messages = []

        for line in lines:
            match = re.match(log_pattern, line)
            if match:
                timestamp, level, message = match.groups()
                timestamps.append(datetime.strptime(timestamp, '%Y-%m-%d %H:%M:%S'))
                levels.append(level)
                messages.append(message)

        # Analyze
        level_counts = Counter(levels)
        error_messages = [msg for lvl, msg in zip(levels, messages)
                         if lvl == 'ERROR']

        report = {
            'total_entries': len(timestamps),
            'time_range': {
                'start': min(timestamps).isoformat() if timestamps else None,
                'end': max(timestamps).isoformat() if timestamps else None
            },
            'level_counts': dict(level_counts),
            'unique_errors': len(set(error_messages)),
            'error_messages': list(set(error_messages))
        }

        # Save report
        with open('log_analysis.json', 'w') as f:
            json.dump(report, f, indent=4)

        return report

    except FileNotFoundError:
        return "Log file not found"

# Test
result = analyze_log('app.log')
print(json.dumps(result, indent=2))
```
