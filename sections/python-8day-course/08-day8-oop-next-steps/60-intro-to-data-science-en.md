# Introduction to Data Science with Python

## What is Data Science?

**Data Science** is the field of extracting insights and knowledge from data using:

- **Statistics** - Understanding data patterns
- **Programming** - Processing and analyzing data
- **Domain knowledge** - Understanding the context
- **Visualization** - Communicating findings

Python is the leading language for data science!

## Why Python for Data Science?

- **Rich ecosystem** of libraries
- **Easy to learn** and read
- **Strong community** support
- **Integration** with other tools
- **Industry standard** for ML/AI

# The Data Science Stack

## Essential Libraries

| Library          | Purpose               | Use Case                    |
| ---------------- | --------------------- | --------------------------- |
| **NumPy**        | Numerical computing   | Arrays, math operations     |
| **Pandas**       | Data manipulation     | DataFrames, data cleaning   |
| **Matplotlib**   | Visualization         | Plots and charts            |
| **Seaborn**      | Statistical viz       | Beautiful statistical plots |
| **Scikit-learn** | Machine learning      | ML algorithms               |
| **Jupyter**      | Interactive notebooks | Exploratory analysis        |

## Installation

```bash
# Create virtual environment
python -m venv ds_env
source ds_env/bin/activate  # or ds_env\Scripts\activate

# Install data science libraries
pip install numpy pandas matplotlib seaborn scikit-learn jupyter

# Or install all at once
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

# NumPy: Numerical Computing

## What is NumPy?

**NumPy** (Numerical Python) provides:

- Fast array operations
- Mathematical functions
- Linear algebra
- Random number generation

## Basic NumPy

```python
import numpy as np

# Create arrays
arr1 = np.array([1, 2, 3, 4, 5])
arr2 = np.array([[1, 2, 3], [4, 5, 6]])

print(arr1)        # [1 2 3 4 5]
print(arr2.shape)  # (2, 3)

# Array operations (vectorized - fast!)
print(arr1 * 2)    # [2 4 6 8 10]
print(arr1 ** 2)   # [1 4 9 16 25]

# Statistical functions
print(arr1.mean())  # 3.0
print(arr1.std())   # 1.4142135623730951
print(arr1.sum())   # 15

# Generate data
zeros = np.zeros((3, 3))       # 3x3 array of zeros
ones = np.ones((2, 4))         # 2x4 array of ones
random = np.random.rand(5)     # 5 random numbers [0, 1)
range_arr = np.arange(0, 10, 2) # [0 2 4 6 8]
```

## Why NumPy is Fast

```python
import time
import numpy as np

# Python list
python_list = list(range(1000000))
start = time.time()
result = [x * 2 for x in python_list]
print(f"List: {time.time() - start:.4f}s")

# NumPy array
numpy_array = np.arange(1000000)
start = time.time()
result = numpy_array * 2
print(f"NumPy: {time.time() - start:.4f}s")

# NumPy is typically 10-100x faster!
```

# Pandas: Data Manipulation

## What is Pandas?

**Pandas** is built on NumPy and provides:

- **DataFrame** - Spreadsheet-like data structure
- **Series** - 1-dimensional labeled array
- Data cleaning and transformation
- Reading/writing various file formats

## DataFrame Basics

```python
import pandas as pd

# Create DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'Age': [25, 30, 35, 28],
    'City': ['New York', 'London', 'Paris', 'Tokyo'],
    'Salary': [70000, 80000, 75000, 72000]
}

df = pd.DataFrame(data)
print(df)

#       Name  Age      City  Salary
# 0    Alice   25  New York   70000
# 1      Bob   30    London   80000
# 2  Charlie   35     Paris   75000
# 3    Diana   28     Tokyo   72000

# Basic operations
print(df.head())           # First 5 rows
print(df.info())           # Data types and info
print(df.describe())       # Statistical summary

# Selecting data
print(df['Name'])          # Single column
print(df[['Name', 'Age']]) # Multiple columns
print(df[df['Age'] > 28])  # Filter rows
```

## Reading Data

```python
# Read from CSV
df = pd.read_csv('data.csv')

# Read from Excel
df = pd.read_excel('data.xlsx')

# Read from JSON
df = pd.read_json('data.json')

# Read from URL
url = 'https://example.com/data.csv'
df = pd.read_csv(url)
```

## Data Analysis Example

```python
import pandas as pd

# Create sample data
data = {
    'Product': ['A', 'B', 'C', 'A', 'B', 'C', 'A', 'B'],
    'Sales': [100, 150, 200, 120, 160, 190, 110, 155],
    'Region': ['East', 'East', 'West', 'West', 'East', 'West', 'East', 'West']
}

