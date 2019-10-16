---
layout: lab
num: lab03
ready: true
desc: "Conditionals, Nested Control Structures, and Loops"
assigned: 2019-10-16 09:00:00.00-7
due: 2019-10-30 17:00:00.00-7
---

In this lab, you'll get more practice with:

* Writing functions
* Testing your functions with pytest
* Using conditionals and nested control statements
* Using loops to iterate through containers (namedtuples)

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_tests.py` - file containing test cases
* Please remember to add your name in a comment at the top of each file.

Starter code is provided for you and is given at the bottom of this page. There are two files: the starter code `{{page.num}}.py` and test cases from `{{page.num}}_tests.py` that go with that function definition.

You will complete the portions in the starter code by doing the following:

1.  Create a directory called `~/cs8/{{page.num}}` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_tests.py` in that `~/cs8/{{page.num}}` directory.
4.  ONE AT A TIME, copy the function definitions from the starter code, and the tests that go along with those functions, and get the tests to pass.
   * By one at a time, what I mean is, at your first step, copy ONLY the first function definition from the starter code `{{page.num}}.py` and copy only the import statements and test cases from `{{page.num}}_tests.py` that go with that function definition.
   * Then, before you move on to the next function definition and <em>its</em> tests, get all of the tests from the one you just copied to pass.
   * Then, and only then, copy the next function definition and its tests into your files.
   * Repeat this until you have ALL of the function definitions and their tests, and all of them pass.

You are encouraged to try submitting to Gradescope periodically for several reasons:

* You can get partial credit if some of your tests pass for some of your functions.
* You will have a backup of your file in case you accidentally delete yours, or in case your laptop dies.
* You can move code between your laptop and CSIL by downloading your submitted code from Gradescope

# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "{{page.num}}" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.

# Starter code for the function definitions

**`{{page.num}}.py`**

```python
# Student: (insert name and perm number here)
# CS8 (F19)

# This file contains several incomplete function definitions with stub
# values. Lab03_tests.py have tests to check if the functions are correct.
# Your assignment is to complete each function according to the
# functions' descriptions.
#
# Once you complete a function, use pytest on the test functions
# in lab03_tests.py to see if your functions are working correctly

def notStringContainingR(word):
    '''
    - Return True when word is a string that contains no letter 'r' (or 'R')
    - It should work both for lower and upper case.
    - When word isn't a string or is an empty string (""), return True
    (because it is not a string contaning an R).
    - You can check if the word value is a string with type(word) == str 
    '''
    return "stub" 


def hasVowel(word):
    '''
    - Return True when word is a string that contains a vowel
    (a,e,i,o,u,A,E,I,O,U).
    - It should work for both lower and upper case vowels.
    - When word doesn't have a vowel, return False. Return True otherwise.
    - If word isn't a string, return False (because it is not a string
    containing a vowel).
    - Hint: recall the boolean operator "in" and use that when
    checking if a character is a vowel.
    '''
    return "stub"


def isNumber(item):
    '''
    - Return True if item is of type int or type float, otherwise return
    False.
    - You can check if item is an int with type(item) == int, and a float
    with type(item) == float
    '''
    return "stub"


def onlyContainsStrings(theList):
    '''
    - Returns True if theList is a list containing only strings.
    - The parameter theList can be anything.
    - An empty list should return False since it doesn't contain a string.
    - If theList is not a list type, return False since theList is not a list
    containing only strings.
    - Note: you can check if theList is a list with type(theList) == list
    '''
    return "stub"


def contains(x, theList):
    '''
    - Returns True if the value of x is in theList.
    - The parameters x and theList can be anything.
    - An emptyList should return False since it doesn't contain any values
    (including x).
    - If theList is not a list type, return False since x is not in a list.
    '''
    return "stub"


def abbreviate(word):
    '''
    - Returns a string with (up to) the first three characters of
    the string word.
    - The value of word can be anything.
    - If word is not a string, return an empty string ("").
    '''
    return "stub"


def hasMultiplesOf(x, listOfNums):
    '''
    - Returns True if ALL items in listOfNums are multiples of x.
    - theList can have elements of any type.
    - If listOfNums is not a list type, return False.
    - If listOfNums is empty, return False since no items are a multiple
    of x
    - If listOfNums contains an element that is not a number (int or
    float), return False.
    '''
    return "stub"
    

def countEvens(listOfInts):
    '''
    - Returns an integer value representing the number of even numbers that
    exist in listOfInts.
    - Return 0 if listOfInts is not a list type or if no even number exists
    in listOfInts.
    - Note: elements in listOfInts can contain any data type.
    '''
    return "stub"


def computeGrade(percentage):
    '''
    - Return the corresponding letter grade string based on the value of
    percentage using the following scale:
    [100 - 90]: 'A'
    (90 - 80] : 'B'
    (80 - 70] : 'C'
    (70 - 60] : 'D'
    (60 - 0]  : 'F'
    - If percentage is not a number type (int or float) OR if percentage is
    outside the range of [100 - 0], return an empty string ("").
    '''
    return "stub"


# Definition of a Book namedtuple object used for the
# following function below.
from collections import namedtuple
Book = namedtuple("Book", "title author price")

def expensiveBooks(price, listOfBooks):
    '''
    - Returns a list of book titles of Books that are greater or equal to
    the value price.
    - If price is not a number type, then return an empty list ([]).
    - If listOfBooks is not a list type, then return an empty list ([]).
    - Elements in listOfBooks may contain multiple types (not necessarily
    Books). You can check if an element is a Book object with
    type(value) == Book. You can "skip" an element that's not a Book and
    continue checking other elements in listOfBooks.
    - You can assume Book objects are constructed correctly (i.e. title
    and author are strings, and book prices are either an int or float).
    - Note: You must obtain values of a book object using the name of
    the object's attributes (.title, .author, .price) instead of indexing
    them for full credit (as discussed in lecture). 
    - Hint: Think of appending book titles to a list (recall .append) when
    the cost of the book is greater than the value price, and returning the
    list of accumulated book titles.
    '''
    return "stub"
```


