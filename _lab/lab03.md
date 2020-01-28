---
layout: lab
num: lab03
ready: true
desc: "Conditionals, Nested Control Structures, and While Loops"
assigned: 2020-1-27 09:00:00.00-7
due: 2020-2-4 8:59:00.00-7
---

In this lab, you'll get more practice with:

* Writing functions
* Testing your functions with pytest
* Using conditionals and nested control statements
* Using `while` loops to iterate through list and string indexes


# Instructions

In this lab, you will need to create two files:
* `lab03.py` - file containing function definitions
* `lab03_tests.py` - file containing test cases
* Please remember to add your name in a comment at the top of each file.

Starter code is provided for you and is given at the bottom of this page. 
There are two files: the starter code `lab03.py` and test cases from `lab03_tests.py` that go with that function definition.
Your file names have to be **exact**, otherwise, you will get a 0 for the assignment on Gradescope.

# Read all instructions (including docstrings) carefully

We recommend that you **read through the whole lab first** before starting to work on the lab.

You will complete the portions in the starter code by doing the following:

1.  Create a directory called `~/cs8/lab03` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `lab03.py` and `lab03_tests.py` in that `~/cs8/lab03` directory.
4.  ONE AT A TIME, copy the function definitions from the starter code (into the `lab03.py`), and the tests that go along with those functions (into the `lab03_tests.py`), and get the tests to pass.
   * By one at a time, what I mean is, at your first step, copy ONLY the first function definition from the starter code `lab03.py` and copy only the import statements and test cases from `lab03_tests.py` that go with that function definition.
   * Then, before you move on to the next function definition and <em>its</em> tests, get all of the tests from the one you just copied to pass.
   * Then, and only then, copy the next function definition and its tests into your files.
   * Repeat this until you have ALL of the function definitions and their tests, and all of them pass.

# Read all instructions (including docstrings) carefully

As you make progress on the lab, we encourage you to submit to Gradescope periodically for several reasons:
* You will have a backup of your file in case you accidentally delete yours, or in case your laptop dies.
* You can move code between your laptop and CSIL by downloading your submitted code from Gradescope

# Upload `lab03.py` and `lab03_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "lab03" on Gradescope and upload your `lab03.py` and `lab03_tests.py` files.

# Starter code for the function definitions

**`lab03.py`**

```python
# Submitted by: (insert name and perm number here)
# CS8 (W20)

# This file contains several incomplete function definitions with stub
# values. lab03_tests.py should have tests to check if the functions are correct.
# Your assignment is to complete each function according to the
# functions' descriptions.
#
# Once you complete a function, use pytest on the test functions
# in lab03_tests.py to see if your functions are working correctly

def charInWord(word, char):
    '''
    -charInWord() takes in a parameter word and another parameter 
    char and determines whether char is contained in word.
    -If word is not a string type, or if char is not a string type, the function
    should return None.
    -If word contains the letter char, the function should return True. Otherwise,
    it should return false. 
    - Note: When char is of type string, it should be of length 1. For example,
    char will be a single letter like “a” or “z.” We will not test for cases
    where char is more than one character, like char = “ab” 
    -*** Note: you will need to use a while loop and string indexing.***
    -*** You will not get full credit if you use other loops or the in operator.***
    '''
   
    return "stub"

def charWordList(wordList, char):
    '''
    - charWordList takes the parameter wordList the parameter char, and returns
    a list of all the strings that contain char.
    - If wordList is not a list type, or if char is not a string type, the function
    should return None.
    - If elements in wordList are not strings, those elements should just be ignored.
    - Note: When char is of type string, it will be of length 1. For example,
    char will be a single letter like “a” or “z.” We will not test for cases
    where char is more than one character, like char = “ab”
    - ***Hint: you will need to use a while loop, list indexing, and a call to
    your previous function. Once again, you may not use the in operator***
    - ***Make sure to use charInWord function that you previously wrote: 
    it is your helper function.***
    '''
   
    return "stub"
  

def addListElements(aList):
    '''
    -write a funciton that takes in a list (aList) of items and returns a tuple of length 2.
    -The 0th element of this tuple should be a sum of all the ints and
    floats in aList, and the 1st element of the tuple should be a
    concatenation of all the strings from aList
    -Other types (e.g., bool) should be ignored
    -If there are no ints or floats, the sum should be zero. If there are no strings,
    the second element of the tuple should be an empty string.
    ***Hint: think of creating a variables that you initialize to the default
    values (0 and ''), which will, for example, help you keep track of the running sum.***
    
    '''
    
    return "stub"
    
def buzzfeedQuizTrip(number):
    '''
    Return the corresponding trip destination based on the value of the user
    input using the following guidelines:
    [1-4]: "Hawai'i"
    (4-8]: "Bahamas"
    (8-12]: "Madagascar"
    (12-16]: "Fiji"
    (16-20]: "Iceland"
    -If the number is not an int type OR if the number is outside the range of
    [1-20], return the message "please enter a valid integer between 1 and 20"
    '''
    
    return "stub"
    
def converter(tuplelist):
    '''
    -Given a list of tuples containing student's first and last names return a list
    of strings with the student's first name, a space, their last name initial,
    followed by a period. 
    -E.g., if this tuple list was given [("Chris", "Gaucho"),("Harry", "Potter")]
    the resulting list would be ["Chris G.", "Harry P."]
    -If the tuple list is empty return an empty list. 
    '''
    
    return "stub"
    
def isPhoneNumber(digits):
    '''
    - Nithya asked for Nassim's phone number. She wants to write a function 
      to check if the number is a real phone number.
    - Returns True if `digits` is of type int and is nine numbers long. Otherwise return False.
    - Hint 1: You can check if digits is an int with type(digits) == int
    - Hint 2: To check the length of digits, you must convert it to a string first 
      using str(digits).
    '''
    return "stub"

```


