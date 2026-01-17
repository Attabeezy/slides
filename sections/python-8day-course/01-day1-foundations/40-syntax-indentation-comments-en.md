# Python Syntax Basics

## Python Syntax

Python uses indentation to define code blocks, making code clean and readable.

### Simple Statement

```python
print("Hello, World!")
```

## Indentation

Indentation is **required** in Python to define blocks of code.

**Correct:**

```python
if 5 > 2:
    print("Five is greater than two")
```

**Incorrect:**

```python
if 5 > 2:
print("Five is greater than two")  # IndentationError!
```

### Indentation Rules

- Use 4 spaces (recommended) or 1 tab
- Be consistent throughout your code
- Don't mix tabs and spaces

## Comments

Comments are ignored by Python but help humans understand code.

### Single-Line Comments

```python
# This is a comment
print("Hello")  # This is also a comment
```

### Multi-Line Comments

Use triple quotes (though technically this creates a string):

```python
"""
This is a multi-line comment.
It can span multiple lines.
Python ignores it if not assigned to a variable.
"""

'''
You can also use single quotes
for multi-line comments.
'''
```

### When to Use Comments

- Explain complex logic
- Document function purposes
- Provide context for future readers
- Temporarily disable code during testing

**Good comment:**

```python
# Calculate compound interest: A = P(1 + r/n)^(nt)
final_amount = principal * (1 + rate / compounds) ** (compounds * time)
```

**Bad comment (obvious):**

```python
# Add 1 to x
x = x + 1
```

