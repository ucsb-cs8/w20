---
assigned: 2019-11-06
desc: Creating a Scrabble word finder, Python lists, dictionaries and file I/O
due: 2019-11-13 08:59
layout: lab
num: lab05
ready: false
---

The goals for this lab are:

* more practice using Python lists
* practice using Python dictionaries
* read data (words) from a text file and put them into a list
* create a Scrabble word finder
* use list method sort() to sort words in order of descending point value
* print formatted output to the screen
* write formatted output to a file

# Step 1: Log on and bring up a terminal window

# Step 2: Create a directory in your cs8 directory named {{page.num}}.

(Remember the commands `cd`, `ls`, and `mkdir`)

# Step 3: Start IDLE

The terminal command for this is `idle3`.  When you have the IDLE window up, you are ready for some programming!

# Step 4: What to program?

In this lab assignment, you are going to make your own Scrabble word finder function, **scrabbleWords**.  In the end, you will simply 
input a string of letters and the program will print out (to the screen and to a file) a list of all the 
possible words you can make along with their point values in descending order (neglecting things like triple letter, 
double word squares, etc. in the real game of Scrabble).  For example, with "Buoni" as the input string of letters, the function prints this:

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
u         1
i         1
```

So, how did our program know which letter combinations were valid words?
......We have to specify a file of words, provided here:
[wordlist.txt](https://sites.cs.ucsb.edu/~buoni/cs8/labs/lab05/wordlist.txt).  
This file must be downloaded (right click and "save as") and put into your **lab05** directory
before you begin, so do that now.  Note that this file contains a fairly complete list of English words, so beware
that there may be some expletive and/or raunchy words.

Functions to Implement:

1. `createWordList(filename)` - return `L`
2. `canWeMakeIt(myWord, myLetters)` - return `True` or `False`
3. `getWordPoints(myWord, letterPoints)` - return `points`
4. `scrabbleWords(myLetters)` - NO return (just prints a formatted list and writes to file)

Function Details:

1. `createWordList(filename)` - return `L`.  Write a function which reads the file **filename** and returns a list **L** containing all the words in the file.  Note that the last character of every line of the file is the invisible "new line" character **'\n'** and needs to be sliced off.

 

2. `canWeMakeIt(myWord, myLetters)` - return `True` or `False`.  Write a function which answers the question: Can I form the word **myWord** from the string of letters **myLetters**?  The function should return a boolean **True** or **False**.  Converting **myLetters** to a list and using the **pop()** or **remove()** method may come in handy.

 

3. `getWordPoints(myWord, letterPoints)` - return `points`.  Write a function that calculates and returns the total point value of **myWord** given the Python dictionary object **letterPoints** which consists of **letter:pointValue** pairs.  Note that you do not need to create the **letterPoints** dictionary in this step - it is a parameter to our function and will be created in part 4.

 

4. `scrabbleWords(myLetters)` - NO return (just prints a formatted list and writes to file).  Here you will call upon your "helper functions" created in steps 1-3 to form a list of all the words (from **wordlist.txt**) that can be formed from the set of letters contained in **myLetters**. 

      (0) Create a Python list of words from **wordlist.txt** and name it **wordList**.  You will want to call helper function **createWordList**.

      (1) Create a list of all the words that we can make with **myLetters** by looping through every word in **wordList** and checking if it can be made with **myLetters** - name this list **myWords**.  You will want to call helper function **canWeMakeIt**.

      (2) Create a dictionary of **letter:pointValue** pairs - name it **letterPoints**.  The image below shows the Scrabble point value for each letter, but note that your dictionary keys should be the lower case letters.


      ![scrabble](scrabbleLetters.jpg)
    
      (3) Create a list of tuples consisting of (**pointValue**, **word**) pairs by looping through the list **myWords** and getting the point value for each word - name this list of tuples **pointWordList**.  To calculate **pointValue**, you will want to call helper function **getWordPoints**.

      (4) Sort **pointWordList** in descending order.  Now, you can use the list method **sort()** to sort the tuples according to their first entry, **pointValue**.  But **sort()** arranges a list in ascending order by default....can you think of a way to reverse this?

      (5) Print all the words followed by their point value.  Format the output so that your word is left justified in a field of width 4 more than the number of letters in **myLetters**, and the point value follows immediately afterwards.  You can do this with the **format** string method by carefully forming the '{...}' string first.  Hint: Use string concatenation with str(len(myLetters) + 4).

      (6) Write the same text as your formatted screen output from Part 5 to a text file.  Name the file the string of letters contained in **myLetters** followed by **.txt**.  So in my example where I call **scrabbleWords('buoni')**, the file that is created is **buoni.txt**.  Note that every time you want to write to a new line, you will need to include the newline character **'\n'** in your **file.write()** statement.  You can see what the output should look like in the example here: [buoni.txt](buoni.txt).  Do not download this file, but simply verify that when you run your program you produce this same file.

### \(^_^)/, you're finished!  Now have fun and experiment with the word finder ;-).

# Step 5: Saving your files

Save your functions in a Python file named **lab05_functions.py** in your directory **lab05**. 

# Step 6: Submit your work to Gradescope
