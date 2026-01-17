# Introduction to Web Scraping

## What is Web Scraping?

**Web scraping** is the process of extracting data from websites.

Common use cases:

- Price monitoring
- News aggregation
- Research data collection
- Job listings
- Real estate data
- Social media analysis

**Important:** Always check a website's `robots.txt` and Terms of Service before scraping!

## Tools for Web Scraping

| Tool              | Purpose                            |
| ----------------- | ---------------------------------- |
| **requests**      | Send HTTP requests                 |
| **BeautifulSoup** | Parse HTML/XML                     |
| **lxml**          | Fast HTML/XML parser               |
| **Selenium**      | Automate browsers (for JavaScript) |
| **Scrapy**        | Full scraping framework            |

We'll focus on `requests` + `BeautifulSoup` - the most beginner-friendly combination.

# Setting Up

## Installation

```bash
# Create virtual environment (recommended)
python -m venv scraper_env
source scraper_env/bin/activate  # or scraper_env\Scripts\activate

# Install required packages
pip install requests beautifulsoup4 lxml
```

## Basic Imports

```python
import requests
from bs4 import BeautifulSoup
```

# Making HTTP Requests

## Using the requests Library

```python
import requests

# Send GET request
url = 'http://quotes.toscrape.com/'
response = requests.get(url)

# Check status code
print(response.status_code)  # 200 means success

# Get content
print(response.text)          # HTML as string
print(response.content)       # HTML as bytes

# Check if request was successful
if response.ok:
    print("Success!")
else:
    print(f"Error: {response.status_code}")
```

## HTTP Status Codes

| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 404  | Not Found    |
| 403  | Forbidden    |
| 500  | Server Error |

# Parsing HTML with BeautifulSoup

## Creating a Soup Object

```python
from bs4 import BeautifulSoup
import requests

url = 'http://quotes.toscrape.com/'
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Now soup contains the parsed HTML
print(type(soup))  # <class 'bs4.BeautifulSoup'>
```

## Basic HTML Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h1 class="heading">Welcome</h1>
    <p id="intro">This is a paragraph.</p>
    <div class="quote">
      <span class="text">"Quote here"</span>
      <span class="author">Author</span>
    </div>
  </body>
</html>
```

# Finding Elements

## Basic Selection Methods

```python
from bs4 import BeautifulSoup

html = '''
<html>
  <body>
    <h1>Title</h1>
    <p class="intro">First paragraph</p>
    <p class="content">Second paragraph</p>
    <a href="http://example.com">Link</a>
  </body>
</html>
'''

soup = BeautifulSoup(html, 'html.parser')

# Find first occurrence
h1 = soup.find('h1')
print(h1.text)  # Title

# Find by class
intro = soup.find('p', class_='intro')
print(intro.text)  # First paragraph

# Find by id
element = soup.find('div', id='main')

# Find all occurrences
all_paragraphs = soup.find_all('p')
for p in all_paragraphs:
    print(p.text)
```

## CSS Selectors

```python
# Select by tag
titles = soup.select('h1')

# Select by class
intro = soup.select('.intro')

# Select by id
main = soup.select('#main')

# Select nested elements
quotes = soup.select('div.quote span.text')

# Select with attribute
links = soup.select('a[href]')
```

# Extracting Data

## Getting Text and Attributes

```python
from bs4 import BeautifulSoup
import requests

url = 'http://quotes.toscrape.com/'
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Find a quote
quote = soup.find('span', class_='text')

# Get text content
print(quote.text)           # The quote text
print(quote.get_text())     # Same as .text

# Get attributes
link = soup.find('a')
print(link['href'])         # Get href attribute
print(link.get('href'))     # Alternative method

# Check if attribute exists
if link.has_attr('href'):
    print("Link has href")
```

# Real-World Example: Scraping Quotes

## Complete Scraper

```python
import requests
from bs4 import BeautifulSoup

def scrape_quotes(url='http://quotes.toscrape.com/'):
    """Scrape quotes from quotes.toscrape.com"""

    # Send request
    response = requests.get(url)

    if not response.ok:
        print(f"Error: {response.status_code}")
        return []

    # Parse HTML
    soup = BeautifulSoup(response.text, 'html.parser')

    # Find all quote containers
    quote_divs = soup.find_all('div', class_='quote')

    quotes = []
    for div in quote_divs:
        # Extract quote text
        text = div.find('span', class_='text').text

        # Extract author
        author = div.find('small', class_='author').text

        # Extract tags
        tags = [tag.text for tag in div.find_all('a', class_='tag')]

        quotes.append({
            'text': text,
            'author': author,
            'tags': tags
        })

    return quotes

# Use the scraper
quotes = scrape_quotes()

for i, quote in enumerate(quotes, 1):
    print(f"\n{i}. {quote['text']}")
    print(f"   - {quote['author']}")
    print(f"   Tags: {', '.join(quote['tags'])}")
```

# Handling Pagination

## Scraping Multiple Pages

```python
import requests
from bs4 import BeautifulSoup
import time

