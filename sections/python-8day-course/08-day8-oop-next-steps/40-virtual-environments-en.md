# Virtual Environments

## What is a Virtual Environment?

A **virtual environment** is an isolated Python environment that allows you to:

- Install packages for specific projects
- Avoid conflicts between project dependencies
- Keep your system Python clean
- Share reproducible environments

Think of it as a separate "workspace" for each project.

## Why Use Virtual Environments?

**Problem without virtual environments:**

```
Project A needs Django 3.2
Project B needs Django 4.0
System Python can only have one version!
```

**Solution with virtual environments:**

```
Project A → venv_a → Django 3.2
Project B → venv_b → Django 4.0
Both can coexist!
```

# Creating a Virtual Environment

## Using `venv` (Built-in)

```bash
# Create a virtual environment
python -m venv myenv

# Or specify Python version
python3 -m venv myenv
```

This creates a directory `myenv` containing:

- Python interpreter
- pip package manager
- Standard library
- Site-packages directory (for installed packages)

## Directory Structure

```
myenv/
├── Scripts/        (Windows)
│   ├── python.exe
│   ├── pip.exe
│   └── activate.bat
├── bin/            (Linux/Mac)
│   ├── python
│   ├── pip
│   └── activate
├── Lib/            (Installed packages)
└── Include/
```

# Activating and Deactivating

## Windows

```bash
# Activate
myenv\Scripts\activate

# Your prompt changes to:
(myenv) C:\Users\YourName\project>

# Deactivate
deactivate
```

## Linux/Mac

```bash
# Activate
source myenv/bin/activate

# Your prompt changes to:
(myenv) user@machine:~/project$

# Deactivate
deactivate
```

## Verification

```bash
# Check which Python is being used
which python    # Linux/Mac
where python    # Windows

# Check Python version
python --version

# Check installed packages
pip list
```

# Installing Packages in Virtual Environment

## Using pip

```bash
# Activate your virtual environment first!
source myenv/bin/activate  # or myenv\Scripts\activate on Windows

# Install a package
pip install requests

# Install specific version
pip install requests==2.28.0

# Install multiple packages
pip install requests numpy pandas

# Upgrade a package
pip install --upgrade requests

# Uninstall a package
pip uninstall requests
```

# Managing Dependencies

## requirements.txt

**Save your dependencies:**

```bash
# Generate requirements file
pip freeze > requirements.txt
```

Example `requirements.txt`:

```
requests==2.28.1
numpy==1.23.4
pandas==1.5.0
beautifulsoup4==4.11.1
```

**Install from requirements:**

```bash
# Install all packages from requirements.txt
pip install -r requirements.txt
```

This is essential for:

- Sharing projects with others
- Deploying to servers
- Reproducing environments

# Practical Workflow

## Step-by-Step Project Setup

```bash
# 1. Create project directory
mkdir my_project
cd my_project

# 2. Create virtual environment
python -m venv venv

# 3. Activate it
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# 4. Install packages
pip install requests beautifulsoup4

# 5. Save dependencies
pip freeze > requirements.txt

# 6. Work on your project
# ... create your Python files ...

# 7. Deactivate when done
deactivate
```

## Sharing Your Project

```bash
# Include in your project repository:
my_project/
├── venv/              # DON'T commit this to git!
├── requirements.txt   # DO commit this
├── main.py
└── README.md

# Add to .gitignore:
venv/
__pycache__/
*.pyc
```

# Real-World Example

## Setting Up a Web Scraping Project

```bash
# Create and activate environment
python -m venv scraper_env
source scraper_env/bin/activate  # or scraper_env\Scripts\activate

# Install required packages
pip install requests beautifulsoup4 lxml pandas

# Save dependencies
pip freeze > requirements.txt

# Create your scraper
cat > scraper.py << 'EOF'
import requests
from bs4 import BeautifulSoup
import pandas as pd

def scrape_quotes():
    url = 'http://quotes.toscrape.com/'
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    quotes = []
    for quote in soup.find_all('div', class_='quote'):
        text = quote.find('span', class_='text').text
        author = quote.find('small', class_='author').text
        quotes.append({'quote': text, 'author': author})

    df = pd.DataFrame(quotes)
    print(df)

if __name__ == '__main__':
    scrape_quotes()
EOF

# Run your scraper
python scraper.py

# When done
deactivate
```