# Starter code for function tests
**`{{page.num}}_tests.py`**

```python
# Student: (insert name and perm number here)
# CS8 (F19)

# lab03_tests.py

from lab03 import notStringContainingR

# Tests for notStringContainingR
def test_notStringContainingR_1():
    assert notStringContainingR("word") == False

def test_notStringContainingR_2():
    assert notStringContainingR("super") == False

def test_notStringContainingR_3():
    assert notStringContainingR("ReEl") == False

def test_notStringContainingR_4():
    assert notStringContainingR("") == True

def test_notStringContainingR_5():
    assert notStringContainingR(3.14) == True

####################
from lab03 import hasVowel

# Tests for hasVowel
def test_hasVowel_1():
    assert hasVowel(True) == False

def test_hasVowel_2():
    assert hasVowel("Pythn") == False

def test_hasVowel_3():
    assert hasVowel("") == False

def test_hasVowel_4():
    assert hasVowel("borg") == True

def test_hasVowel_5():
    assert hasVowel("frEE") == True

####################
from lab03 import isNumber

# Tests for isNumber
def test_isNumber_1():
    assert isNumber("1") == False

def test_isNumber_2():
    assert isNumber(-1) == True

def test_isNumber_3():
    assert isNumber(True) == False

def test_isNumber_4():
    assert isNumber(3.14) == True

def test_isNumber_5():
    assert isNumber([0]) == False

####################
from lab03 import onlyContainsStrings

# Tests for onlyContainsStrings
def test_onlyContainsStrings_1():
    assert onlyContainsStrings([]) == False

def test_onlyContainsStrings_2():
    assert onlyContainsStrings(["a", "c", ""]) == True

def test_onlyContainsStrings_3():
    assert onlyContainsStrings(["18", 18, "eighteen"]) == False
    
def test_onlyContainsStrings_4():
    assert onlyContainsStrings([-1, "-1"]) == False

def test_onlyContainsStrings_5():
    assert onlyContainsStrings("python") == False

####################
from lab03 import contains

# Tests for contains
def test_contains_1():
    assert contains([], [4, [], 5]) == True

def test_contains_2():
    assert contains("18", [18, 18.0, "18"]) == True

def test_contains_3():
    assert contains("element", []) == False

def test_contains_4():
    assert contains("item", ("item")) == False

def test_contains_5():
    assert contains((1,2), [1, 2, "3", (1,2)]) == True
                    
####################
from lab03 import abbreviate

# Tests for abbreviate
def test_abbreviate_1():
    assert abbreviate("January") == "Jan"

def test_abbreviate_2():
    assert abbreviate(20) == ""

def test_abbreviate_3():
    assert abbreviate("At") == "At"

def test_abbreviate_4():
    assert abbreviate("T") == "T"

def test_abbreviate_5():
    assert abbreviate(["A", "T"]) == ""

####################
from lab03 import hasMultiplesOf

# Tests for hasMultiplesOf
def test_hasMultiplesOf_1():
    assert hasMultiplesOf(3, [-3, 0, 3, 6]) == True

def test_hasMultiplesOf_2():
    assert hasMultiplesOf("3", [-3, 0, 3, 6]) == False

def test_hasMultiplesOf_3():
    assert hasMultiplesOf(3, (-3, 0, 3, 6)) == False

def test_hasMultiplesOf_4():
    assert hasMultiplesOf(1.1, [1.1, 2.2, 4.4]) == True

def test_hasMultiplesOf_5():
    assert hasMultiplesOf(5, []) == False

####################
from lab03 import countEvens

# Tests for countEvens
def test_countEvens_1():
    assert countEvens([0,2,4]) == 3

def test_countEvens_2():
    assert countEvens([0,"2","Four", 6]) == 2

def test_countEvens_3():
    assert countEvens((0,2,4)) == 0

def test_countEvens_4():
    assert countEvens([-1,1,3,5,7]) == 0
    
def test_countEvens_5():
    assert countEvens([1.0,2.0,3.0,4.0,5.0,6.0,7.0,-2.0]) == 4

####################
from lab03 import computeGrade

# Tests for computeGrade
def test_computeGrade_1():
    assert computeGrade(90) == "A"

def test_computeGrade_2():
    assert computeGrade("80") == ""

def test_computeGrade_3():
    assert computeGrade(79.9) == "C"

def test_computeGrade_4():
    assert computeGrade(101) == ""

def test_computeGrade_5():
    assert computeGrade(-1) == ""

####################
from lab03 import expensiveBooks, Book

b1 = Book("Title1", "Author1", 5.99)
b2 = Book("Title2", "Author2", 0.99)
b3 = Book("Title3", "Author3", 20)
b4 = Book("Title4", "Author4", 0)
b5 = Book("Title5", "Author5", 100)
bookList = [b1,b2,b3,b4,b5]

# Tests for expensiveBooks
def test_expensiveBooks_1():
    assert expensiveBooks("0", bookList) == []

def test_expensiveBooks_2():
    assert expensiveBooks(5.99, bookList) == ['Title1','Title3','Title5']

def test_expensiveBooks_3():
    assert expensiveBooks(25, bookList) == ['Title5']

def test_expensiveBooks_4():
    assert expensiveBooks(5.99, (b1,b2)) == []

def test_expensiveBooks_5():
    assert expensiveBooks(101, bookList) == []

```