df = pd.DataFrame(data)

# Group by and aggregate
print(df.groupby('Product')['Sales'].mean())
# Product
# A    110.0
# B    155.0
# C    195.0

print(df.groupby('Region')['Sales'].sum())
# Region
# East    565
# West    585

# Multiple aggregations
print(df.groupby('Product').agg({
    'Sales': ['mean', 'sum', 'count']
}))
```

# Matplotlib: Data Visualization

## Basic Plotting

```python
import matplotlib.pyplot as plt
import numpy as np

# Line plot
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.title('Sine Wave')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.grid(True)
plt.show()

# Bar chart
categories = ['A', 'B', 'C', 'D']
values = [23, 45, 56, 78]

plt.bar(categories, values)
plt.title('Bar Chart')
plt.xlabel('Category')
plt.ylabel('Value')
plt.show()

# Scatter plot
x = np.random.rand(50)
y = np.random.rand(50)

plt.scatter(x, y, alpha=0.5)
plt.title('Scatter Plot')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()
```

## Pandas Integration

```python
import pandas as pd
import matplotlib.pyplot as plt

# Create DataFrame
df = pd.DataFrame({
    'Month': ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
    'Sales': [100, 120, 140, 130, 150]
})

# Plot directly from DataFrame
df.plot(x='Month', y='Sales', kind='line', figsize=(10, 6))
plt.title('Monthly Sales')
plt.ylabel('Sales ($)')
plt.show()

# Bar plot
df.plot(x='Month', y='Sales', kind='bar', figsize=(10, 6))
plt.title('Monthly Sales')
plt.ylabel('Sales ($)')
plt.show()
```

# Real-World Example: Sales Analysis

## Complete Data Analysis Workflow

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# 1. Create sample sales data
np.random.seed(42)
dates = pd.date_range('2024-01-01', periods=365)
sales = np.random.randint(100, 500, size=365) + np.sin(np.arange(365) / 50) * 50

df = pd.DataFrame({
    'Date': dates,
    'Sales': sales
})

# 2. Add derived columns
df['Month'] = df['Date'].dt.month
df['Weekday'] = df['Date'].dt.day_name()
df['Quarter'] = df['Date'].dt.quarter

# 3. Analysis
print("=== Overall Statistics ===")
print(f"Total Sales: ${df['Sales'].sum():,.2f}")
print(f"Average Daily Sales: ${df['Sales'].mean():.2f}")
print(f"Best Day: {df.loc[df['Sales'].idxmax(), 'Date'].date()} (${df['Sales'].max()})")

print("\n=== Sales by Month ===")
monthly = df.groupby('Month')['Sales'].agg(['sum', 'mean'])
print(monthly)

print("\n=== Sales by Weekday ===")
weekday = df.groupby('Weekday')['Sales'].mean().sort_values(ascending=False)
print(weekday)

# 4. Visualization
fig, axes = plt.subplots(2, 2, figsize=(15, 10))

# Daily sales
axes[0, 0].plot(df['Date'], df['Sales'])
axes[0, 0].set_title('Daily Sales')
axes[0, 0].set_xlabel('Date')
axes[0, 0].set_ylabel('Sales ($)')

# Monthly totals
monthly['sum'].plot(kind='bar', ax=axes[0, 1])
axes[0, 1].set_title('Monthly Total Sales')
axes[0, 1].set_xlabel('Month')
axes[0, 1].set_ylabel('Total Sales ($)')

# Weekday averages
weekday.plot(kind='bar', ax=axes[1, 0])
axes[1, 0].set_title('Average Sales by Weekday')
axes[1, 0].set_ylabel('Average Sales ($)')

# Sales distribution
axes[1, 1].hist(df['Sales'], bins=30, edgecolor='black')
axes[1, 1].set_title('Sales Distribution')
axes[1, 1].set_xlabel('Sales ($)')
axes[1, 1].set_ylabel('Frequency')

plt.tight_layout()
plt.show()
```

# Machine Learning Preview

## What is Machine Learning?

**Machine Learning** is teaching computers to learn from data without being explicitly programmed.

Types:

- **Supervised Learning** - Learn from labeled data (e.g., predict prices)
- **Unsupervised Learning** - Find patterns in unlabeled data (e.g., clustering)
- **Reinforcement Learning** - Learn through trial and error

## Simple ML Example with Scikit-learn

