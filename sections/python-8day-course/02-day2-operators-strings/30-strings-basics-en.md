# String Basics

## Creating Strings

Strings are sequences of characters enclosed in quotes.

### Single and Double Quotes

```python
# Single quotes
name = 'Python'
message = 'Hello, World!'

# Double quotes
name = "Python"
message = "Hello, World!"

# Both work the same
print('Python' == "Python")  # True
```

### When to Use Which?

```python
# Use single quotes when string contains double quotes
sentence = 'He said, "Python is awesome!"'

# Use double quotes when string contains single quotes
sentence = "It's a beautiful day"

# Or use escape character
sentence = 'It\'s a beautiful day'
```

### Multi-Line Strings

Use triple quotes for multi-line text:

```python
# Triple single quotes
text = '''This is a
multi-line
string'''

# Triple double quotes
paragraph = """Python is a powerful language.
It's easy to learn and fun to use.
Let's master it together!"""

print(paragraph)
```

## String Concatenation

Combine strings using the `+` operator.

```python
first_name = "John"
last_name = "Doe"

# Concatenation
full_name = first_name + " " + last_name
print(full_name)  # John Doe

# Multiple concatenations
greeting = "Hello, " + "my " + "name " + "is " + full_name
print(greeting)  # Hello, my name is John Doe
```

### String Repetition

Use `*` operator to repeat strings:

```python
print("=" * 20)         # ====================
print("Ha" * 3)         # HaHaHa
print("Python! " * 3)   # Python! Python! Python! 

# Create separators
separator = "-" * 50
print(separator)
```

## Escape Sequences

Special characters in strings.

| Escape | Meaning | Example |
|--------|---------|---------|
| `\n` | New line | `"Line1\nLine2"` |
| `\t` | Tab (4 spaces) | `"Name:\tJohn"` |
| `\` | Backslash | `"C:\Users"` |
| `\'` | Single quote | `'It\'s'` |
| `\"` | Double quote | `"Say \"Hi\""` |

### Examples

```python
# New line
print("Hello\nWorld")
# Output:
# Hello
# World

# Tab spacing
print("Name:\tJohn\nAge:\t25")
# Output:
# Name:	John
# Age:	25

# Backslash in file paths
path = "C:\Users\Documents\file.txt"
print(path)  # C:\Users\Documents\file.txt

# Quotes in strings
print("She said, \"Hello!\"")  # She said, "Hello!"
print('It\'s a nice day')      # It's a nice day
```

### Raw Strings

Prefix with `r` to ignore escape sequences:

```python
# Normal string (escape sequences processed)
path1 = "C:\new\test"
print(path1)  # C:
              # ew	est (interprets \n and \t)

# Raw string (escape sequences ignored)
path2 = r"C:\new\test"
print(path2)  # C:\new\test
```

## String Length

Use `len()` to get string length:

```python
text = "Python"
print(len(text))  # 6

# Empty string
print(len(""))  # 0

# With spaces
sentence = "Hello World"
print(len(sentence))  # 11 (space counts!)

# Multi-line strings
paragraph = """Line 1
Line 2
Line 3"""
print(len(paragraph))  # includes newline characters
```

## Checking String Content

```python
# Check if substring exists
text = "Python Programming"
print("Python" in text)      # True
print("Java" in text)        # False
print("python" in text)      # False (case-sensitive!)

# Check if string starts/ends with substring
print(text.startswith("Python"))  # True
print(text.endswith("ming"))      # True
print(text.startswith("Java"))    # False
```

## String Comparison

```python
# Exact comparison
print("Python" == "Python")   # True
print("Python" == "python")   # False (case-sensitive)

# Lexicographic comparison (alphabetical order)
print("apple" < "banana")     # True
print("cat" > "car")          # True

# Case-insensitive comparison
s1 = "Python"
s2 = "python"
print(s1.lower() == s2.lower())  # True
```

