---
num: Lec19
lecture_date: 2020-03-09
desc: Review
ready: true
---
* Algorithm: a solution to a problem, typically written in a human-understandable language(pseudocode)

* Pay attention to conditionals!

* You can find the list of the UCSB major/minor codes here: <https://registrar.sa.ucsb.edu/faculty-staff/resources-for-faculty-staff/major-minor-codes>

```python
ucsb_majors = {}
try:
  infile = open("major_codes.txt")
except:
  print("This files does not exist.")
  print("ERROR:", err)
else:
  for line infile:
    # line = line.split('\t').strip() #strip the white space
    line_to_write = line
    line = line.strip() # remove white psace
    line = line.splot('\t')
    # print("Key = ", line[0].strip()
    key = line[0].strip() # make sure there's no extra white space
    # ucsb_majors[key] = line[1]
    if ucsb_major.get(key) != None:
      print(line)
      ucsb_majors[key] = line[1]
      continue
    else:
      outfile.write(line_to_write)
    
    print(line)
infile.close()
outfile.close()
```
# What is Computer Science?

What is the other component of Computer Science?

Pseudo code!
- gives the "algorithm": sequence of steps to solve a problem

# Roadmap

What are the basic elements of programming?
1. Pseudocode/Algorithm
2. Basic Data Types
    - This forces you to care about syntax!
    - `int` and `float`
        - Allow you to do arithmetic ==> `+`, `-`, `**`, `//`, `/`, `%`, `*`
    - `bool`
        - `if`/`else`/`elif`
            - `==` and `!=`
        - Flow of elements
    - `string`
        - Indexing
        - `len` and `print`
3. Functions!
    - Parameters
        - The name I have in a parameter is different than what I actually use inside the function
    - These will be a **huge** component on the final exam....
    - `pytest`, `assert`
        - Verifies the correctness of code
4. More complex data types
    - Lists
        - `len` and indexing now apply to lists
        - plot (not going to be on the exam)
    - Tuples
        - Mutability
        - Named tuples
            - Will definitely be on the final!!
Indexing gave us...
5. Loops!
    - `while` loop
        - `range()`
    - `for` loop
        - Anything you can do with a while loop you can do with a for loop (without infinite loops)!
6. Recursion
    - Call our function within its definition
7. Dictionaries
    - Will definitely be on the final!!
8. File I/O
    - Reading in our data to store complex data types
    - Writing out files into a file
    
Consider making a similar concept map while studying!

# Practice Algorithm

Exceptions won't be on the exam, but it's still good to know for your future projects.

We can use `try` to tell python that a line of code *may* cause an error. This prevents your code from crashing, giving you a way to gracefully handle the exception.

For example,
```python
try:
    infile = open("major_codes.txt")
except FileNotFoundError as err:
    print("No such file exists.")
    print("ERROR:", err) 
else:
    ucsb_majors = {}
    for line in infile: # line is a str
        line = line.strip() # strips whitespaces from the beginning and end of line
        line = line.split('\t') # splits at the whitespace
        print(line)
        key = line[0].strip() # strips whitespaces from the key
        value = line[1]
        ucsb_majors[key] = value
    infile.close()
```

Reading a large file in may take a really long time to load, and will make testing your function very tedious....

Instead, consider using a small file for testing to speed up the process and use the large file when your function is ready.

**Note!** Even if you are not submitting the replacement lab, we still encourage you to look at it for practice! Knowing how to compute summary statistics yourself might come in handy during the final.

Let's fix our code to skip duplicates.
```python
try:
    infile = open("major_codes.txt")
except FileNotFoundError as err:
    print("No such file exists.")
    print("ERROR:", err) 
else:
    ucsb_majors = {}
    for line in infile: # line is a str
        line = line.strip() # strips whitespaces from the beginning and end of line
        line = line.split('\t') # splits at the whitespace
        print(line)
        key = line[0].strip() # strips whitespaces from the key
        value = line[1]
        if ucsb_majors.get(key) != None:
            ucsb_majors[key] = value
            print(type(line))
            outfile.write(line_to_write)
    infile.close()
```


Practice your debugging skills: given a function/code that is not correct, find the error or where it might potentially be going wrong.
