# Working with File Formats

## JSON

```python
import json

# Write JSON
data = {'name': 'Alice', 'age': 25, 'city': 'Boston'}
with open('data.json', 'w') as file:
    json.dump(data, file, indent=2)

# Read JSON
with open('data.json', 'r') as file:
    data = json.load(file)
    print(data['name'])  # Alice

# String conversion
json_string = json.dumps(data)
data_back = json.loads(json_string)
```

## CSV

```python
import csv

# Write CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', 25, 'Boston'],
    ['Bob', 30, 'New York']
]

with open('data.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Read CSV
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Dict reader
with open('data.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row['Name'], row['Age'])
```