```python
from sklearn.linear_model import LinearRegression
import numpy as np
import matplotlib.pyplot as plt

# Generate sample data
X = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]).reshape(-1, 1)
y = np.array([2, 4, 5, 4, 5, 7, 8, 8, 9, 10])

# Create and train model
model = LinearRegression()
model.fit(X, y)

# Make predictions
predictions = model.predict(X)

# Visualize
plt.scatter(X, y, color='blue', label='Actual')
plt.plot(X, predictions, color='red', label='Predicted')
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Linear Regression')
plt.legend()
plt.show()

# Predict new values
new_X = np.array([[11], [12]])
new_predictions = model.predict(new_X)
print(f"Predictions for X=11, 12: {new_predictions}")
```

# Jupyter Notebooks

## What are Jupyter Notebooks?

**Jupyter** provides an interactive environment where you can:

- Write and execute code in cells
- Mix code with markdown documentation
- Visualize results inline
- Share reproducible analyses

## Starting Jupyter

```bash
# Activate your environment
source ds_env/bin/activate

# Start Jupyter
jupyter notebook

# Or JupyterLab (modern interface)
jupyter lab
```

This opens in your browser at `http://localhost:8888`

## Notebook Benefits

- **Interactive** - Run code cells independently
- **Documentation** - Mix code with explanations
- **Visualization** - See plots inline
- **Sharing** - Export to HTML, PDF
- **Exploratory** - Perfect for data analysis

# Next Steps in Data Science

## Learning Path

1. **Master the basics** (You are here!)
   - Python fundamentals
   - NumPy basics
   - Pandas basics

2. **Deep dive into libraries**
   - Advanced Pandas (pivoting, joining, time series)
   - Advanced visualization (Seaborn, Plotly)
   - NumPy linear algebra

3. **Statistics**
   - Descriptive statistics
   - Probability distributions
   - Hypothesis testing

4. **Machine Learning**
   - Supervised learning (regression, classification)
   - Unsupervised learning (clustering, dimensionality reduction)
   - Model evaluation and validation

5. **Specialized Topics**
   - Deep Learning (TensorFlow, PyTorch)
   - Natural Language Processing
   - Computer Vision
   - Time Series Analysis

## This Course Continues!

After completing this 8-day Python fundamentals course, you'll continue with:

- **Python Data Science Overview**
- **NumPy** - Complete coverage
- **Pandas** - Data manipulation mastery
- **Matplotlib/Pyplot** - Advanced visualization
- **Machine Learning Theory**
- **Supervised Learning with Scikit-learn**
- **Neural Networks with Keras**
- **Unsupervised Learning & Data Exploration**

# Resources for Data Science

## Essential Documentation

- **NumPy**: https://numpy.org/doc/
- **Pandas**: https://pandas.pydata.org/docs/
- **Matplotlib**: https://matplotlib.org/stable/contents.html
- **Scikit-learn**: https://scikit-learn.org/stable/
- **Jupyter**: https://jupyter.org/documentation

## Practice Datasets

- **Kaggle**: https://www.kaggle.com/datasets
- **UCI ML Repository**: https://archive.ics.uci.edu/ml/
- **Google Dataset Search**: https://datasetsearch.research.google.com/
- **Data.gov**: https://www.data.gov/

## Learning Platforms

- **Kaggle Learn**: Free micro-courses
- **DataCamp**: Interactive data science courses
- **Coursera**: University-level courses
- **Fast.ai**: Practical deep learning

# Quick Data Science Template

## Standard Analysis Workflow

```python
# 1. Import libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# 2. Load data
df = pd.read_csv('data.csv')

# 3. Explore data
print(df.head())
print(df.info())
print(df.describe())

# Check for missing values
print(df.isnull().sum())

# 4. Clean data
df = df.dropna()  # Remove missing values
# or
df = df.fillna(df.mean())  # Fill with mean

# 5. Analyze
# Correlations
print(df.corr())

# Group by analysis
print(df.groupby('Category')['Value'].agg(['mean', 'sum', 'count']))

# 6. Visualize
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
df['Column'].hist(bins=30)
plt.title('Distribution')

plt.subplot(1, 3, 2)
df.boxplot(column='Value', by='Category')
plt.title('Box Plot')

plt.subplot(1, 3, 3)
df.plot(kind='scatter', x='X', y='Y')
plt.title('Scatter Plot')

plt.tight_layout()
plt.show()

# 7. Save results
df.to_csv('results.csv', index=False)
```

## Key Takeaways

- Python is the leading language for data science
- NumPy provides fast numerical operations
- Pandas makes data manipulation easy
- Matplotlib creates visualizations
- Scikit-learn enables machine learning
- Jupyter notebooks are perfect for exploration
- The data science modules in this course will teach you everything in depth!
