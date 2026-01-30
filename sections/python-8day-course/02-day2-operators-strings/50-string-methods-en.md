# String Methods

## Indexing and Slicing

### Accessing Characters by Index

Strings are sequences - each character has an index starting from 0.

```python
text = "Python"
print(text[0])   # 'P' (first character)
print(text[1])   # 'y'
print(text[5])   # 'n' (last character)

# Negative indexing (from the end)
print(text[-1])  # 'n' (last character)
print(text[-2])  # 'o'
print(text[-6])  # 'P' (first character)
```

## Slicing

Extract substrings using `[start:stop:step]`.

```python
text = "Python Programming"

# Basic slicing
print(text[0:6])    # 'Python' (index 0 to 5)
print(text[7:18])   # 'Programming'

# Omit start (defaults to 0)
print(text[:6])     # 'Python'

# Omit stop (goes to end)
print(text[7:])     # 'Programming'

# Negative indices
print(text[-11:])   # 'Programming'
print(text[:-12])   # 'Python'

# Step parameter
print(text[::2])    # 'Pto rgamn' (every 2nd character)
print(text[::3])    # 'Ph ormn' (every 3rd character)

# Reverse a string
print(text[::-1])   # 'gnimmargorP nohtyP'
```

# Case Conversion Methods

```python
text = "Python Programming"

print(text.upper())        # 'PYTHON PROGRAMMING'
print(text.lower())        # 'python programming'
print(text.capitalize())   # 'Python programming'
print(text.title())        # 'Python Programming'
print(text.swapcase())     # 'pYTHON pROGRAMMING'

# Case checking
print("HELLO".isupper())   # True
print("hello".islower())   # True
print("Hello".istitle())   # True
```

## Searching Methods

```python
text = "Python is awesome. Python is powerful."

# find() - returns index or -1 if not found
print(text.find("Python"))        # 0
print(text.find("is"))            # 7
print(text.find("Java"))          # -1

# rfind() - find from right (last occurrence)
print(text.rfind("Python"))       # 19
print(text.rfind("is"))           # 26

# index() - like find() but raises error if not found
print(text.index("awesome"))      # 10
# print(text.index("Java"))       # ValueError!

# count() - count occurrences
print(text.count("Python"))       # 2
print(text.count("is"))           # 2
print(text.count("o"))            # 4
```

# Testing and Cleaning Methods

```python
# Check string content
print("Python123".isalnum())      # True (alphanumeric)
print("Python".isalpha())         # True (all letters)
print("12345".isdigit())          # True (all digits)
print("12345".isnumeric())        # True (numeric characters)
print("123.45".isdigit())         # False (dot not a digit)

# Check identifier validity
print("my_var".isidentifier())    # True
print("2var".isidentifier())      # False (starts with number)
print("my-var".isidentifier())    # False (hyphen not allowed)

# Check whitespace
print("   ".isspace())            # True
print("Hello".isspace())          # False
```

## Cleaning Methods

```python
# strip() - remove whitespace from both ends
text = "   Hello, World!   "
print(text.strip())               # 'Hello, World!'
print(text.lstrip())              # 'Hello, World!   '
print(text.rstrip())              # '   Hello, World!'

# Remove specific characters
text = "###Python###"
print(text.strip("#"))            # 'Python'

# Remove from beginning or end only
print("www.example.com".lstrip("w."))    # 'example.com'
print("file.txt".rstrip(".txt"))         # 'file'
```

# Modification Methods

```python
# replace() - replace substring
text = "I love Java"
print(text.replace("Java", "Python"))    # 'I love Python'

# Replace with count limit
text = "ha ha ha ha"
print(text.replace("ha", "he", 2))       # 'he he ha ha'

# split() - split into list
text = "Python is awesome"
print(text.split())                      # ['Python', 'is', 'awesome']

text = "apple,banana,orange"
print(text.split(","))                   # ['apple', 'banana', 'orange']

# join() - join list into string
words = ["Python", "is", "awesome"]
print(" ".join(words))                   # 'Python is awesome'
print("-".join(words))                   # 'Python-is-awesome'
```

## Alignment and Padding

```python
text = "Python"

# Center align
print(text.center(20))            # '       Python       '
print(text.center(20, "*"))       # '*******Python*******'

# Left align
print(text.ljust(20))             # 'Python              '
print(text.ljust(20, "-"))        # 'Python--------------'

# Right align
print(text.rjust(20))             # '              Python'
print(text.rjust(20, "="))        # '==============Python'

# Zero padding for numbers
print("42".zfill(5))              # '00042'
print("-42".zfill(5))             # '-0042'
```

## Start/End Checking

```python
text = "Python Programming"

# startswith()
print(text.startswith("Python"))        # True
print(text.startswith("Java"))          # False
print(text.startswith("Prog", 7))       # True (from index 7)

# endswith()
print(text.endswith("ing"))             # True
print(text.endswith("Python"))          # False
```

## Useful String Methods Summary

| Method | Description | Example |
|--------|-------------|---------|
| `upper()` | Convert to uppercase | `"hi".upper()` → `"HI"` |
| `lower()` | Convert to lowercase | `"HI".lower()` → `"hi"` |
| `capitalize()` | First letter uppercase | `"hi".capitalize()` → `"Hi"` |
| `title()` | Title case | `"hi there".title()` → `"Hi There"` |
| `strip()` | Remove whitespace | `" hi ".strip()` → `"hi"` |
| `replace(old, new)` | Replace substring | `"cat".replace("c", "b")` → `"bat"` |
| `split()` | Split into list | `"a b c".split()` → `['a', 'b', 'c']` |
| `join(list)` | Join list to string | `"-".join(['a','b'])` → `"a-b"` |
| `find(sub)` | Find substring index | `"hello".find("ll")` → `2` |
| `count(sub)` | Count occurrences | `"aaa".count("a")` → `3` |
| `startswith(sub)` | Check prefix | `"hello".startswith("he")` → `True` |
| `endswith(sub)` | Check suffix | `"hello".endswith("lo")` → `True` |
| `isdigit()` | Check if digits | `"123".isdigit()` → `True` |
| `isalpha()` | Check if letters | `"abc".isalpha()` → `True` |

