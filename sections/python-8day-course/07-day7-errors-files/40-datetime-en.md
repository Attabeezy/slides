# Date and Time

## datetime Module

```python
from datetime import datetime, date, time, timedelta

# Current date and time
now = datetime.now()
print(now)  # 2024-01-15 14:30:00.123456

# Current date
today = date.today()
print(today)  # 2024-01-15

# Create specific datetime
dt = datetime(2024, 12, 25, 10, 30)
print(dt)  # 2024-12-25 10:30:00
```

## Formatting Dates

```python
from datetime import datetime

now = datetime.now()

# strftime - format to string
print(now.strftime("%Y-%m-%d"))           # 2024-01-15
print(now.strftime("%d/%m/%Y"))           # 15/01/2024
print(now.strftime("%B %d, %Y"))          # January 15, 2024
print(now.strftime("%H:%M:%S"))           # 14:30:45
print(now.strftime("%A, %B %d, %Y"))      # Monday, January 15, 2024
```

## Parsing Dates

```python
from datetime import datetime

# strptime - parse string to datetime
date_string = "2024-12-25"
dt = datetime.strptime(date_string, "%Y-%m-%d")
print(dt)  # 2024-12-25 00:00:00
```

## Date Arithmetic

```python
from datetime import date, timedelta

today = date.today()

# Add days
tomorrow = today + timedelta(days=1)
next_week = today + timedelta(weeks=1)
next_month = today + timedelta(days=30)

# Subtract days
yesterday = today - timedelta(days=1)

# Difference between dates
date1 = date(2024, 1, 1)
date2 = date(2024, 12, 31)
difference = date2 - date1
print(difference.days)  # 365
```
