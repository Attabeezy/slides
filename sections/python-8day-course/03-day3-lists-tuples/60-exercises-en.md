# Day 3 Exercises

## Level 1: Lists Basics

1. **Create and Access Lists**
   - Create an empty list called `my_list`
   - Create a list of 5 fruits
   - Get the first, middle, and last fruit from the list
   - Print the length of the list

2. **List Operations**
   - Create a list: `numbers = [1, 2, 3, 4, 5]`
   - Change the first item to 10
   - Change the last item to 50
   - Print the modified list

3. **List Methods**
   - Create a list: `colors = ['red', 'blue', 'green']`
   - Add 'yellow' to the end
   - Insert 'purple' at index 1
   - Remove 'blue' from the list
   - Print the final list

4. **Slicing Practice**
   - Create a list: `numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`
   - Get the first 5 numbers
   - Get the last 3 numbers
   - Get every other number
   - Reverse the list using slicing

5. **Tuple Basics**
   - Create a tuple with 3 items
   - Access the first and last items
   - Try to change an item (observe the error)
   - Convert the tuple to a list, modify it, then convert back

## Level 2: Intermediate Operations

1. **List Manipulation**
   - Create two lists: `list1 = [1, 2, 3]` and `list2 = [4, 5, 6]`
   - Combine them using concatenation
   - Combine them using `extend()`
   - What's the difference?

2. **Sorting and Reversing**
   - Create a list: `numbers = [5, 2, 9, 1, 7, 6, 3]`
   - Sort it in ascending order
   - Sort it in descending order
   - Create a new sorted list without modifying original

3. **List Comprehension**
   - Create a list of squares from 1 to 10 using list comprehension
   - Create a list of even numbers from 0 to 20
   - Convert a list of strings to uppercase using comprehension

4. **Finding and Counting**
   - Create a list: `items = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']`
   - Count how many times 'apple' appears
   - Find the index of the first 'banana'
   - Remove all occurrences of 'apple' (hint: use a loop or comprehension)

5. **Tuple Operations**
   - Create two tuples and concatenate them
   - Create a tuple and repeat it 3 times
   - Unpack a tuple of 4 items into 4 variables
   - Try unpacking with `*rest` for remaining items

## Level 3: Advanced Challenges

1. **Shopping List Manager**
   Create a program that:
   - Starts with an empty shopping list
   - Adds items: 'milk', 'bread', 'eggs', 'cheese'
   - Removes 'bread'
   - Inserts 'butter' after 'milk'
   - Prints the final list
   - Prints the list in alphabetical order (without modifying original)

2. **Number Analysis**
   Given: `numbers = [45, 67, 23, 89, 12, 56, 90, 34, 78]`
   - Find the maximum and minimum values
   - Calculate the sum and average
   - Create a new list with only numbers greater than 50
   - Sort and print the top 3 numbers

3. **List Comprehension Challenges**
   - Create a list of numbers from 1-100 that are divisible by both 3 and 5
   - Given `words = ['hello', 'world', 'python', 'programming']`, create a list of word lengths
   - Create a list of tuples pairing numbers with their squares: `[(1,1), (2,4), (3,9), ...]` for 1-10

4. **Nested Lists (Matrix)**
   ```python
   matrix = [
       [1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]
   ]
   ```
   - Access the center element (5)
   - Get the first row
   - Get the last column as a list
   - Flatten the matrix into a single list

5. **Student Grades**
   Create a program that:
   - Has a list of student names: `['Alice', 'Bob', 'Charlie', 'Diana']`
   - Has a list of their scores: `[85, 92, 78, 95]`
   - Creates a list of tuples pairing names with scores
   - Finds the student with the highest score
   - Calculates the class average
   - Lists students who scored above 80

6. **List Copying**
   ```python
   original = [1, 2, 3, 4, 5]
   ```
   - Create a shallow copy using `.copy()`
   - Create a copy using slicing
   - Create a copy using `list()`
   - Create a reference (not a copy) and modify it
   - Explain what happens in each case

7. **Tuple Unpacking Advanced**
   ```python
   data = (('Alice', 25), ('Bob', 30), ('Charlie', 35))
   ```
   - Unpack the first tuple
   - Use a loop to unpack all tuples and print: "Name is Age years old"
   - Convert to a dictionary with names as keys and ages as values

8. **Remove Duplicates**
   ```python
   numbers = [1, 2, 3, 2, 4, 1, 5, 3, 6, 4]
   ```
   - Remove duplicates while preserving order
   - Create a new list with unique items only
   - Hint: Use a loop or list comprehension with a condition

9. **Common Elements**
   ```python
   list1 = [1, 2, 3, 4, 5]
   list2 = [4, 5, 6, 7, 8]
   ```
   - Find elements common to both lists
   - Find elements only in list1
   - Find elements only in list2
   - Use list comprehension

10. **List Rotation**
    ```python
    items = [1, 2, 3, 4, 5]
    ```
    - Rotate the list right by 2 positions: `[4, 5, 1, 2, 3]`
    - Rotate left by 2 positions: `[3, 4, 5, 1, 2]`
    - Use slicing

## Bonus Challenges

1. **Fibonacci Sequence**
   - Generate the first 10 Fibonacci numbers in a list
   - Use a loop to build the list
   - Fibonacci: `[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]`

2. **Prime Numbers**
   - Create a list of all prime numbers between 1 and 50
   - Use list comprehension with a helper function

3. **Palindrome Checker**
   - Given a list of words, filter only palindromes
   - Example: `['radar', 'hello', 'level', 'world', 'noon']`
   - Result: `['radar', 'level', 'noon']`

4. **Merge Sorted Lists**
   - Given two sorted lists:
     ```python
     list1 = [1, 3, 5, 7]
     list2 = [2, 4, 6, 8]
     ```
   - Merge them into one sorted list: `[1, 2, 3, 4, 5, 6, 7, 8]`
   - Don't use `sort()` - merge them manually

5. **Chunk List**
   - Given: `numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]`
   - Split into chunks of size 3: `[[1,2,3], [4,5,6], [7,8,9]]`
   - Make it work for any chunk size

