---
layout: lab
num: lab08
ready: true
desc: "Recursion and dictionaries"
assigned: 2020-03-03 9:00am
due: 2020-03-10 08:59am
---

In this lab, you'll get more practice with:

* Writing recursive functions
* Writing tests in pytest for your recursive functions
* Creating and using Python dictionaries

## This lab must be done solo.

The following functions you might see in later CS courses or during the programming interviews, so it would be helpful for you to work on developing algorithms for solving them.


## All solutions in this lab must use recursion in order to receive credit.

You may not use any functions that are not in the book and that we have NOT discussed in lecture.

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_tests.py` - file containing test cases. A sample test is provided for each function. You will write 3 - 5 (or more) additional tests per function to confirm your code works as expected.
    * As usual, you want to test a variety of values: test the boundary of accepted inputs, check the negative numbers, "empty" variables, or really large values, if applicable.
    * Read through the docstring and make sure you are testing (and passing!) all conditions outlined there.
* <strong>Please add a comment with your name and PERM at the top of each file.</strong>

Starter code is provided for you at the bottom of this page.

You will complete the portions in the starter code by doing the following:

1.  Create a directory called `~/cs8/{{page.num}}` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_tests.py` in that `~/cs8/{{page.num}}` directory.
4.  **ONE AT A TIME**, copy the function definitions (**including the docstrings!**) from the starter code, write tests that go along with those functions in `{{page.num}}_tests.py`, and get your tests to pass.
   * Before you move on to the next function definition and <em>its</em> tests, get all of the tests you just wrote to pass.
   * Repeat this until you have ALL of the function definitions and their tests, and all of them pass.

------

# Questions to ask to solve recursion:

When designing a recursive solution, we need to answer the following questions:

* What is our **base case** (or cases)?
* What action should be taken in the base case? What is `print`ed or `return`ed?
* What is the **first recursive case** (next simplest input)?
* What action do we need to take to **get from the first recursive case to the base case**?

Remember, a skeleton of the recursive function will have the following approximate structure:

```python
# Note, this is just a pseudocode skeleton structure
def recF(input): 
   if input ...
      print/return # base case / cases 
   else / elif
      print/return recF( input => base case ) 

# => stands for "that gets you closer to"
# so, the recursive case is supposed to use
# the input that gets you closer to the base case
```
------


## Recursion walk-through

### Base case

**Remember**, recursive functions should always either **`print`** or **`return`** their result, depending on what you are asked to do. _Every case_ has to have a `print` or a `return`. The recursive case should always involve _calling the function itself_ on the input that _gets you closer to the base case_.

Whenever you are writing a recursive function, you need to first identify the **base case** (or cases): the simplest case for which the function works that will stop the recursion. 

For example, imagine you are given an integer `num` as an input and you want to reverse its digits and return the reversed digits as a string. The base case in this scenario would be a single-digit `num`. In your function, you can simply return the string consisting of `num` if it's between 0 and 9 (since there is nothing for you to reverse).

```python 
def reverseDigits( num ):
    """
    Reverse the digits of an 
    integer >0, using recursion.
    Return a string that contains
    the reversed number.
    Returns None if num < 0.
    """
    if 0 <= num <= 9:
        return str(num)
```

In your test file, you can test a few individual values (making sure your return types match what the docstring asks!).

```python
def test_reverseDigits_neg():
    assert reverseDigits(-1) == None

def test_reverseDigits_0():
    assert reverseDigits(0) == '0'

def test_reverseDigits_9():
    assert reverseDigits(9) == '9'
```

**Pro tip**: You can make sure that you check all numbers between 0 and 9 without having to write an individual case for each.

```python
def test_reverseDigits_base():
    for num in range(0, 10):
        assert reverseDigits(num) == str(num)
```

### Recursive case

Now, you can start developing an algorithm for a recursive solution.

Think of what input will result in the very first recursive case. Since it is the very first recursive case, that means that it would end up calling itself on an input that will lead to the base case.

I recommend thinking of _the next simplest input_ and how you can reduce that input to the base case (i.e., use base case as part of your solution for this case). What action do you need to take once you get the result of the base case to obtain the next simplest case?

