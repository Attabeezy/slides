# Day 1 Exercises

## Level 1: Basics

1. **Check Python Version**
   - Open your terminal/command prompt
   - Run `python --version` or `python3 --version`
   - Take note of your Python version

2. **Python Shell Practice**
   - Open the Python interactive shell
   - Perform the following calculations:
     - `3 + 4`
     - `10 - 5`
     - `6 * 7`
     - `15 / 3`
     - `10 % 3` (modulus)
     - `2 ** 5` (exponentiation)
     - `17 // 5` (floor division)

3. **String Output**
   - In the Python shell, print the following strings:
     - Your name
     - Your country
     - "I am enjoying learning Python"

4. **Check Data Types**
   - Use `type()` to check the data types of:
     - `10`
     - `9.8`
     - `3.14`
     - `4 - 4j`
     - `['Python', 'Java', 'JavaScript']`
     - Your name (as a string)
     - Your country (as a string)

## Level 2: Variables and Operations

1. **Create Variables**
   - Create a file named `day1.py` in VS Code
   - Declare the following variables:
     - `first_name` - your first name
     - `last_name` - your last name
     - `full_name` - your full name
     - `country` - your country
     - `city` - your city
     - `age` - your age
     - `year` - current year
     - `is_married` - True or False
     - `is_true` - any boolean value
     - `is_light_on` - any boolean value

2. **Multiple Variables**
   - Declare multiple variables in one line:
     - `x, y, z = 5, 10, 15`

3. **Check Variable Types**
   - Use `type()` to check all your variables from exercise 1
   - Print each variable with its type

4. **Length Function**
   - Find the length of your first name using `len()`
   - Find the length of your last name
   - Compare: is your first name longer than your last name?

5. **Arithmetic Operations**
   - Declare `num_one = 5` and `num_two = 4`
   - Calculate and store the following:
     - `total = num_one + num_two`
     - `diff = num_one - num_two`
     - `product = num_one * num_two`
     - `division = num_one / num_two`
     - `remainder = num_two % num_one`
     - `exp = num_one ** num_two`
     - `floor_division = num_one // num_two`

## Level 3: Advanced

1. **Circle Calculations**
   - Create variables:
     - `radius = 30`
     - `pi = 3.14`
   - Calculate:
     - Area of circle: `pi * radius ** 2`
     - Circumference: `2 * pi * radius`
   - Print the results with descriptive messages

2. **User Input**
   - Use `input()` to get the following from a user:
     - First name
     - Last name
     - Country
     - Age
   - Store each in a variable and print them

3. **Type Conversions**
   - Create string variables: `"10"`, `"3.14"`, `"True"`
   - Convert them to appropriate types (int, float, bool)
   - Perform a calculation using the converted values

4. **Data Type Exploration**
   - Create one example of each data type:
     - Integer
     - Float
     - Complex number
     - String
     - Boolean
     - List
     - Tuple
     - Set
     - Dictionary
   - Print each with its type using `type()`

5. **Euclidean Distance**
   - Calculate the Euclidean distance between two points (2, 3) and (10, 8)
   - Formula: `distance = ((x2 - x1)**2 + (y2 - y1)**2) ** 0.5`
   - Print the result

## Bonus Challenge

Create a mini program that:
1. Asks for the user's name
2. Asks for their birth year
3. Calculates their age (current year - birth year)
4. Prints: "Hello [name], you are approximately [age] years old!"

**Hint:** You'll need `input()`, `int()`, and type conversion!

