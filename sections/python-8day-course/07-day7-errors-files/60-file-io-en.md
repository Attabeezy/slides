# File Input/Output

## Reading Files

```python
# Read entire file
with open('file.txt', 'r') as file:
    content = file.read()
    print(content)

# Read line by line
with open('file.txt', 'r') as file:
    for line in file:
        print(line.strip())

# Read into list
with open('file.txt', 'r') as file:
    lines = file.readlines()
```

## Writing Files

```python
# Write mode (overwrites)
with open('output.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("Python is great!\n")

# Append mode
with open('output.txt', 'a') as file:
    file.write("New line\n")

# Write list
lines = ['Line 1\n', 'Line 2\n', 'Line 3\n']
with open('output.txt', 'w') as file:
    file.writelines(lines)
```

## File Modes

- `'r'` - Read (default)
- `'w'` - Write (overwrite)
- `'a'` - Append
- `'x'` - Create (error if exists)
- `'r+'` - Read and write
- `'b'` - Binary mode

## File Paths

```python
import os

# Check if file exists
if os.path.exists('file.txt'):
    print("File exists")

# Get file size
size = os.path.getsize('file.txt')

# Get absolute path
abs_path = os.path.abspath('file.txt')
```