In our case, the next simplest input would be a two-digit number, e.g., 16.
You will need to decide if you are going to be reversing the number by going front-to-back or back-to-front. Why? Because you need to decide if you are going to be assembling the reversed digits at the end or at the beginning of the string that contains the base case. For this example, I'm going to use the fact that modulo operator `%` is going to give me the remainder of the division by 10, in order to get the last digit. Since I'll be processing the number from the last digit, I'll be assembling the rest of the digits **after** the "last digit" that will be placed at the _beginning_ of the resulting string.

What does it look like?
* Input: `num = 16` (`reverseDigits(16)`) 
    * Get the last digit `6` (by using modulo: `num%10 = 16%10 = 6`).
    * Give the rest of the number (i.e., `1`) as an input to `reverseDigits` (calling `reverseDigits(1)` will trigger our base case and return `'1'` back to us).
    * Concatenate the result of `reverseDigits(1)` **after** the last digit, so `'6' + reverseDigits(1) = '6'+'1'` will produce the desired `"61"` result.

Let's see if this would work for a longer number.
* Input: `num = 162` (`reverseDigits(162)`) 
    * Get the last digit `2` (by using modulo: `num%10 = 162%10 = 2`).
    * Give the rest of the number (i.e., `16`) as an input to `reverseDigits` (calling `reverseDigits(16)` will trigger our previous case, which will eventually get to the base case; it should return `'61'` back to us).
    * Concatenate the result of `reverseDigits(16)` **after** the last digit, so `'2' + reverseDigits(16) = '2'+'61'` will produce the desired string `"261"` as a result.

Looks like this might work!
The only part we are missing in the above pseudocode, is the "Give the rest of the number" part. How would you get 16 from 162? Well, if we got 2 by getting the remainder, we can get 16 by getting _the integer part of dividing 162 by 10_.
We can express it using `int(num/10)`.

We are ready to put it together.

```python
def reverseDigits( num ):
    """
    Reverse the digits of an 
    integer >0, using recursion.
    Return a string that contains
    the reversed number.
    Returns None if num < 0.
    """
    if 0 <= num <= 9:
        return str(num)

    elif num > 0:
        return str(num%10) + reverseDigits(int(num/10))
```

Add the remaining tests to verify that the function works as expected.

```python

def test_reverseDigits_16():
    assert reverseDigits(16) == '61'

def test_reverseDigits_162():
    assert reverseDigits(162) == '261'

def test_reverseDigits_1623():
    assert reverseDigits(1623) == '3261'

```


# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.

## Your solutions must use recursion in order to receive credit.

Remember to include docstrings and write your own test functions.

```python
# Student: (insert name here)
# PERM number
# Make sure to include and read the comments for each function.

def recursiveDigitSum(n):
    '''
    Computes the sum of digits of a positive integer n.
    Returns None of n is negative.
    - Your solution must use recursion in order to receive credit.
    '''
    return "stub"


def recursiveSubstring(s, sub):
    '''
    The parameters sub and s are strings. 
    Compute if the string sub exists in s.
    - Your solution must use recursion in order to receive credit. (This means you are not allowed to use the "in" operator!)
    '''
    return "stub"


def recursiveReverseList(L):
    '''
    Tbe parameter L is a list containing any items. 
    Return the list L in reverse order.
    - Your solution must use recursion in order to receive credit.
    '''
    return "stub"

```

## Check if an input string is a palindrome

A **palindrome** is a word, number, or other sequence of characters which reads the same backward as forward, such as "madam" or "racecar".

Write your own implementation of a function `isPalindrome` to check if a string is a palindrome. For example: “redivide” is not a palindrome, while “detartrated” is a palindrome. **Ignore case** (capitalization) when comparing characters of the string.

The function returns `True` if an input string is a palindrome and `False` if it is not. You can do this by checking if the first character equals the last character, and so on. **You should use a recursive implementation**. 
_Hint_: remember how string slicing works.

