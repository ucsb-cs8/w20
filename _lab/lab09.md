---
layout: lab
num: lab09
ready: true 
desc: "Labs 0-3 Replacement Assignment"
assigned: 03-10 09:00
due: 2020-03-17 09:00
---

# This lab is optional 
Your submission for this lab will replace your lowest score from Lab00-Lab03, if the score for this lab is higher.

In this lab, you'll get more practice with:
* Skills from lab00
  * performing basic management of directories and files
  * creating Python programs in IDLE
  * submitting an assignment using the Gradescope system
* Skills from lab01
  * Creating a file that has some functions in it
  * Testing those functions interactively at the Python prompt
  * Creating a file of automatic test cases for those functions
  * Running those test cases
  * Submitting your functions and test cases to Gradescope for grading

* Skills from lab02
  * Creating a file that has some functions in it
  * Testing those functions interactively at the Python prompt
  * Creating a file of automatic test cases for those functions
  * Running those test cases
  * Submitting your functions and test cases to Gradescope for grading

* Skills from lab03
  * Testing your functions with pytest
  * Using conditionals and nested control statements
  * Using `while` loops to iterate through list and string indices


# This lab must be done solo.

As with all labs in this course, as specified in the Syllabus and the university policies on academic integrity, your submission should be your own work, done by you from start to finish, without using another resource as the source of your answers.

The Office of Student Conduct has policies, tips, and resources for proper citation use, recognizing actions considered to be cheating or other forms of academic theft, and students’ responsibilities, available on their website at: <https://studentconduct.sa.ucsb.edu/academic-integrity>. You are required to read the policies and to abide by them.
We will be using plagiarism detection services and we will report the violation of academic integrity cases to the Office of Student Conduct. 

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_tests.py` - file containing test cases
* Please remember to add your name in a comment at the top of each file.

Your file names have to be **exact**, otherwise, you will get a 0 for the assignment on Gradescope (there should be no curly braces in the filenames!).

# Read all instructions (including docstrings) carefully

We recommend that you **read through the whole lab first** before starting to work on the lab.

You will complete the portions in the starter code by doing the following:

1.  Create a directory called `~/cs8/{{page.num}}` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_tests.py` in that `~/cs8/{{page.num}}` directory.
4.  ONE AT A TIME, copy the function definitions (**including the docstring**) from the starter code, and the tests that go along with those functions, and get the tests to pass.
   * By one at a time, what we mean is, as your first step, copy ONLY the first function definition from the starter code `{{page.num}}.py` and copy only the import statements and test cases from `{{page.num}}_tests.py` that go with that function definition. 
   * Make sure you include `import pytest` at the top of your file so that you are able to test your functions in terminal with pytest. **Include additional tests.** Before you move on to the next function definition and <em>its</em> tests, get all of the tests from the one you just added to pass.
   * Then, and only then, copy the next function definition and its tests into your files.
   * Repeat this until you have ALL of the function definitions and their tests, and all of them pass.

# Read all instructions (including docstrings) carefully

As you make progress on the lab, we encourage you to submit to Gradescope periodically for several reasons:
* You will have a backup of your file in case you accidentally delete yours, or in case your laptop dies.
* You can move code between your laptop and CSIL by downloading your submitted code from Gradescope

# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "{{page.num}}" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.

# Lab01
**1)** The first function called `InToFtandIn`  that we are going to create is converting a value in inches to feet and inches. For example, if you are 66 inches tall you are 5 feet and 6 inches. Return the result as a string `"feet:VALUE inches:VALUE"` where `VALUE` should be replaced with the correct output.

```python
>>> InToFtandIn(66.0) 
'feet: 5.0 inches: 6.0'
```
**2)** The second function that we are going to create is converting centimeters to feet and inches. So if you are 254 centimeters tall you are 8 feet and 4 inches. Return the result as a string `"feet:VALUE inches:VALUE"`, where `VALUE` should be replaced with the correct output.
* Hint use the `InToFtandIn` function in the second function.

```python
>>> CmToFtandIn(254) 
'feet: 8.0 inches: 4.0'
```

Here are the function stubs:

```python
# Submitted by: (insert name and perm number here)
# CS8 (W20)

def InToFtandIn(inches):
    """
    Convert a value in inches to feet and inches. 
    Return the result as a string 
    "feet:VALUE inches:VALUE" where VALUE should be 
    replaced with the correct output.
    """
    return "STUB" #TODO: replace this line with the proper code
    
def CmToFtandIn(cm):
    """
    Convert a value in centimeters to feet and inches. 
    Return the result as a string 
    "feet:VALUE inches:VALUE" where VALUE should be 
    replaced with the correct output.
    """
    return "STUB" #TODO: replace this line with the proper code 

```

Similarly, for the **{{page.num}}_tests.py**.

```python
def test_InToFtandIn_66():
    assert InToFtandIn(66.0)=="feet: 5.0 inches: 6.0"

def test_InToFtandIn_254():
    assert InToFtandIn(71.0)=="feet: 8.0 inches: 4.0"
```


