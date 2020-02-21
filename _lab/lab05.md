---
assigned: 2020-02-11
desc: Encryption and Decryption
due: 2020-02-18 08:59
layout: lab
num: lab05
ready: true
---

# Warm-ups to Help with the Main Part of the Lab

In this lab you'll get to:

* Use modulo `%` operator to mimic looping around a list or a string
* Use `for` loops to output the contents of a list/string
* Use the accumulator pattern
* Deconstruct the essential cryptographic processes of encryption and decryption
* Create encryption and decryption algorithms that use a secret key
* Write "helper" functions that are called by other functions
* Decode a message from your instructor :-)

* * *

Let's get started by creating a file **{{page.num}}.py**.

**IMPORTANT**: For all functions, even if you are given code for it, you need to verify that the code is running correctly. As such, you want to always write your own tests to verify that you are able to correctly return the requested values. 

## Example of the use of modulo 
Given a random number `num`, use it to index a list and advise the user on which step to take to succeed in this course.
The user can provide any non-negative number `num`, and this number may be larger than the length of the list that we want to index. 

Recall that indexing a list at an index greater than its length gives us an out of range error. For example:

```python
>>> numbers = list(range(0,5))
>>> numbers
[0, 1, 2, 3, 4]
>>> numbers[7]
Traceback (most recent call last):
  File "<pyshell#10>", line 1, in <module>
    numbers[7]
IndexError: list index out of range
```

Because the user can provide any non-negative number, its value needs to somehow map any non-negative `num` to one of the elements stored in the list. Given that there is a fixed number of elements in the list, in order to always pick an element from the list, we can think of numbers that are greater than `len(stepsToSuccess)` mapping to the remainder that's left when we divide `num` by the size of the list. So if we apply this logic to the example above, instead of indexing at `numbers[7]`, we would index at `numbers[2]`, because there are 5 elements in the list, so `7 % 5` gives us 2. 

Now, use this idea of "mapping to the remainder" to modify the function below.
Note that you shouldn't hard-code values and instead use the functions that would provide the correct value to you (i.e., for the number of elements, use `len` instead).

```python
def getAdvice(num):
    """
    Given an input number >= 0,
    return an element from the list,
    which we'd land on if we loop 
    around the list num times.
    """

    stepsToSuccess = [ "Keep track of deadlines", \
                     "Read the book", \
                     "Do the homework yourself", \
                     "Attend lectures", "Ask questions", \
                     "Attend labs", "Enjoy studying" ]
    
    if num > 0 :
        advice = stepsToSuccess[num % ...] # TODO: replace ...
        return ...
```

Now is a good time to create **{{page.num}}_tests.py** and use the provided pytests to check if your function is correct.
Add your own tests to verify that you are able to correctly return every value from the list. If you don't write any other tests, at least write two tests that verify that your function correctly returns the first and the last requested values.


```python
def test_getAdvice_1():
        assert getAdvice(6) == "Enjoy studying"
def test_getAdvice_2():
        assert getAdvice(100) == "Do the homework yourself"
def test_getAdvice_3():
        assert getAdvice(-1) == None
```

## Use a `for` Loop and Keep Track of Indices

Recall that a `for` loop has the following structure:

```
for VARIABLE in COLLECTION:
    #loop body
    one or more statements
```

Let's start with an easy `for` loop example to remind us how to use a `for` loop.
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
  print(fruit)
```
This code goes through the list to print out "apple", "banana", and "cherry". 

Now, use this code as a basis for a function `print_list_index`, which would produce the following output:

```
apple is at index 0
banana is at index 1
cherry is at index 2
```

Here's the function definition:

```python
def print_list_index( aList ):
    """
    Given an input list aList,
    display "<item> is at index <N>"
    for each item in the list.
    """
    pass # TODO: replace with the proper output
```

Test it by running it with the following examples:
```
>>> print_list_index(fruits)
apple is at index 0
banana is at index 1
cherry is at index 2

>>> print_list_index(["A", "B", "C"])
A is at index 0
B is at index 1
C is at index 2
```

Now, instead of indexing a list, you can write a function that finds at which index/indices a character is found within a string.

 Write a function that uses a `for` loop and the `range` function to return a list of all indices at which a `char` occurred in the `text`. 
For example, if the input `text` is `Mississippi` and `char` is `s`, the function should return `[2, 3, 5, 6]`; if the `char` is `M`, the function should return `[0]`; if the `char` is `i`, you should get `[1, 4, 7, 10]`.

```python
def get_index_list(text, char):
    """
    Given text and a single character char,
    which are both strings, return a list
    that contains the indices at which char 
    occurred in the text.
    If text or char is not a string, or if
    a char is longer than 1 character,
    return None. 
    If char is not found, return an
    empty list.
    """
    return "stub"