def scrape_all_pages(base_url='http://quotes.toscrape.com'):
    """Scrape quotes from all pages"""

    all_quotes = []
    page = 1

    while True:
        url = f"{base_url}/page/{page}/"
        print(f"Scraping page {page}...")

        response = requests.get(url)

        if not response.ok:
            break

        soup = BeautifulSoup(response.text, 'html.parser')
        quote_divs = soup.find_all('div', class_='quote')

        if not quote_divs:
            break

        for div in quote_divs:
            text = div.find('span', class_='text').text
            author = div.find('small', class_='author').text
            all_quotes.append({'text': text, 'author': author})

        # Check for next button
        next_btn = soup.find('li', class_='next')
        if not next_btn:
            break

        page += 1
        time.sleep(1)  # Be polite - don't hammer the server

    return all_quotes

quotes = scrape_all_pages()
print(f"Scraped {len(quotes)} quotes")
```

# Saving Scraped Data

## To CSV

```python
import csv

def save_to_csv(quotes, filename='quotes.csv'):
    """Save quotes to CSV file"""

    with open(filename, 'w', newline='', encoding='utf-8') as file:
        writer = csv.DictWriter(file, fieldnames=['text', 'author'])
        writer.writeheader()
        writer.writerows(quotes)

    print(f"Saved {len(quotes)} quotes to {filename}")

# Usage
quotes = scrape_quotes()
save_to_csv(quotes)
```

## To JSON

```python
import json

def save_to_json(quotes, filename='quotes.json'):
    """Save quotes to JSON file"""

    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(quotes, file, indent=4, ensure_ascii=False)

    print(f"Saved {len(quotes)} quotes to {filename}")

# Usage
quotes = scrape_quotes()
save_to_json(quotes)
```

# Best Practices

## Ethical Scraping

1. **Check robots.txt**

   ```
   http://example.com/robots.txt
   ```

2. **Read Terms of Service**
   - Some sites prohibit scraping

3. **Be polite**

   ```python
   import time
   time.sleep(1)  # Wait between requests
   ```

4. **Use User-Agent**

   ```python
   headers = {
       'User-Agent': 'Mozilla/5.0 (compatible; MyBot/1.0)'
   }
   response = requests.get(url, headers=headers)
   ```

5. **Handle errors gracefully**
   ```python
   try:
       response = requests.get(url, timeout=10)
       response.raise_for_status()
   except requests.exceptions.RequestException as e:
       print(f"Error: {e}")
   ```

# Error Handling

## Common Issues and Solutions

```python
import requests
from bs4 import BeautifulSoup
import time

def safe_scrape(url, retries=3):
    """Scrape with error handling and retries"""

    for attempt in range(retries):
        try:
            # Set timeout
            response = requests.get(url, timeout=10)

            # Check status
            response.raise_for_status()

            # Parse HTML
            soup = BeautifulSoup(response.text, 'html.parser')
            return soup

        except requests.exceptions.Timeout:
            print(f"Timeout on attempt {attempt + 1}")

        except requests.exceptions.HTTPError as e:
            print(f"HTTP Error: {e}")
            break

        except requests.exceptions.RequestException as e:
            print(f"Error: {e}")

        # Wait before retry
        if attempt < retries - 1:
            time.sleep(2 ** attempt)  # Exponential backoff

    return None

# Usage
soup = safe_scrape('http://quotes.toscrape.com/')
if soup:
    quotes = soup.find_all('div', class_='quote')
    print(f"Found {len(quotes)} quotes")
```

# Advanced: Dynamic Content (JavaScript)

## When BeautifulSoup Isn't Enough

Some websites load content with JavaScript. For these, you need Selenium:

```python
# Installation: pip install selenium
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Setup (requires browser driver)
driver = webdriver.Chrome()

try:
    # Load page
    driver.get('http://example.com')

    # Wait for element to load
    element = WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.CLASS_NAME, 'quote'))
    )

    # Find elements
    quotes = driver.find_elements(By.CLASS_NAME, 'quote')

    for quote in quotes:
        text = quote.find_element(By.CLASS_NAME, 'text').text
        print(text)

finally:
    driver.quit()
```

# Quick Reference

## BeautifulSoup Methods

```python
soup.find('tag')                    # First occurrence
soup.find_all('tag')                # All occurrences
soup.find('tag', class_='name')     # Find by class
soup.find('tag', id='name')         # Find by id
soup.find('tag', attrs={'key': 'value'})  # Find by attribute

soup.select('tag')                  # CSS selector
soup.select('.class')               # By class
soup.select('#id')                  # By id
soup.select('tag.class')            # Tag with class

element.text                        # Get text
element.get_text()                  # Get text
element['attr']                     # Get attribute
element.get('attr')                 # Get attribute (safe)
element.has_attr('attr')            # Check attribute exists
```

## Complete Scraper Template

```python
import requests
from bs4 import BeautifulSoup
import time
import json

def scrape_website(url):
    """Template for web scraping"""

    try:
        # 1. Send request with headers
        headers = {'User-Agent': 'Mozilla/5.0'}
        response = requests.get(url, headers=headers, timeout=10)
        response.raise_for_status()

        # 2. Parse HTML
        soup = BeautifulSoup(response.text, 'html.parser')

        # 3. Extract data
        items = []
        for element in soup.find_all('div', class_='item'):
            item = {
                'title': element.find('h2').text.strip(),
                'link': element.find('a')['href']
            }
            items.append(item)

        # 4. Save data
        with open('data.json', 'w') as f:
            json.dump(items, f, indent=4)

        return items

    except Exception as e:
        print(f"Error: {e}")
        return []

    finally:
        time.sleep(1)  # Be polite

# Usage
data = scrape_website('http://example.com')
print(f"Scraped {len(data)} items")
```