# Lab02

**1)** Write a function `addDigits()` that takes in an integer parameter `num` and _repeatedly_ adds the digits of `num` together.  This cycle continues until the resulting number is just a single digit. The function should return this single digit as an integer.

For example, if `num = 123456789`, then `1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 = 45`, and then `4 + 5 = 9`.

Make sure to check that `num` is a positive integer. If it is not, return `"Error: num should be a positive integer"`.
(Hint: You might want to use two loops, the outermost of which is a `while` loop.)

**2)**  Write a function that takes a list of numbers and computes the summary statistics of the list (the minimum, maximum, and mean). We recommend computing these values WITHOUT using built-in functions i.e. `mean()`, `maximum()`, etc. Your function needs to return a list of tuples with the value and corresponding indices of the minimum and maximum value (note that _the mean value does not have an index in the list_!).

Your function should return the list that's formatted as follows (in that exact order): `[(“Min”, VALUE, INDEX), (“Mean”, VALUE), (“Max”, VALUE, INDEX)]`.

Assume the list contains valid numbers (integers and floats). Return an empty list, if the input list is empty.

```python
def addDigits(num):
    """
    Given an integer parameter num, repeatedly add 
    the digits of num together. This cycle continues 
    until the resulting number is just a single digit. 
    The function should return this digit as an integer.
    If num < 0, return "Error: num should be a positive integer"
    """
    return "STUB" #TODO: replace this line with the proper code 


def summaryStatistics(aList):
    """
    Given a list of numbers, compute
    the summary statistics of the list
    (i.e., min, average, max).
    Return the result as a list of tuples
    formatted as follows:
    [(“Min”, VALUE, INDEX), (“Mean”, VALUE), (“Max”, VALUE, INDEX)]
    substituting the value and corresponding indices.
    Assume the list contains valid numbers.
    Return an empty list, if aList is empty.
    """
    return "STUB" #TODO: replace this line with the proper code 

```

Here's a super-simple test to check that your function might be working correctly:

```python
def test_summaryStatistics_1():
    assert summaryStatistics([42]) == [('Min', 42, 0), ('Mean', 42), ('Max', 42, 0)]
```

# Lab03
**1)** Allie went to a fortune teller to get some advice about who she should ask
    out to prom. The fortune teller was pretty vague, but had a couple
    pieces of advice that she was adamant about. She emphasized that Allie should stay away
    from people whose names begin with the letters 'J' or 'M', and also warned against
    people with the zodiac sign is 'Taurus'.

Given a list of tuples containing a name as the first element of each tuple and a zodiac sign as the second element of each tuple, write a function `potentialDates()` that returns a list of the names of all potential dates for Allie.

For example,
`potentialDates([('Bill', 'Taurus') , ('Jill', 'Virgo'), ('Quinn', 'Gemini'), ('Matt', 'Cancer'),('Shawn', 'Capricorn')])`
    should return `["Quinn", "Shawn"]`.
    
**2)** Write a function `rearrangeWord()` that has two parameters: a list of integers and a word, and returns a string with the letters rearranged in the order of the integers in the list. If the length of the word and the length of the list are not the same, return None.

For example, `rearrangeWord([4, 2, 0, 1, 3], "chair")` would return `"rachi"`.   
    
```python
def potentialDates(aList):
    """
    Given a list of tuples containing a name 
    as the first element of each tuple and a zodiac sign
    as the second element of each tuple,
    returns a list of the names that do not begin with 
    the letters 'J' or 'M', and whose zodiac sign is not 
    'Taurus'.
    """
    return "STUB" #TODO: replace this line with the proper code 


def rearrangeWord(listofints, word):
    """
    Given a list of integers and a word, returns a string 
    with the letters rearranged in the order of the integers 
    in the given list. If the length of the word and the 
    length of the list are not the same, return None.
    """
    return "STUB" #TODO: replace this line with the proper code 
    
```

Here's the above example written as a pytest:

```python
def test_potentialDates_1():
    candidates = [('Bill', 'Taurus') , ('Jill', 'Virgo'), ('Quinn', 'Gemini'), ('Matt', 'Cancer'),('Shawn', 'Capricorn')]
    assert potentialDates(candidates) == ['Quinn', 'Shawn']

```


# Submit your {{page.num}}.py and {{page.num}}_tests.py to Gradescope

Remember: it is your responsibility to submit a correct file to Gradescope. Before your final submission, run the file to make sure there are no Python errors: if you see an error, then Gradescope will get it too and you will get a 0 for the **entire lab**, even if some of your functions were correct.

Before you submit your code to Gradescope, make sure that your files 
* are named **exactly** as stated (there should be no curly braces in the filenames!)
* do not have any `TODO` comments left in the code.
* contains a comment at the top of the file that says `Submitted by <name>, PERM, for CS 8 (W20)`. (Please, replace `<name>` and `PERM` with your first and last name and PERM number respectively.)

* * *

**Acknowledgment**: Special thanks to Noemi Rieber, Olivia Gillam, and Sara Mandic who helped to create this lab.