```

# Encryption and Decryption

First, some important background on cryptography.

Read the following instructions carefully to make sure you understand the process and what is being asked of you.

**Encryption** is a procedure that is used to transform a message (referred to as _plaintext_) in order to prevent anyone except the intended recipient from reading that data. The output of the process is called _ciphertext_, and it should be unintelligible without knowledge of the key and decryption algorithm.

**Decryption** is the reverse procedure: the process of making the encrypted data readable.

## Substitution Cipher

We will start with a simple substitution cipher, which illustrates the process of encryption and decryption. (Read more about substituion cipher: <https://en.wikipedia.org/wiki/Substitution_cipher>.)

In a simple substitution cipher, we will replace each character of the plaintext alphabet with the corresponding ciphertext alphabet. 

Here's [an example from WikiHow](https://www.wikihow.com/Create-Substitution-Ciphers) that uses only upper-case letters in the alphabet:
![](substitution-cipher-wikihow.png)

### Generate the plaintext and ciphertext alphabets

To generate the plaintext alphabet, you need to assemble a string of all characters that should be included in your encryption algorithm.  We will refer to this string as **alphabet**. 

The alphabet should include all the lower case letters, followed by all the uppercase letters, then a space, a comma, a period, a hyphen (`'-'`), a tilde (`'\~'`), and a pound symbol (`'#'`). There should be no spacing between the symbols in the resulting alphabet; the only exception being the single space you are asked to add after the uppercase letters. Ensure that your alphabet is correct before proceding to prevent unexpected results.

Typing letters manually is tedious and error-prone, so you shouldn't do it. Instead, use the module `ascii_lowercase` imported from the `string` library to construct the alphabet string. (Hint: you can either use `str.upper()` or `ascii_uppercase` to get the uppercase letters.)

```python
import string
def createAlphabet():
    """
    createAlphabet returns a string that includes 
    all lowercase letters,
    followed by all upper-case letters,
    then a space, a comma, a period, a hyphen('-'), 
    a tilde('~'), and a pound symbol ('#'). 
    NOTE: the order of characters in the alphabet is
    very important!
    In other words, the string being returned will be
    'abcdef...xyzABCDEF...XYZ ,.-~#' (the ellipses ...
    hide the alphabet letters)
    """
    lc = string.ascii_lowercase
    uc = ...
    return lc + uc + " ,.-~#"
```


Let's make our cipher alphabet be _the reverse_ of the input plaintext alphabet.

Remember to write out your algorithm or the steps in pseudocode to make sure you understand how to approach the solution. Since you want to reverse the string, you want to find a way to move from the end of the input string toward the beginning... sounds like the solution will need `len()` and loops.

```python
def createCipher( alphabet ):
    """
    Given the input plaintext alphabet,
    return the reversed input.
    NOTE: createCipher() returns a string.
    """
    return "stub"
```

You can test your `createCipher` function, first, with something simple to verify that it works, and then, by passing `createAlphabet()` as an input to verify that it was reversed correctly.

```python
def test_createCipher_ABC():
    assert createCipher("ABC") == "CBA"
```

Note that there are more Pytest functions at the bottom of this page.
Feel free to add your own tests.
Add your pytest functions to the file **{{page.num}}_tests.py**.

 
### Encrypting text
Note that for this algorithm to work, the letters of the alphabet (and any other characters that should be allowed in the plaintext), as well as their order, **must be fixed and should be the same** for both encryption and decryption. For example, if you encrypt with the 26 letter English alphabet and decrypt with the 27-letter Spanish alphabet (including ñ), you won't get the correct decrypted plaintext back.

Now that we have a way to generate our alphabets, let's try to encode a sample message by substituting every character from our input `plaintext` with the corresponding character from the `cipher` alphabet.

```
BASIC PSEUDOCODE
# Given the plaintext, alphabet, cipher
# Create a string that will hold the ciphertext
# Loop through the plaintext
#   For every character in plaintext
#   Find its position/index in the alphabet
#   Get the character at the same index in cipher
#   Add the cipher-char to the ciphertext string
# Return the resulting ciphertext
```

You can now update the above pseudocode with the additional checks that are listed in the docstring of the `simpleEncode` function.

```python

