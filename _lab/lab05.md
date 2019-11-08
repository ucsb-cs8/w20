---
layout: lab
num: lab05
ready: true
desc: "Scrabble Word Finder: Python lists, dictionaries and file I/O"
assigned: 2019-11-06 10:00am
due: 2019-11-13 09:59am
---

In this lab, you'll get more practice with:

* using Python lists
* using Python dictionaries
* reading data (words) from a text file and putting them into a list
* creating a Scrabble word finder
* using list method `sort()` to sort words in order of descending point value
* formatting output and writing it to the screen and a file

## This lab should be done solo. 

Make sure that you adhere to the [Academic Integrity](https://studentconduct.sa.ucsb.edu/academic-integrity) standards and do/submit your own work.

## Getting started

* Step 1: Log on and open up a terminal window
This is done following the steps you have performed in lab00.
* Step 2: Create a directory in your cs8 directory named {{page.num}}.
* Step 3: Start IDLE. The terminal command for this is "`idle3 &`".  When you have the IDLE window up, you are ready for some programming!

## What is Scrabble?
[Scrabble](https://en.wikipedia.org/wiki/Scrabble) is a word game in which players take turns placing tiles with individual letters onto a game board. The words that players create earn points by counting the points for the letters according to the game rules. 

## What to program?

In this lab assignment, you are going to make your own Scrabble word finder function, `scrabbleWords()`.  In the end, you will input a string of letters and your program will print out (to the screen and to a file) a list of all possible words you can make along with their point values in descending order (neglecting things like triple letter, double word squares, etc. in the real game of Scrabble).  For example, if I input `'bouni'` as my string of letters, this is what I get:

```
>>> scrabbleWords('buoni')
obi      5
nub      5
nob      5
nib      5
bun      5
bio      5
bin      5
bi       4
uni      3
ion      3
on       2
nu       2
no       2
in       2
u        1
i        1
```

You will first define four helper functions, which you will then use in the main `scrabbleWords()` method. The section "Putting it all together" describes what `scrabbleWords()` method is supposed to do and how to call the helper functions, so if you want to set the big picture, you can start reading that section first.


## Getting started

So, how did our program know which letter combinations were valid words?......We have to specify a file of words, which you can find here: [wordlist.txt](https://ucsb-cs8.github.io/f19/lab/lab05/wordlist.txt).

This file must be downloaded (right click and "save as") and put into your `{{page.num}}` directory before you begin, so do that now. Note that you can also open the file in a new tab/window and copy/paste its contents into a new "wordlist.txt" file in your directory.

Use the starter code we have provided at the end of the lab.

### Functions to Implement:

1. **createWordList(filename)** - return a list of strings
2. **canWeMakeIt(myWord, myLetters)** - return True or False
3. **getWordPoints(myWord, letterPoints)** - return an integer representing the point value for a word
4. **outputWordPointPairs(pointWordList, myLetters, toFile)** - NO return (just prints a formatted list or writes it to a file).
5. **scrabbleWords(myLetters)** - NO return (just calls other functions)

### Function Details:

1) **createWordList(filename)** - return a list of strings.  Write a function which reads the file `filename` and returns a list containing all words in the file.  Note that the last character of every line of the file is the invisible "new line" character `'\n'` and needs to be sliced off.

2) **canWeMakeIt(myWord, myLetters)** - return True or False.  Write a function which answers the question: Can I form the word `myWord` from the string of letters `myLetters`?  The function should return a boolean True or False.  If the input is not the correct type then return `False`. 

Try to write an algorithm on paper first before attempting to write the code. Think about the list functions at your disposal and the tools you've learned up till now.

_Hint:_ Converting `myLetters` to a list and using its `pop()` or `remove()` method may come in handy. You do not need to use all letters in `myLetters`. It's possible that `myLetters` will contain multiples of the same letters. In the example above if `myLetters = "buoni"`  and `myWord = "boon"` then `canWeMakeIt` should return False. 

3) **getWordPoints(myWord, letterPoints)** - return an int representing the points for `myWord`.  Write a function that calculates and returns the total point value of `myWord` given the Python dictionary object `letterPoints` which consists of `letter : pointValue` pairs. If a character in `myWord` is not a key in the provided dictionary then its score value is 0. If any of the input is incorrect type then return 0. Note that you **do not need to create the `letterPoints` dictionary in this step** - it is a parameter to our function and will be created in `scrabbleWords()`.

