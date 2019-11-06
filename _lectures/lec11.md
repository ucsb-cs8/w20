---
num: "lec11"
desc: "File I/O + Dictionaries"
ready: true
lecture_date:  2019-11-05
reading: Chapters 4.3, 6.1
---

# CS 8 Lec 11
```python
''' A few notes about Lab05
- Lab05 uses tuples as a way to organize certain data.
- One of the requirements is to print certain data in
descending order
- We talked about sorting lists
'''

letters = ["b","c","a"]
letters.sort()
print(letters)

# but what if we had a list of tuples? How would the list sort
# these items?

tuples = [(1,3),(3,2),(3,1),(3,3),(0,1)]
print(tuples)
tuples.sort()
print(tuples)

# by default, list.sort() will sort the first value and then by
# the 2nd value in the case of a tie.
# We can reverse the sorting order (descending instead of ascending)

tuples.sort(reverse=True)
print(tuples)


''' Dictionaries
- New Tool: DICTIONARIES
- Otherwise known as TABLES or MAPS
    - Works where a KEY maps to a VALUE
    - Use dictionaries for two main reasons:
        - Gives us more precise indexing than Lists
        - L['someString'] - allows us to index elements
        based on some key
        - Performance is MUCH better than searching through
        Lists.
            - keys are HASHED to a specific index value
                - keys are passed through some math equation
                and an index is computed
                - Provides DIRECT ACCESS to the value given a
                key.
            - Details of hashing is not discussed in this class,
            but you may see it sometime...
'''
''' Syntax for Dictionaries
{<key1>:<value1>,<key2>:<value2>, ... , <keyn>:valuen>}
'''

fruit_dict = {} # Empty dictionary. Notice the curly braces instead of []

fruit_dict = {'apple':18, 'orange':19, 'banana':20, 'kiwi':21}

print(fruit_dict)
print("You have", fruit_dict['apple'], "apples")
print("You have", fruit_dict['kiwi'], "kiwis")
print(len(fruit_dict))


'''
# Simple way to get key / value
for x in D:
    print(x) # Prints the keys
    print(D[x]) # Prints the values
'''

for fruit in fruit_dict:
    print("You have", fruit_dict[fruit], fruit)

fruit_dict["melon"]

''' Restrictions on using Dictionaries
- Keys must be an immutable type (int, str, namedtuples, - not
lists for example).
- Values can be anything (mutable or immutable objects)
- For our purposes, KEYS are UNIQUE. Don't define something like
{'apple':17, 'apple':18}.
- Python is actually OK with duplicate keys and it will return
the last key/value in the dictionary.
- Again, for our purposes, we should never use duplicate key
values (kinda defeats the purpose of dictionaries).
'''

''' dictionary methods
    D.pop(key) # remove and return the value
    D.update(D2) # combine values in D and D2
    D.get(key) # returns item if it exists. If not, returns None or a default value
    D.keys() # dict_keys([ LIST OF KEYS ])
    D.values() # dict_values([ LIST OF VALUES ])
    D.items() # dict_items([ LIST OF KEY,VALUE ])
'''
'''
value = D.pop('apple')
print(D)
print(value)
D.update({'cherry':25,'lemon':27})
print(D)

# What if something is not in the dictionary and we try to access it?
#print(D["CS8"]) #ERROR - "CS8" key doesn't exist.
print(D.get("CS8"))

# Can define the default return value if key doesn't exist
print(D.get("CS8", "not in dictionary!"))

print(D.keys())
print(D.values())
'''
'''
for item in D.keys():
    print(item)
'''

# Example of adding to a dictionary
D = {}
print(D)
D['CS8'] = "UCSB"
print(D)
D['CS16'] = "UCSB"
print(D)
'''
```

# File I/O

```python
'''
    - FILES are a valuable tool to help us solve many
    types of problems.

FILES give us PERSISTENCE
    - So far, we've been running our programs in IDLE and
    putting our code into a file.
    	* Data must be entered on every program run
    	* Programs have no way to write permanent output
    - With PERSISTENCE, our data can be "saved" between
    each program execution.

FILE BASICS:
    - We can store files in many different forms
        - Examples: .xls, .docx, .pdf, .jpg, ...
        - For this class, we'll just deal with "plain text"
        files (.txt)
        - These CHARACTERS are represented in something called
        ASCII (American Standard Code for Information Interchange)
        - This was dominant / simple way of representing text
        where each character is 8 bits long
        - UTF-8 is the most popular format in today's web browsers
        - Allows us to represent MANY characters from multiple
        languages

TERMS:
    
   	File: A document
    Directory: A folder containing files and other folders
    File System: Collection of all the files and folders on the computer, organized in a heirarchy
    For this class, we'll deal with reading and writing files
    that are in the same directory as our .py file (known as our "working directory")
        - This makes our lives much easier

The Unix File system:
- In unix the directory at the highest level of the hierarchy is called the root (denoted by `/`). 
  - All other directories and files are stored within the root
- Path: The path is a sequence (of directories) that specifies the location of a file or directory within the file system.
  - For example, `/Users/ykk/` says that the directory `ykk` is within the directory `Users` which is within the root

	* An ABSOLUTE path describes the location of a file or directory starting with the root (`/`)
	* A RELATIVE path describes the location of a file relative to the current directory. 
    For example `./cs8/lab05/` (Here `./` stands for "current directory" ) 

- You can move through the unix file system via the command line (instead of using the graphical interface)
- Few useful unix commands
  - `pwd` (path to your current working directory)
  - `ls`  (list all the files and directories within the current directory)
  - `mkdir` (make a new directory)
  - `cd` (change into a directory, need to give either absolute or relative path)



FILE I/O:
    - I/O stands for input / output
    - We read data from a file into our program.
    - We write data from our program into a file.
    - Steps for File I/O
        1. Open the file (creates a "connection" between your program and the file).
            - Choose if the connection will be for reading, writing, or appending to a file.
        2. Read the data / write the data
        3. Close the file (close the "connection"). This should to be done once per file.

Common ways to read data from files
    1. `read()` method - reads the entire file into one string
        - Good for small data (large files may be too big to
        store into memory)
    2. `read(n)`: Read the next n characters from the input
        - Better for larger files since you only need to store
        n characters in memory at a time.
    3. `readline()`: Reads everything from the current position
        to the next '\n' (or to the end of the file, 'EOF'). If
        nothing left to read, .readline() returns an empty string.
    4. `readlines()`: Reads all the lines in the file and returns
        a list.
    5. `for a_line in infile`:
        - `a_line` represents a line in the file, `infile` is the
        open file.
'''
```

### An example from class 

* creating a text file with the data from <https://registrar.sa.ucsb.edu/faculty-staff/resources-for-faculty-staff/major-minor-codes>
* reading a file with major codes/descriptions 
* creating a dictionary 
```py
infile = open("major-codes.txt", 'r')

major_dict = {} # an empty dictionary
for line in infile:  # for every line in the input file
    print(line)
    mline = line.strip().split('\t') # strip the whitespace, split it by tabs
    
    print(mline[0], ":", mline[1]) 
    major_dict[mline[0]] = mline[1] # add the key and value to the dictionary

print(major_dict)

infile.close()
```