```python

def test_isPalindrome_1():
    assert isPalindrome("Redivider") == True

def test_isPalindrome_2():
    assert isPalindrome("detartrated") == True

def test_isPalindrome_3():
    assert isPalindrome("Racingcar") == False

```

## Compute 2<sup>n</sup> - 1 recursively

Write your own implementation of a function `computeValue` that computes and returns _2<sup>n</sup> - 1_, given _n_ as an input parameter. If _n_ is less than 0, return the string `"Error"`.
__Make sure your solution uses recursion.__

__Hint:__  2<sup>n</sup> - 1 = 1 + 2 + 4 + ... + 2<sup>n-1</sup>

__Hint 2:__  1 + 2 + 4 + ... + 2<sup>n-1</sup> = 1 + 2(1 + 2(1 + 2(...)))
How many times will you need to repeat the computation?

```python
def computeValue(n):
    '''
    Compute 2^n-1 for n >= 0.
    Return "Error" if n < 0.
    """
    return "stub"
```

Remember to write your own test cases.
```python
def test_computeValue_1():
   assert computeValue(-5) == "Error"
   
def test_computeValue_2():
   assert computeValue(2) == 3
   
def test_computeValue_3():
   assert computeValue(5) == 31
   
```

# Practice using dictionaries

Remember that a dictionary stores key-value pairs:

```python
DICT = {<key1>:<value1>, <key2>:<value2>, ... , <keyN>:<valueN>}
```
* Also remember that using `DICT.get(key)` will by default return `None` if the `key` is not in the dictionary.
* You can use `DICT[key] = value` in order to add a new key-value pair to the dictionary.

```python
def palindromeDict ( aDict, word ):
    """
    Given a dictionary aDict and a
    string word, check if the word
    is stored in the dictionary and
    return its corresponding dictionary
    value if it's in aDict.
    Otherwise, store this word as
    a key in the dictionary with the
    boolean value indicating if it's
    a palindrome.
    Use isPalindrome() as a helper
    function.
    """
    if aDict... == None:
        aDict[word] = ...
    else:
        return ...
```

For the function above, you can test it in IDLE by first creating a sample dictionary and checking if the function behaves as requested.
You can create a sample dictionary and then test that you can add new keys and their corresponding values to it.

```python
>>> myDict = {"cat":True}
>>> palindromeDict(myDict, "cat")
True
>>> palindromeDict(myDict, "dog")
>>> palindromeDict(myDict, "dog")
False
```

# Bonus: counting words using dictionaries

This is an optional part of this assignment to give you more practice with the dictionaries.

**Submit your file called {{page.num}}_bonus.py on Gradescope under the {{page.num}}-bonus assignment.** Do not submit it with the regular {{page.num}} files, since you won't get credit for it if it is not submitted in the bonus assignment.

Remember the `getWordCount()` function from the previous lab?
Now, instead of returning a list of lists, re-write this function to return a correct dictionary.

```python
def getWordCount(filepath, charsToRemove):
    '''
    Get the frequency of each unique word
    in the file with given filepath, and return
    a dictionary, where each word is a key 
    and the number of times the word occurs in
    the file is the word's corresponding value
    in the dictionary.
    '''
    return "stub"
```

Once you can store the word counts in a dictionary, you can find the most common word by sorting the dictionary values.

```python
def mostCommonWord( aDict ):
    '''
    Given a dictionary aDict, returns the word with
    the highest frequency associated with it.
    In the case of ties (i.e., more than one word
    with the same max count, then return the word
    that occurs earliest in dictionary order
    (remember string comparisons).
    '''
    return "stub"
```


# Upload your {{page.num}}.py and {{page.num}}_tests.py files to Gradescope

Once you’re done with writing your functions, navigate to the Lab assignment “{{page.num}}” on Gradescope and upload your {{page.num}}.py and {{page.num}}_tests.py files. Submit all your files all at once, instead of uploading them one by one: each submission overwrites the previous files. You should be able to go to Gradescope to see both Python files in your submission.

If you are submitting a bonus assignment, make sure to submit those files separately, according to the instructions.

# Congratulations! You are finished with {{page.num}}!