# Alternative: virtualenv and virtualenvwrapper

## virtualenv (Third-party)

```bash
# Install virtualenv
pip install virtualenv

# Create environment
virtualenv myenv

# Activate (same as venv)
source myenv/bin/activate
```

## virtualenvwrapper (Advanced)

Makes managing multiple environments easier:

```bash
# Install
pip install virtualenvwrapper

# Create environment
mkvirtualenv project1

# Switch between environments
workon project1
workon project2

# List all environments
lsvirtualenv

# Delete environment
rmvirtualenv project1
```

# Modern Alternative: Poetry

## What is Poetry?

Poetry is a modern dependency management tool that:

- Manages virtual environments automatically
- Resolves dependency conflicts
- Builds and publishes packages

## Quick Start

```bash
# Install Poetry
curl -sSL https://install.python-poetry.org | python3 -

# Create new project
poetry new my_project

# Or initialize in existing directory
poetry init

# Add dependencies
poetry add requests

# Install dependencies
poetry install

# Run Python in the environment
poetry run python script.py

# Activate the environment
poetry shell
```

## pyproject.toml

Poetry uses `pyproject.toml` instead of `requirements.txt`:

```toml
[tool.poetry]
name = "my-project"
version = "0.1.0"
description = ""

[tool.poetry.dependencies]
python = "^3.9"
requests = "^2.28.0"
beautifulsoup4 = "^4.11.0"

[tool.poetry.dev-dependencies]
pytest = "^7.0"
```

# Best Practices

## Virtual Environment Tips

1. **One environment per project**
   - Keep projects isolated
   - Avoid dependency conflicts

2. **Name it consistently**
   - Use `venv`, `.venv`, or `env`
   - Easy to recognize and .gitignore

3. **Never commit venv to version control**

   ```gitignore
   # .gitignore
   venv/
   .venv/
   env/
   ENV/
   ```

4. **Always use requirements.txt**
   - Document your dependencies
   - Makes setup reproducible

5. **Update regularly**
   ```bash
   pip list --outdated
   pip install --upgrade package_name
   ```

# Common Issues and Solutions

## Troubleshooting

| Issue                            | Solution                                |
| -------------------------------- | --------------------------------------- |
| `pip` not found after activation | Deactivate and reactivate               |
| Permission denied                | Don't use `sudo` with virtual env       |
| Wrong Python version             | Specify: `python3.9 -m venv venv`       |
| Can't activate on Windows        | Run: `Set-ExecutionPolicy RemoteSigned` |
| Packages not found               | Ensure venv is activated                |

## Checking Your Environment

```python
# Check if in virtual environment
import sys
print(sys.prefix)  # Should show your venv path

# Check installed packages
import pkg_resources
installed = [pkg.key for pkg in pkg_resources.working_set]
print(installed)
```

# Quick Reference

## Essential Commands

```bash
# Create
python -m venv venv

# Activate
source venv/bin/activate      # Linux/Mac
venv\Scripts\activate         # Windows

# Install packages
pip install package_name
pip install -r requirements.txt

# Save dependencies
pip freeze > requirements.txt

# Deactivate
deactivate

# Remove (just delete the directory)
rm -rf venv                   # Linux/Mac
rmdir /s venv                 # Windows
```

## Workflow Summary

```bash
1. Create:     python -m venv venv
2. Activate:   source venv/bin/activate
3. Install:    pip install -r requirements.txt
4. Develop:    # work on your code
5. Save:       pip freeze > requirements.txt
6. Deactivate: deactivate
```
