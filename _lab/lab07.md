---
layout: lab
num: lab07
ready: false
desc: "String Formatting, Random, and File IO"
assigned: 2019-11-20 9:00am
due: 2019-11-27 08:59am
---

In this lab, you'll get more practice with:

* Using `randrange`
* Testing your functions with pytest
* Using String Formatting
* Reading and processing files

## This lab should be done solo.

# Instructions

In this lab, you will need to create two files:
* `{{page.num}}.py` - file containing function definitions
* `{{page.num}}_tests.py` - file containing test cases
* <strong>Please comment your name / perm at the top of each file.</strong>
* <strong>Make sure to have a docstring for every function.</strong>

Starter code is provided for you at the bottom of this page.

1.  Create a directory called ~/cs8/{{page.num}} (using the `mkdir` command) and `cd` into that directory.
2.  Use `idle3` (you might try `idle3 &` if you want to be able to type commands on your terminal window after IDLE opens).
3.  Use "New File" to create empty files called `{{page.num}}.py` and `{{page.num}}_tests.py` in that `~/cs8/{{page.num}}` directory.
4.  Download `input1.txt` and `input2.txt` in that `~/cs8/{{page.num}}` directory. These are used when running pytest on {{page.num}}_tests.py.

You are encouraged to try submitting to Gradescope periodically for several reasons:

* You can get partial credit if some of your tests pass for some of your functions.
* You will have a backup of your file in case you accidentally delete yours, or in case your laptop dies.
* You can move code between your laptop and CSIL by downloading your submitted code from Gradescope.

# Some notes about printing the dice distribution

An example `printDistribution` function will appear as follows:

```
Distribution of dice rolls

 2:     7 (  2.8%)  *******
 3:    14 (  5.6%)  **************
 4:    29 ( 11.6%)  *****************************
 5:    26 ( 10.4%)  **************************
 6:    34 ( 13.6%)  **********************************
 7:    41 ( 16.4%)  *****************************************
 8:    30 ( 12.0%)  ******************************
 9:    23 (  9.2%)  ***********************
10:    23 (  9.2%)  ***********************
11:    16 (  6.4%)  ****************
12:     7 (  2.8%)  *******
------------------------------
250 rolls
```

* The first line is simply "`Distribution of dice rolls`" followed by an empty line.
* The dice rolls are printed in a histogram format, one for each roll with additional information.
	* Your solution should print this portion while iterating through the diceTally in a loop using the `.format` function. <strong>Do not simply write 11 print statements using `.format`.</strong> 
	* The dice roll values will have two spaces right-justified followed by a `':'` character.
	* Six spaces are reserved to print number of times a particular roll occurred, which is right-justified, followed by an empty space and open parenthesis, `'('`, characters.
	* 5 spaces are reserved for the actual percentage value, with one space for the floating point value. This is followed by the `'%)'`, and two blank spaces.
	* The `'*'` character is printed the number of times a particular dice roll occurred.
* 30 hyphens `-` are printed after the diceRolls are printed
* The number of rolls are then printed.
* Using your function definitions, the following statement should display an output similar (but not exactly since `rollDice` is random) to the output shown above:

```>>> printDistribution(rollDistribution(250))```

# Some notes about the File I/O functions

Two input files are provided for you to test your functionality. One additional input file is not provided and will be tested with your submission on Gradescope.

Note that all words are separated by a whitespace character, and a word contains only alpha-numeric characters that does not include punctuation characters. For simplicity, you may assume the text only contains the `,.!?;` punctuation characters. Your code will need to split and strip the text file string appropriately.

# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "Lab06" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.


# `{{page.num}}.py`

```python
# lab06.py

# Student(s): (insert name and perm number here)

from random import randrange

def rollDice():
    '''
    (10 points)
    Function that returns the sum of rolling two six-sided dice.
    - Note that the possible sum of rolling two dice is [2-12].
    However, this distribution is not uniform (i.e. rolling a 2 does
    not have the same probability as rolling a 6). Your function must
    use randrange correctly to account for this.
    '''
    return "stub"


def rollDistribution(n):
    '''
    (10 points)
    Function that rolls a pair of dice n number of times. Returns a
    list of ints, diceTally, that keeps track of the number of times
    a certain sum occurs.
    - Use the technique discussed in lecture where you can create a
    list of 13 integers, where the index of the list represents a
    particular dice roll value, and the value of that position represents
    the number of times that dice roll occurred.
    - Note: diceTally[0] and diceTally[1] will always be 0 since
    having rolling a pair of dice will never result in 0 or 1.
    - Your algorithm should call rollDice() n number of times when
    populating your list.
    '''
    return "stub"


def printDistribution(diceTally):
    '''
    (20 points)
    Function that prints the diceTally distribution in a specific
    format (see lab instructions for more details).
    - This function does not return anything since it is simply
    printing to the console.
    - Note: Your algorithm must iterate and print each dice roll value in
    a loop. Do not simply have 11 print statements for each dice roll value.
    - Be VERY PRECISE in your format. Each character matters for full credit.
    '''
    return


def totalWords(filename):
    '''
    (20 points)
    Reads the file with filename into your function and returns
    the number of words in the file.
    - Words are separated by whitespace characters, but does not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - The split and strip functions may be useful in your implementation.
    - Your function should open the file for reading, and close
    the file before returning.
    '''
    return "stub"


def longestWord(filename):
    '''
    (20 points)
    Reads the file with filename into your function and returns
    the longest word in the text file.
    - Words are separated by whitespace characters, but does not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - In the case of a tie, the 1st occurrence of the longest word
    is returned.
    - The split and strip functions may be useful.
    - Your function should open the file for reading, and close
    the file before returning.
    '''
    return "stub"


def charactersPerWord(filename):
    '''
    (20 points)
    Reads the file with filename into your function and returns
    the average number of characters per word.
    - Words are separated by whitespace characters, but does not include
    the following punctuation characters (,.!?;). You can assume contractions
    count as one word (i.e. "don't", "you'll", etc. are one word).
    - The split and strip functions may be useful.
    - Your function should open the file for reading, and close
    the file when done.
    '''
    return "stub"

```