def simpleEncode(plaintext, alphabet, cipher):
    """
    Given plaintext to encode,
    an alphabet and a cipher alphabet, return
    the encoded ciphertext.
    If the lengths of the alphabet and
    cipher are not the same, return -1.
    If a character from plaintext is not
    found in the alphabet, return None.
    """
    return "stub"
```

Now, you can encode a message such as "hi", by calling your function with this message, using `createAlphabet()` as the second argument, and using the same function (`simpleEncode) as an input into `createCipher`, which will return the third argument that `simpleEncode` needs.

```python
>>> simpleEncode("HI", createAlphabet(), createCipher(createAlphabet()))
'yx'
```

### Decrypting text

Now that we have successfully converted our plaintext into a gibberish ciphertext, we can write the function that will "undo" our encryption and will decrypt the ciphertext back into plaintext.

```python
def simpleDecode(ciphertext, alphabet, cipher):
    """
    Given ciphertext to decode,
    an alphabet and a cipher alphabet, return
    the decoded plaintext.
    If the lengths of the alphabet and
    cipher are not the same, return -1.
    If a character from ciphertext is not
    found in the cipher alphabet, return None.
    """
    return "stub"
```

You should be able to run `simpleDecode("yx", createAlphabet(), createCipher(createAlphabet()))` and get back the original string "HI" that you encoded above.


See if you can decode this message from your mentors:
```
zO,#MfWR~dfhRLf#O,fRSfMY,fOXZYMfMO#-Vdfv,,QfLQfMY,fZRR.fJROVd
```


# Caesar cipher

A Caesar cipher is one of the simplest and most widely known encryption algorithms. In this algorithm, each letter of the plaintext is replaced by a different letter that is some fixed number of positions later in the alphabet. For example, with a shift number of 4, _A_ would be replaced by _E_, _B_ would become _F_, and so on. 

In the next lab, you will write an encryption / decryption algorithm for the Caesar cipher.

In the rest of this lab, you will create two functions, which will be used as helper functions in the Caesar cipher.

Functions to Implement:

* `getCharacterForward(character, key)` - return right-shifted character based on key
* `getCharacterBackward(character, key)` - return left-shifted character based on key

Function Details:

You already created a function that produces an alphabet: `createAlphabet()`. 

**IMPORTANT**: make sure that you use `createAlphabet()` as the helper function to generate the alphabet used by the encryption/decryption routines. You should be able to change the alphabet returned by `createAlphabet()` and all your other functions should still work correctly.

* `getCharacterForward(char, key)` - return right-shifted character. 
    * `char` is a single character from the alphabet
        * if `char` is not a single character, return `None`
    * `key` is an integer that indicates the number of steps to take
        * if `key` is not an integer, return -1

Upon receiving a character and a “key” this function gets the character to the right ("forward") of `char` in the alphabet. To do so, it looks at the index of `char` in the alphabet and moves forward by the number of steps specified in the key. 

For example, if you call this function with parameters “b” and 2 the result will be “d”. It is because “d” is 2 characters away from “b”. As another example, if you call this function with the input “a” and the total number of characters (`len(createAlphabet()`) the result will be “a” because you move it to the number of total characters and you will eventually land on the first character that you started the process on.

```python
def getCharacterForward(char, key):
	"""
	Given a character char, and an integer key, 
    the function shifts char forward `key` steps.
    Return the new character.
    If `char` is not a single character, return `None`.
    If `key` is not an integer, return -1.
	"""
	return "stub"
```

* `getCharacterBackward(char, key)` - return left-shifted character. 

This function is performing the opposite behavior of the previous function. After being called, it gets the character to the left of `char` by moving "backward" by the specified `key` positions in the alphabet. For example, if you this function with the parameter “c” and 2 the result is “a” and if you call it with “a” and `len(createAlphabet())` the result is “a” because you are essentially moving over all the characters and so the result is the initial character.

```python
def getCharacterBackward(char, key):
	"""
	Given a character char, and an integer key, 
    the function shifts char backward `key` steps.
    Return the new character.
    If `char` is not a single character, return `None`.
    If `key` is not an integer, return -1.
	"""
	return "stub"
```

# Pytest Functions for {{page.num}}_tests.py

