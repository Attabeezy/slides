# Day 2 Exercises

## Level 1: Operators

1. **Arithmetic Operations**
   - Declare two variables: `num1 = 15` and `num2 = 4`
   - Calculate and print:
     - Addition
     - Subtraction
     - Multiplication
     - Division
     - Modulus
     - Floor division
     - Exponentiation

2. **Comparison Practice**
   - Use comparison operators to check:
     - Is 10 greater than 5?
     - Is 10 less than 20?
     - Is 10 equal to 10?
     - Is 5 not equal to 10?
     - Is `len("Python")` equal to 6?

3. **Logical Operators**
   - Evaluate these expressions:
     - `True and False`
     - `True or False`
     - `not True`
     - `(5 > 3) and (10 < 20)`
     - `(5 > 10) or (20 > 15)`

4. **Temperature Converter**
   - Create a variable `celsius = 30`
   - Convert to Fahrenheit: `(celsius * 9/5) + 32`
   - Print: "30°C is X°F"

# Day 2 Exercises - Level 2

1. **String Creation**
   - Create a variable `company = "Coding For All"`
   - Print the string
   - Print its length using `len()`
   - Convert to uppercase
   - Convert to lowercase
   - Use `capitalize()`, `title()`, and `swapcase()`

2. **String Slicing**
   - Using the string "Python Programming":
     - Extract "Python"
     - Extract "Programming"
     - Get the first character
     - Get the last character
     - Reverse the entire string

3. **String Methods**
   - Using the string "Coding For All":
     - Check if it contains "Coding" using `in`
     - Replace "Coding" with "Python"
     - Split it into a list of words
     - Check if it starts with "Coding"
     - Check if it ends with "All"

4. **String Formatting**
   - Create variables: `name = "Alice"`, `age = 25`, `city = "Boston"`
   - Use f-strings to print: "My name is Alice, I am 25 years old, and I live in Boston"
   - Use .format() to print the same message
   - Use % operator to print the same message

# Day 2 Exercises - Level 3

1. **Calculator Program**
   - Get two numbers from user input
   - Convert them to integers
   - Calculate and display:
     - Sum
     - Difference
     - Product
     - Division
     - Modulus
   - Use f-strings for formatted output

2. **Area Calculations**
   - Write code to calculate and display:
     - Area of a circle (radius = 10, pi = 3.14)
     - Area of a rectangle (length = 15, width = 8)
     - Area of a triangle (base = 20, height = 10, area = 0.5 * base * height)
   - Format output with 2 decimal places

3. **String Analyzer**
   - Create a program that:
     - Takes a sentence as input
     - Counts vowels (a, e, i, o, u)
     - Counts consonants
     - Prints the results
   - Hint: Use `.lower()` and `count()`

4. **Name Formatter**
   - Get first name and last name from user
   - Display:
     - Full name
     - Initials (e.g., "John Doe" → "J.D.")
     - Email address (e.g., "john.doe@example.com")
     - Username (e.g., "john_doe")

5. **String Operations Challenge**
   ```python
   sentence = "You cannot end a sentence with because because because is a conjunction"
   ```
   - Find the position of the first "because"
   - Find the position of the last "because"
   - Extract the phrase "because because because"
   - Replace all "because" with "BECAUSE"
   - Count how many times "because" appears

6. **Format Table**
   - Use string formatting to create:
   ```
   Name        Age    City         
   ================================
   Alice       25     Boston       
   Bob         30     New York     
   Charlie     35     Seattle      
   ```
   - Use f-strings with alignment (ljust, rjust, or format specifiers)

7. **Membership and Identity**
   - Create two list variables: `list1 = [1, 2, 3]` and `list2 = [1, 2, 3]`
   - Create `list3 = list1`
   - Compare using:
     - `==` operator
     - `is` operator
   - Explain the difference in results

8. **Boolean Logic**
   - Create a program that checks if a year is a leap year:
     - Divisible by 4 AND (not divisible by 100 OR divisible by 400)
   - Test with years: 2000, 1900, 2024, 2023

# Day 2 Bonus Challenges

1. **Acronym Generator**
   - Input: "Python For Everyone"
   - Output: "PFE"
   - Hint: Split the string, take first letter of each word, join them

2. **String Reversal**
   - Create multiple ways to reverse a string:
     - Using slicing
     - Using a loop
     - Using `reversed()` function

3. **Password Validator**
   - Check if a password string:
     - Has at least 8 characters
     - Contains at least one digit
     - Contains at least one uppercase letter
     - Contains at least one lowercase letter
   - Use string methods: `isdigit()`, `isupper()`, `islower()`

4. **Mathematical Expressions**
   - Using `a = 8` and `b = 6`, create formatted output:
   ```
   8 + 6 = 14
   8 - 6 = 2
   8 * 6 = 48
   8 / 6 = 1.33
   8 % 6 = 2
   8 // 6 = 1
   8 ** 6 = 262144
   ```
   - Use f-strings with proper formatting