4) **outputWordPointPairs(pointWordList, myLetters, toFile)** - NO return (just prints a formatted list or writes it to file).

* Write a function which will output the (pointValue, word) pairs in `pointWordList` to the screen or to a file depending on the bool value `toFile`. Refer to the function `scrabbleWords` for more details on `pointWordList`. When myLetters is "buoni", `pointWordList` might look like:

```
>>> pointWordList
[(5, 'obi'), (5, 'nub'), (5, 'nob'), (5, 'nib'), (5, 'bun'), (5, 'bio'), (5, 'bin'), (4, 'bi'), (3, 'uni'), (3, 'ion'), (2, 'on'), (2, 'nu'), (2, 'no'), (2, 'in'), (1, 'u'), (1, 'i')]
```
* When `toFile` is `False`,  print all the words followed by their point value.  Format the output so that your word is left justified in a field of width 4 more than the number of letters in `myLetters`, and the point value follows immediately afterwards.  You can do this with the `format` string method by carefully forming the `'{...}'` string first.

* If `toFile` is `True`, write the same text as your formatted screen output from above to a text file.  Name the file the string of letters contained in `myLetters` followed by ".txt".  So in the example above with scrabbleWords("buoni"), the file that is created is `buoni.txt`.  Note that every time you want to write to a new line, you will need to include the newline character `\n` in your `file.write()` statement.  You can see what the output should look like in the example here: 

**buoni.txt**
```
obi      5
nub      5
nob      5
nib      5
bun      5
bio      5
bin      5
bi       4
uni      3
ion      3
on       2
nu       2
no       2
in       2
u        1
i        1
```

You can simply verify that when you run your program you produce the same file if `myletters` == `"buoni"`.

### Putting it all together:

**scrabbleWords(myLetters)** - NO return (just calls the helper functions above).  Here you will call upon your "helper functions" created in steps 1-4 to form a list of all the words (from wordlist.txt) that can be formed from the set of letters contained in `myLetters`:

* Create a Python list of strings containing the words from `wordlist.txt`.  You will want to call helper function `createWordList()`.

* Create a list of all the words that we can make with `myLetters` by looping through every word in `wordList` and checking if it can be made with `myLetters`.  You will want to call helper function `canWeMakeIt()`.

* Create a dictionary of letter: pointValue pairs - name it `letterPoints`.  The image below shows the Scrabble point value for each letter, but note that your dictionary keys should be the lower case letters. Any character that is not shown in this image has a point value of 0. You don't have to add 0 point keys to your dictionary, rather make sure that your `getWordPoints` _uses a point value of 0 if a letter is not in the provided dictionary_.

![letter points](scrabble_letters.png){:height="250px"}

* Create a list of tuples consisting of (pointValue, word) pairs by looping through the list `myWords` and getting the point value for each word - name this list of tuples `pointWordList`.  To calculate pointValue, you will want to call helper function `getWordPoints()`.

* Sort `pointWordList` in descending order.  Now, you can use the list method `sort()` to sort the tuples according to their first entry, pointValue.  But `sort()` arranges a list in ascending order by default... can you think of a way to _reverse_ this?

* Call your `outputWordPointPairs()` and print your formatted string output to terminal. Then make a second call to `outputWordPointPairs()` to output to a ".txt" file named after the string in `myLetters`.

## Write test code

You must write your own tests using pytest for the following functions: 
* `createWordList(filename)`
* `canWeMakeIt(myWord, myLetters)`
* `getWordPoints(myWord, letterPoints)`