# Starter code for function tests
**`lab03_tests.py`**

```python
# Submitted by: (insert name and perm number here)
# CS8 (W20)
# lab03_tests.py
####################

from lab03 import charInWord
# Test cases for charInWord:

def test_charInWord_1():
  assert charInWord("word", "d") == True
  
def test_charInWord_2():
  assert charInWord("", "d") == False
  
def test_charInWord_3():
  assert charInWord(8, "d") == None
  
def test_charInWord_4():
  assert charInWord("word", True) == None
  
def test_charInWord_5():
  assert charInWord("abcde", "f") == False


####################

from lab03 import charWordList
# Test cases for charWordList: 

def test_charWordList_1():
  assert charWordList(["dog", "cat", "fish","wolf", "rabbit", "donkey"], "o") == ["dog", "wolf", "donkey"]
  
def test_charWordList_2():
  assert charWordList(["", 8, True, "groot", "grout"], "u") == ["grout"]
  
def test_charWordList_3():
  assert charWordList([""], "o") == []
  
def test_charWordList_4():
  assert charWordList(["", 8, True, "groot", "grout"], True) == None

####################

from lab03 import addListElements
# Test cases for addListElements: 

def test_addListElements_1():
  assert addListElements(["I", 13, "Love", 12, "Shrek", 11]) == (36,"ILoveShrek")
  
def test_addListElements_2():
  assert addListElements(["", True, "groot", ""]) == (0,"groot")
  
def test_addListElements_3():
  assert addListElements([]) == (0,"")

def test_addListElements_4():
  assert addListElements(["What", True, "Are", "Those?"]) == (0,"WhatAreThose?")
  
####################  
from lab03 import buzzfeedQuizTrip
# Test cases for buzzfeedQuizTrip

def test_buzzfeedQuizTrip_1():
    assert buzzfeedQuizTrip(1) == "Hawai'i"
    
def test_buzzfeedQuizTrip_2():
    assert buzzfeedQuizTrip(4) == "Hawai'i"

def test_buzzfeedQuizTrip_3():
    assert buzzfeedQuizTrip(12) == "Madagascar"

def test_buzzfeedQuizTrip_4():
    assert buzzfeedQuizTrip(18) == "Iceland"

def test_buzzfeedQuizTrip_5():
    assert buzzfeedQuizTrip(7) == "Bahamas"

def test_buzzfeedQuizTrip_6():
    assert buzzfeedQuizTrip(21) == "please enter a valid integer between 1 and 20"

def test_buzzfeedQuizTrip_7():
    assert buzzfeedQuizTrip(0) == "please enter a valid integer between 1 and 20"
    
#################### 

from lab03 import converter
# Test cases for converter

def test_converter_1():
    assert converter([])==[]

def test_converter_2():
    assert converter([("Chris", "Gaucho"),("Harry", "Potter")])==["Chris G.", "Harry P."]

def test_converter_3():
    assert converter([("Stephen", "Curry"), ("Kobe", "Bryant"), ("Michael", "Jordan") , ("LeBron", "James"), ("James", "Harden")])== ["Stephen C.", "Kobe B.", "Michael J." , "LeBron J.", "James H."]
    
####################
from lab03 import isPhoneNumber

# Tests for isPhoneNumber
def test_isPhoneNumber_1():
    assert isPhoneNumber("1234") == False
    
def test_isPhoneNumber_2():
    assert isPhoneNumber(8051112222) == True
    
def test_isPhoneNumber_3():
    assert isPhoneNumber(1234) == False
    
def test_isPhoneNumber_4():
    assert isPhoneNumber(3.14) == False
    
def test_isPhoneNumber_5():
    assert isPhoneNumber([0]) == False
    

```
# Bonus! Make your own Spongebob Font generator!

