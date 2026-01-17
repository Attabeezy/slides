# Development Environment

## Python Interactive Shell

The Python shell (REPL - Read-Eval-Print Loop) allows you to execute Python code interactively.

### Opening the Shell

```bash
python
# or
python3
```

### Using the Shell

```python
>>> 2 + 3
5
>>> print("Hello, World!")
Hello, World!
>>> name = "Python"
>>> print(f"I love {name}")
I love Python
```

### Exiting the Shell

```python
>>> exit()
# or press Ctrl+D (Linux/Mac) or Ctrl+Z then Enter (Windows)
```

## Visual Studio Code

VS Code is a popular, free code editor with excellent Python support.

### Installing VS Code

1. Download from [code.visualstudio.com](https://code.visualstudio.com/)
2. Install the application
3. Open VS Code

### Python Extension

1. Open VS Code
2. Click the Extensions icon (or press Ctrl+Shift+X)
3. Search for "Python"
4. Install the official Python extension by Microsoft

### Creating Your First Python File

1. Create a new folder for your project
2. Open the folder in VS Code (File → Open Folder)
3. Create a new file: `hello.py`
4. Write your code:

```python
print("Hello, World!")
```

5. Run the file:
   - Right-click in the editor → "Run Python File in Terminal"
   - Or press F5 to debug

## Python Files vs Shell

| Python Shell | Python Files (.py) |
|--------------|-------------------|
| Interactive | Saved scripts |
| One command at a time | Multiple lines executed |
| Good for testing | Good for projects |
| Results shown immediately | Need to use `print()` |

