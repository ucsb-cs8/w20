---
assigned: 2020-02-25 9:00am
desc: "String Formatting and File IO"
due: 2020-03-03 08:59am
layout: lab
num: lab07
ready: true
---

In this lab, you'll get to practice:

* Testing your functions with pytest
* Using String Formatting, using `split()` and `strip()`
* Reading and processing files
* Doing basic text processing

# This lab should be done solo.

# About this lab

In this lab, you will be opening/closing text files,
writing code to read the file contents, and
counting the total and the unique words in the file.

## Instructions

In this lab, you will need to create the following files:
* `{{page.num}}.py` - a file containing function definitions
* `{{page.num}}_tests.py` - a file containing test cases
* `inputX.txt` files that you used for testing
* <strong>Please comment your name / perm at the top of each file.</strong>
* <strong>Make sure to have a docstring for every function.</strong>

Starter code is provided for you at the bottom of this page.

## Some notes about the File I/O functions

* Create four files `input1.txt`, `input2.txt`, `input3.txt` and `input4.txt` in the `~/cs8/{{page.num}}` directory. 
* Use these input files to test your functionality: feel free to change these files to add a small number of words (2-10) to make sure that you can verify that your function is working correctly. 
* Make sure you can correctly remove all requested punctuation characters; test for contractions, e.g., words like "don't". 
* Make sure to test a file that contains more than one line.

Here are simple examples you should try:

**input1.txt**
```
hello
hello
hello world
```

**input2.txt**
```
hello world
world
world
```

**input3.txt**
```
Hello! Today is a lovely day, isn't it?
```

**input4.txt**
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quid est, quod ab ea absolvi et perfici debeat? Philosophi autem in suis lectulis plerumque moriuntur. Paulum, cum regem Persem captum adduceret, eodem flumine invectio? Urgent tamen et nihil remittunt. 

Hoc positum in Phaedro a Platone probavit Epicurus sensitque in omni disputatione id fieri oportere. Eorum enim omnium multa praetermittentium, dum eligant aliquid, quod sequantur, quasi curta sententia; Duo Reges: constructio interrete. O magnam vim ingenii causamque iustam, cur nova existeret disciplina! Perge porro.

Sed ea mala virtuti magnitudine obruebantur. Iam in altera philosophiae parte. Apud ceteros autem philosophos, qui quaesivit aliquid, tacet; Itaque sensibus rationem adiunxit et ratione effecta sensus non reliquit. Sed ille, ut dixi, vitiose. Ergo ita: non posse honeste vivi, nisi honeste vivatur? 

```


These files are used when running pytest functions in `{{page.num}}_tests.py`.

**We will be using additional input files to test your submission on Gradescope**.


## Read all words into a list
To open and close the file within every function to get the list of words, let's write a helper function `getAllWords()`. The `split()` function will be useful to achieve this.

```python
def getAllWords(filepath):
    '''
    Returns a list of all words 
    from the given filepath.
    The function opens the file for reading,
    and closes the file before returning.
    '''
    return "stub"
```


For example, 
`getAllWords("input1.txt")` returns `["hello", "hello", "hello", "world"]`; 
`getAllWords("input2.txt")` returns `["hello", "world", "world", "world"]`.


## Clean the resulting words

`getCleanWordList` reads a file with given filepath and return a list of all words in the file with all the specified  punctuation characters (`,.!?;`) removed (you might find the `strip()` function helpful).

Note that all words are separated by whitespace characters, and a word contains only characters that **do not** include the following punctuation characters: 
`,.!?;"`.
Your code will need to split and strip the strings from the text file appropriately.

For example, 
`getCleanWordList("input3.txt", ",.!?;")` returns `["Hello", "Today", "is", "a", "lovely", "day", "isn't", "it"]`.

Hint: you need to call `getAllWords` inside `getCleanWordList`. 

```python
def getCleanWordList(filepath, charsToRemove):
    '''
    Read a file with given filepath, return a list
    of all words from the file with the specified
    characters that are stored in the string called
    charsToRemove are removed.
    Empty strings should not be added to the
    resulting list of cleaned words.
    '''
    return "stub"
 ```

## Get unique words (a.k.a. Remove the duplicates)

`getUniqueWords` reads a file with given filepath and returns a list of all unique words that appeared in the file. 

For example, 
`getUniqueWords("input1.txt")` returns either `["hello", "world"]` or `["world", "hello"]`; 
`getUniqueWords("input2.txt")` returns either `["hello", "world"]` or `["world", "hello"]`. 

Hint: you need to call `getCleanWordList` first.

```python
def getUniqueWords(filepath):
    '''
    Return a list of unique words that appeared 
    in the file with the given filepath.
    '''
    return "stub"
```

## Count the number of words
`getWordCount` reads a file with given filepath and returns a list of lists, where **each element is a list** of two elements in the format `[word, count]`. 

For example, 
`getWordCount("input1.txt")` returns either `[["hello", 3], ["world", 1]]` or `[["world", 1], ["hello", 3]]`; 
`getWordCount("input2.txt")` returns either `[["hello", 1], ["world", 3]]` or `[["world", 3], ["hello", 1]]`.    

Hint: you need to call `getCleanWordList` and `getUniqueWords` in this function. 

```python
def getWordCount(filepath):
    '''
    Get the frequency of each unique word 
    in the file with given filepath, and return 
    a list of lists where each element is a list 
    of two element in the format [<word>, <count>].
    '''
    return "stub"
```

## Find frequently occuring words

Finally, `mostCommonWord` reads a file with given filepath, and returns the most common word in the file. 

```python
def mostCommonWord(filepath):
    '''
    Reads the file from filepath in your function
    and returns the most common word in 
    the file (i.e.,the word with the highest frequency).
    In the case of ties (i.e., more than one word
    with the same max count, then return the word
    that occurs earliest in dictionary order
    (remember string comparisons).
    - Use getWordCount() helper function to count 
    the frequency of each word.
     '''
    return "stub"
```

### Notes on computing the most common words

If you run `mostCommonWord("input1.txt")`, this function should essentially return the mode value from the file (the word that occurs most often).
Use `getWordCount` to help you first count the words in a file, then `mostCommonWord()` can find the max count, save all words with that count and return the word that occurs first in ditionary order

* `mostCommonWords("input1.txt")` Test that you are able to return "hello" as the most frequently occuring word. 
* `mostCommonWords("input2.txt")`, the function should return `'world'`.

Test the other functions accordingly, verifying on a simple input file that the results are correct.


# Upload `{{page.num}}.py` and `{{page.num}}_tests.py` and .txt files to Gradescope.

Once you're done with writing your functions, navigate to the Lab assignment "{{page.num}}" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_tests.py` files together with your **.txt** input files.
**Submit all your files all at once**, instead of uploading them one by one: each submission overwrites the previous files. 
You should be able to go to Gradescope to see both Python files and the text files in your submission.


### Congratulations! You are finished with the lab!
Congratulations, you are finished with this lab!  