![Mocking Spongebob Meme](mockingSpongebob.jpg) 
This is an optional, extra credit exercise for you to have fun with strings, conditionals, and while loops. 

You will need to submit this function in a separate file **`lab03_bonus.py`** to a separate Gradescope assignment **Lab03: Bonus**.

This function is based off of the Mocking Spongebob Meme. Your task: to write a function that takes in a string `message` and returns the same message but so that it looks like the font from a Mocking Spongebob meme, meaning that it's letters are randomly uppercase or lowercase. But in Python, strings are immutable (i.e you cannot directly modify them by changing individual characters). For example:

```python
>>> word = "hello"
>>> word[0] = "H"

Traceback (most recent call last):
  File "<pyshell#3>", line 1, in <module>
    word[0] = "H"
TypeError: 'str' object does not support item assignment
```
Notice when we try to assign `word[0]` to be `"H"`, we get an error. Because we cannot directly change/reassign the characters in the string `message`, we will instead declare an empty string variable called `SpongebobText` that we will add characters to one by one. We will access each character in `message`, decide whether to make a letter lowercase or uppercase, and then add it to `SpongebobText`.

To decide whether or not to make a letter uppercase or lowercase, we will pick a random number between 0 and 10 (you'll see how to do that below). If that number is even, make the letter lowercase and add it to `SpongebobText`. Otherwise, make the letter uppercase and add it to `SpongebobText`.

This function will require you to use Python functions you are probably unfamiliar with: two of them are `someStr.lower()` and `someStr.upper()`, where `someStr` is a string variable. `lower()` takes a string variable and returns a lowercase version of it. `upper()` takes a string variable and returns an uppercase version of it.

```python
>>> word = "Hello"
>>> word[0].lower()
'h'
>>> print(word)
'Hello'
>>> word.upper()
'HELLO'
>> print(word)
'Hello'
```

Note that `upper()` or `lower()` **do not modify** the variable `word`: they return a **_new_** string with the characters that are either in lower or upper case..

You will also have to use `random.randint(a,b)` which returns a random integer `N` such that `a <= N <= b`. 

```python
>>> random.randint(0, 5)
2
>>> random.randint(0, 7)
3
```

For the `spongebobFont()` function, every time you index a character in message, you will want to generate a random integer between 0 and 10. Then, if that integer is even, you should add a lowercase version of that letter to `SpongebobText`. Otherwise, add an uppercase version of that letter to `SpongeboText`.

Here is the starter code:

```python
import random

def spongebobFont(message):
    '''
    - Given an input string, go through the string character by character and
    decide whether or not to make a specific character uppercase or lower case. 
    -E.g., if message = "hello", first look at the first character 'h'. Then pick
    a random integer. If that integer is even, add a lowercase 'h' to 
    SpongebobText. Otherwise, add an uppercase 'H' to SpongebobText. 
    Do this for every character in message.
    '''
    
    SpongebobText = ""  # This is the string we will add characters to and return at the end of our function
    random.seed(7919)   # Do not edit this line!
    
    i = 0   # This is the index variable we will use to index message
    while i < ... # TODO: while i is less that the length of sentence; replace ... with the rest of the expression
        num = ... # TODO: pick a random number from 0 to 10
        if ...  # TODO: if num is even; replace ... with the expression to check if num is even
            SpongebobText += ... # TODO: make the letter at index i in message lowercase and add it to SpongebobText
        else:   # otherwise num is odd
            SpongebobText += ... # TODO: make the letter at index i in message lowercase and add it to SpongebobText
        i = ... # TODO: update i by 1
    
    return SpongebobText
    
def test_spongebobFont():
    assert spongebobFont("Beep boop, I'm a computer") == "bEeP booP, i'M a cOmpUter"

  ```

Submit this function in a separate file **`lab03_bonus.py`** to a separate Gradescope assignment **Lab03: Bonus**.

# Last Step: Submit your files to Gradescope

Please DO NOT upload your file to Gradesope without testing locally first (i.e., using `pytest`).
Once you see your tests are passing, THEN submit a version to Gradescope.


**Acknowledgment**: Special thanks to Olivia Gillam, Sara Mandic, Noemi Rieber, April Sanchez, and Cindy Zhao who helped design this lab at UCSB for CS 8 (W20).

