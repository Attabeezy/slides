# Regular Expressions

## re Module

```python
import re

# Search for pattern
text = "The price is $100"
match = re.search(r'\$\d+', text)
if match:
    print(match.group())  # $100

# Find all matches
text = "Call 123-456-7890 or 098-765-4321"
phones = re.findall(r'\d{3}-\d{3}-\d{4}', text)
print(phones)  # ['123-456-7890', '098-765-4321']

# Replace
text = "Hello world"
new_text = re.sub(r'world', 'Python', text)
print(new_text)  # Hello Python

# Split
text = "apple,banana;orange:grape"
fruits = re.split(r'[,;:]', text)
print(fruits)  # ['apple', 'banana', 'orange', 'grape']
```

## Common Patterns

```python
import re

# Email validation
email = "user@example.com"
pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'
if re.match(pattern, email):
    print("Valid email")

# Phone number
phone = "(123) 456-7890"
pattern = r'\(\d{3}\) \d{3}-\d{4}'

# URL
url = "https://www.example.com"
pattern = r'https?://[\w\.-]+'
```
