---
layout: lab
num: lab08
ready: true
desc: "Recursion"
assigned: 2019-11-27 10:00am
due: 2019-12-06 05:59pm
---

In this lab, you'll get more practice with:

* Writing recursive functions
* Writing tests in pytest for your recursive functions

## This lab must be done solo.

## This lab is optional. 
If you choose to complete it, whatever points you earn on this assignment will be added to your overall lab grade (which could only boost your grade).

Additionally, recursion will be on the final exam, so even if you don't complete the lab, you need to be comfortable writing recursive functions.


## All solutions in this lab must use recursion in order to receive credit.

You may not use any functions that are not in the book and that we have NOT discussed in lecture.

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_student_tests.py` - file containing test cases. A sample test is provided for each function. You will write 3 - 5 (or more) additional tests per function to confirm your code works as expected.
    * As usual, you want to test a variety of values: test the boundary of accepted inputs, check the negative numbers, "empty" variables, or really large values, if applicable.
    * Read through the docstring and make sure you are testing (and passing!) all conditions outlined there.
* <strong>Please add  comment with your name at the top of each file.</strong>

Starter code is provided for you at the bottom of this page.

You will complete the portions in the starter code by doing the following:

1.  Create a directory called `~/cs8/{{page.num}}` (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_student_tests.py` in that `~/cs8/{{page.num}}` directory.
4.  ONE AT A TIME, copy the function definitions (**including the docstrings!**) from the starter code, write tests that go along with those functions in `{{page.num}}_student_tests.py`, and get your tests to pass.
   * Before you move on to the next function definition and <em>its</em> tests, get all of the tests you just wrote to pass.
   * Repeat this until you have ALL of the function definitions and their tests, and all of them pass.


## Recursion walk-through

### Base case

**Remember**, recursive functions should always **`return`** their result. Every case has to have a `return`. The recursive case should always **`return`** the result that involves _calling the function itself_ on the input that gets you closer to the base case.

Whenever you are writing a recursive function, you need to first identify the **base case(s)**: the simplest case for which the function works that will stop the recursion. 

For example, imagine you are given an integer `num` as an input and you want to reverse its digits and return the reversed digits as a string. The base case in this scenario would be a single-digit `num`. In your function, you can simply return the string consisting of `num` if it's between 0 and 9 (since there is nothing for you to reverse).

```python 
def reverseDigits( num ):
    """
    Reverse the digits of an 
    integer >0, using recursion.
    Return a string that contains
    the reversed number.
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
I recommend thinking of _the next simplest input_ and how you can reduce that input to the base case (i.e., use base case as part of your solution for this case). What action do you need to take once you get the result of the base case to obtain the next simplest case?

In our case, the next simplest input would be a two-digit number, e.g., 16.
You will need to decide if you are going to be reversing the number by going front-to-back or back-to-front. Why? Because you need to decide if you are going to be assembling the reversed digits at the end or at the beginning of the string that contains the base case. For this example, I'm going to use the fact that modulo operator `%` is going to give me the remainder of the division by 10, in order to get the last digit. Since I'll be processing the number from the last digit, I'll be assembling the rest of the digits **after** the "last digit" that will be placed at the beginning of the resulting string.

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
    """
    if 0 <= num <= 9:
        return str(num)

    elif num > 0:
        return str(num%10) + reverseDigits(int(num/10))
```

Add the remaining tests to verify that it works as expected.

```python

def test_reverseDigits_16():
    assert reverseDigits(16) == '61'

def test_reverseDigits_162():
    assert reverseDigits(162) == '261'

def test_reverseDigits_1623():
    assert reverseDigits(1623) == '3261'

```


# Upload `{{page.num}}.py` and `{{page.num}}_student_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_student_tests.py` files.

## Your solutions must use recursion in order to receive credit.

```python
# Student: (insert name here)
# PERM number
# Make sure to include and read the comments for each function.

def recursiveDigitSum(n):
    '''
    Computes the sum of digits of a positive integer n
    - Your solution must use recursion in order to receive credit.
    '''
    return "stub"


def recursiveSubstring(s, sub):
    '''
    The parameters sub and s are strings. This function computes if a
    the string sub exists in s.
    - Your solution must use recursion in order to receive credit.
    '''
    return "stub"


def recursiveReverseList(L):
    '''
    Tbe parameter L is a list containing any items. This function returns
    the list L in reverse order.
    - Your solution must use recursion in order to receive credit.
    '''
    return "stub"

```

The following functions you might see in later CS courses or during the programming interviews, so it would be helpful for you to work on developing an algorithm for solving them.


#### Function to find if two strings are anagrams

Two strings are anagrams if the letters can be rearranged to form each other. For example, "Eleven plus two" is an anagram of "Twelve plus one". Each string contains one 'v', three 'e's, two 'l's, etc. Similarly "Rats and Mice" and "in cat’s dream" are anagrams of each other.

Write your own implementation of a function called `isAnagram` that takes two strings as arguments and returns a boolean true if the two strings are anagrams, otherwise, it returns false. The function should not be case sensitive and should disregard any punctuation or spaces. 

#### Function to check if an input string is a palindrome

A palindrome is a word, number, or other sequence of characters which reads the same backward as forward, such as "madam" or "racecar".

Write your own implementation of a function `isPalindrome` to check if a string is a palindrome. For example: “redivide” is not a palindrome, while “detartrated” is a palindrome. Ignore case when comparing characters of the string.

The function returns true if an input string is a palindrome and false if it is not. You can do this by checking if the first character equals the last character, and so on. You should use a recursive implementation. Hint: remember how string slicing works.