Write the test code before you implement the functions. This is a way of demonstrating that you understand what each function is supposed to do.

You should test the other two functions manually, although you are welcome to write test code for them as well.

Put your test code in `{{page.num}}_tests.py` and submit it along with your `{{page.num}}.py` file.
We recommend writing at least 3-5 test cases per function, but feel free to write more until you're confident in your solution.

Gradescope will use test cases different from the tests that you will wrote in `{{page.num}}_tests.py`.

### What {{page.num}}.py could look like

# `{{page.num}}.py`
```python
# Student: (insert your name here)
# Make sure to read the comments for each function. 

def createWordList(filename):
	'''
	Reads in the in the filename and creates a list L which contains all the words. 
	You must remove the newline character ('\n') at the end of each word.	

	:param filename: the string which represents the filename you are reading from.
	:return: A list of strings	
	'''
	return "stub"


def canWeMakeIt(myWord, myLetters):
	'''
	Takes in a word and a string of letters and checks whether the word can be made with those letters.	

	:param myWord: the string we are checking.
	:param myLetters: a string of letters we can use to build a string. 
	:return: A bool whether the string can be made or not.	
	'''
	return "stub"


def getWordPoints(myWord, letterPoints):
	'''
	Returns the total points of a given word. 

	:param myWord: the string you want to calculate points for
	:param LetterPoints: a dictionary of (letter, value) pairs which gives the point value of each letter
	:return: The total point value of the word.	 
	'''
	return "stub"


def outputWordPointPairs(pointWordList, myLetters, toFile):
	'''
	Outputs the contents of pointWordList in a specified format to a file (see lab instructions).
		
	:param pointWordList: a list of tuples to output to, with each tuple 
	 containing a (pointValue, word) pair
	:param myLetters: a string that you will name the file with if toFile is True
	:param toFile: a boolean to decide whether I want to print to file or not. 
	If True then output to file else output to terminal.
	:return: None
	'''
	return


def scrabbleWords(myLetters):
	'''
	A function which takes in a string of letters and shows what words can be constructed from it.
	It should use the helper functions defined above to do so. 

	:param myLetters: a string of letters we are using. 
	:return: None
	'''
	return
```


### What {{page.num}}_tests.py should look like

```python
# Student: (insert your name here)
import pytest
from {{page.num}} import createWordList

def test_createWordList_0():
	# Example test
	# Write to a file with words in it
	words = ['computer', 'science', 'python']
	outfile = open('test_file_0.txt', 'w')
	for item in words:
		outfile.write(item +'\n')

	outfile.close()

	# Read the file with words created in it to test if createWordList
	# creates a list of words correctly.
	newlist = createWordList('test_file_0.txt')
	assert(len(newlist) == len(words))

	for i in range(len(words)):
		assert(words[i] == newlist[i])

def test_createWordList_1():
	#Your test code
....


from {{page.num}} import canWeMakeIt

def test_canWeMakeIt_0():
	assert(canWeMakeIt('ape','pae') == True)

...
from {{page.num}} import getWordPoints
letterPoints = {'a':1, 'b':3, 'c':3, 'd':2, 'e':1, 'f':4,\
		'g':2, 'h':4, 'i':1, 'j':8, 'k':5, 'l':1,\
		'm':3, 'n':1, 'o':1, 'p':3, 'q':10, 'r':1,\
		's':1, 't':1, 'u':1, 'v':4,	'w':4, 'x':8,\
		'y':4, 'z':10}

def test_getWordPoints_0():
	assert(getWordPoints('ape',letterPoints) == 5)
...
```

# Running the final product

You can load your `{{page.num}}.py` and run `scrabbleWords` in IDLE's interactive shell. In `scrabbleWords` you <strong>must</strong> make one call to print to the console with `outputWordPointPairs` where `toFile = True`, and another call to write to a file with `outputWordPointPairs` where `toFile = False`. Gradescope test cases will fail if you forget to write your output to a file.

# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "{{page.num}}" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files.

Thanks to Matthew Buoni for this lab!
