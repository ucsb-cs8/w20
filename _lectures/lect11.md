---
num: Lec 11
lecture_date: 2020-02-10
desc:
ready: false
pdfurl:
---

# Lecture 11: File I/O + Binary Numbers

## Feedback from this week's lab:
- Confused with `pytest`, please provide additional examples in the lab.
    - Look back at previous labs!
    - Look at the homework for using `pytest` with a list
    - There will be `pytest` examples in this week's lab
- Liked a more practical lab! (:

## Announcements

### HW07
- Due Sat 2/15 at 11 am
- https://ucsb-cs8.github.io/w20/work_list
- HW 1-4 replacement assignment
- Will be released a little later

### No Common Final
- Will be defaulting to times scheduled on Gold

# Review

+ `range()`
+ `while` loops
    - a **condition-controlled loop** that repeats while condition is true
    - syntax:
    ```python
    while CONDITION:
        # loop body
    ```
+ `for` loops
    - a **count-controlled loop** that repeats a specified number of times
    - syntax:
    ```python
    for VAR in COLLECTION:
        # loop body
        One or more statements
   ```
- For both loops, anything on the same indentation as the for and while statement will be executed when the loop ends
- `continue` will get you out of the loop that you are in and will recheck the condition
- `break` takes us out of the loop that it is in
    - example:
    ```python
    For loop
        While loop
        # Statments
        Break
        # Statements
    ```
        - Break will get us out of the while loop, **not** the for loop!
        
## What is the output of this code?
```python
for x in range(1, 4, 2):
    print (2**x, end = " "
```
Output: 2 8

### Answer explained:
- range(starting point, ending point, step-size)
- `range(1, 4, 2)` evaluates to 1, and 3
- `2**x` raises 2 to the power of x
- `print(2**x, end = " "` prints 2 to the power of 1 and 2 to the power of 3
    - Thus, the ouput is 2 8
    
## What does `end = " "` do?

- python puts a new line at the end of a printed value as a defaults 
- We are overwriting the default, and setting the end as a space 
- Similarly, python puts a space between printed value as a default. So, `sep = ` overwrites the default separator

## Starting iteration using `range()`

```python
start = 2
end = 9
step = 3
for i in range(start, end, step):
    print i
```
- i defaults as the start value, then increases by the step value, and the for loop will continue to execute while i < end

## String iteration

```python
s = "Hi there!"
for c in s:
    print(c) # prints the characters in s
    
for i in range(len(s)):
    print (i) # prints the indicies of the letters in s
```

### Indexing a string

```python
for i in range(len(s)):
    print(s[i]) # prints each letter in s
```

# File I/O

## Opening and reading

- We will be opening and reading text files.

```python
fobj = open("info.txt") # Open "info.txt"
content = fobj.readlines() 
fobj.close() # Close "info.txt"
```

- Get in the habit of closing files!
- **Note:** python has a way to open a file without having to close it, but we will not be using that method in this class!
- `.readlines()` reads a bunch of lines that python gets from this file and stores it as a list
    - The output is a list with all the lines of text in the file
- `open()` opens the filename passed inside 
    - Returns a file object that is connected to the file, we get to name the object
    
- Does this only work for text files?
    - No! Works with any file 
    - Will be able to open it but may not succeed to get the contents inside the file
    
## Opening and writing

- Write contents produced back into a different file.

```python
fobj = open("info.txt", "w") # "w" is a write flag that says we will overwrite any contents in file 
content = fobj.write()
fobj.close()
```

- `.write()` tells file object what we want to write
    - Arguement must be a string 

## Demo

```python
fobj = open("sample_file.txt", "w")

for x in range(1, 4, 2):
    fobj.write(str(2**x) + " ")

fobj.close
```

Output: contents in "sample_file.txt" are changed. Now the file contains: 2 8

```python
fobj = open("sample_file.txt", "a") # "a" is an append flag that says we will add to any contents in file 

for x in range(1, 4, 2):
    fobj.write(str(2**x) + " ")

fobj.close
```

Output: 2 8 is added to contents in "sample_file.txt"

Can be tedious to open  file every time, so we can store the contents in the file in a variable.

```python
fobj = open("sample_file.txt", "r") # "r" is an read flag that reads the contents in file 

contents = fobj.readlines() # Store file object in a list variable 

fobj.close

print(contents)

for line in contents:
    print(line) # Print each line separately instead of as a list
```

Another example:

```python
file_obj = open("another_sample.txt")

message = file_obj.readlines() # Each line in another_sample.txt is an element in the list, message

for line in message:
    print(line, end = "") # Prints each element in message
    
# Could also print each element in message using indexing explicitly:
for i in range(len(message)):
    print(message[i], end = "")
    
print("Contents of message:", message) # Prints message as a list
```

# Looking forward to next topic:

This is how we count:

- 00
- 01
- 02
- 03
- ..
- 08
- 09
- 10
- 11
- 12
- 13
- ...
- 18
- 19
- 20
- 21

In Binary, we only have two digits: 0 and 1

- 00 --> 00
- 01 --> 01
- 10 --> 02
- 11 --> 03
- 100 --> 04

We will be writing a function where given a string, we will confirm if this is a binary string or not (contains only binary characters)


```python
def only_binary(input_str):
    """
    If input_str has only 1s and 0s 
        return True
    Otherwise,
        return False
    """

    for char in input_str:
        if char != '1' or char != '0':
            return False
    return "stub"
```


```python
only_binary('1')
```
    False

```python
only_binary('0')
```
    False

Hmmm, not what we expected. 
**Debugging skill:** any time your function is not acting as expected, use the simplest possible input to see what is happening.


```python
def only_binary(input_str):
    """
    If input_str has only 1s and 0s 
        return True
    Otherwise,
        return False
    """

    for char in input_str:
        if char != '1' and char != '0': # Notice we changed OR to an AND
            return False
    return True
```


```python
only_binary('1')
```
    True

```python
only_binary('0')
```
    True

Now that our function is working properly, we can give it more complicated inputs.


```python
only_binary('1011')
```
    True

```python
only_binary('10171')
```
    False


