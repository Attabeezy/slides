# Dictionary Methods

## update() - Merge Dictionaries

```python
dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, 'd': 4}

dict1.update(dict2)
print(dict1)  # {'a': 1, 'b': 2, 'c': 3, 'd': 4}

# Overwrites existing keys
dict1.update({'a': 999})
print(dict1)  # {'a': 999, 'b': 2, 'c': 3, 'd': 4}
```

## setdefault() - Get or Set Default

```python
person = {'name': 'Alice'}

# Get existing key
print(person.setdefault('name', 'Unknown'))  # 'Alice'

# Get and set if missing
print(person.setdefault('age', 25))  # 25
print(person)  # {'name': 'Alice', 'age': 25}
```

## fromkeys() - Create Dictionary from Keys

```python
keys = ['a', 'b', 'c']
default_value = 0

result = dict.fromkeys(keys, default_value)
print(result)  # {'a': 0, 'b': 0, 'c': 0}
```

## copy() - Shallow Copy

```python
original = {'a': 1, 'b': 2}
copy = original.copy()

copy['a'] = 999
print(original)  # {'a': 1, 'b': 2} (unchanged)
print(copy)      # {'a': 999, 'b': 2}
```