```python
# lab05_tests.py
from lab05 import createAlphabet

'''Note: for some of these to work, your createAlphabet function must be working properly'''


from lab05 import createCipher

def test_createCipher_1():
    assert createCipher('lmnop') == 'ponml'
    
def test_createCipher_2():
    assert createCipher('asdfghjkl') == 'lkjhgfdsa'
    
def test_createCipher_3():
    assert createCipher(' &#A.,?QP') == 'PQ?,.A#& '
    
#######################################################################################################
from lab05 import simpleEncode

def test_simpleEncode_1():
    assert simpleEncode('beep beep boop', createAlphabet(), createCipher(createAlphabet()))  == '~,,Qf~,,Qf~RRQ'
    
def test_simpleEncode_2():
    assert simpleEncode('only these characters have to be in alphabet', 'pq', 'st' ) == None

def test_simpleEncode_3():
    assert simpleEncode('only these characters have to be in alphabet', 'onlythescarvbip ', 'pasdfghjklzxcvbn' ) == 'pasdnfghjhnkglzlkfhzjnglxhnfpnchnvanlsbglchf'

def test_simpleEncode_4():
    assert simpleEncode('thisIsMyPlainText', 'someAlphabet','wrongLength') == -1
    
#######################################################################################################
from lab05 import simpleDecode
def test_simpleDecode_1():
    assert simpleDecode('~,,Qf~,,Qf~RRQ', createAlphabet(),createCipher(createAlphabet())) == 'beep beep boop'

def test_simpleDecode_2():
    assert simpleDecode('tbamret s==sida', createCipher('abtes= rmid'), createCipher(createCipher('abtes= rmid'))) == 'midterms == bad'

def test_simpleDecode_3():
    assert simpleDecode('pasdnfghjhnkglzlkfhzjnglxhnfpnchnvanlsbglchf','onlythescarvbip ', 'pasdfghjklzxcvbn') == 'only these characters have to be in alphabet'

def test_simpleDecode_4():
    assert simpleDecode('abc','abg','ghj') == None

def test_simpleDecode_5():
    assert simpleDecode('abc','abg','ghzj') == -1

#######################################################################################################
        
from lab05 import getCharacterForward
'''changes depending on alphabet used'''
def test_getCharacterForward_1():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterForward('a', 5) == 'f'
    
def test_getCharacterForward_2():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterForward('#', 5) == 'e'

def test_getCharacterForward_3():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterForward('a', 967) == 'N'
#######################################################################################################
    
from lab05 import getCharacterBackward
'''changes depending on alphabet used'''
def test_getCharacterBackward_1():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterBackward('f', 5) == 'a'
    
def test_getCharacterBackward_2():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterBackward('e', 5) == '#'

def test_getCharacterBackward_3():
    # Note: This is using the alphabet used in createAlphabet()
    assert getCharacterBackward('N', 967) == 'a'


```

### To be continued in the next lab...


Save your functions in a Python file named `{{page.num}}.py` and `{{page.num}}_tests.py` in your directory **{{page.num}}**.

# Submit your work to Gradescope

Congratulations, you are finished with this lab! 

When submitting your files to Gradescope, you need to submit **all** requested files **together**, _all at once_, **every time** you submit your files to Gradescope. If you submit them one by one, Gradescope will only keep **the last one** that you submitted.

For this assignment, submit the `{{page.num}}.py` and `{{page.num}}_tests.py`, and if applicable the screenshot of the extra credit, all together. 

# Extra Participation Credit

You have a chance to earn 5 extra points on this lab by participating in a research study. To get credit for your participation, you need to submit to Gradescope a screenshot of the final page of the survey that shows that **you** have completed it. The screenshot should clearly show that it was taken by you, so the best way to do it is to have your name that is part of the System Menu at the top right of the screen.

**Instructions**:

To better understand students’ attitudes about computer science, as well as what facilitates feelings of belonging in computer science classrooms, you are being asked to participate in an anonymous online survey. This survey should take 15-25 minutes and asks about how you think you fit in computer science, your interest and motivation for computing, your attitudes about others, and your career interests. Sometimes attitudes can change over time, so you will also be asked to take this survey again at the end of the semester. Thank you for your help!

 The link is:  <https://www.surveygizmo.com/s3/5317570/Small-for-Big-CS4All-Phase-1>

_Acknowledgments: Thanks to Ana Nika and Matthew Buoni for the initial version of this lab, and to Noah Stier and Jose Cuellar for adapting it for this assignment. Additional thanks to Abtin Bateni, Rakshith Gopalakrishna, Radha Kumaran, and Sherry Chen for modularizing the functions, and to Olivia Gillam for creating the test functions._
