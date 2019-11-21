---
num: "lec09"
desc: ""
ready: true
lecture_date: 2019-10-29
reading: 
---

# Lecture 9: String Processing Cryptography

On the menu today: fruity looped strings and indices, a dash of imported modules, and a cipher sundae. But before we begin…

# Some words of wisdom

Try not to hard-code values into your programs. Write code that can be reused in many different situations without modification. You can do this by keeping automation in mind.

For example, instead of specifying that there are 26 letters in a string, use the `len()` function to get that same number. That way, your program can quickly and easily adapt to different cases, such as a string with 33 letters.

Plus, when writing a program, it's always nice to start with pseudocode and work your way up to algorithms and then actual code. That way, you'll have an easier time keeping track of your main objective rather than getting bogged down by syntax.

Oh, and run your code every few lines that you write. It's best to catch errors early on when they're not as much of a hassle to fix.

# Now, a bit of review (or, the appetizers)

## (Froot) Loops

A **`for` loop** is a *count*-controlled loop that repeats a specific number of times based on how many items are in a collection, such as a list, a tuple, or a range. As such, you don't need to tell it specifically when to end, because it ends by itself ~~when it feels like it~~ when it has gone through all of the items in the collection. Here's the rough format of a `for` loop:

```python
for VARIABLE in COLLECTION:
    STATEMENT(s)
```

Compare this to a **`while` loop**, which is a *condition*-controlled loop that does require you to specify an end condition, such as when a counter reaches a certain value.

This lecture will exclusively use `for` loops. `while` loops will be saved for another meal.

## Strings (and string cheese)

Happy Halloween! Soon. Let's define a string:

```python
s = "Halloween"
```

As you (hopefully) recall, individual characters in a string can be accessed with their **index**. Here are the indicies, both positive and negative, of each of the characters of our string `s`.

| H | a | l | l | o | w | e | e | n |
| :---: | :---: |  :---: |  :---: |  :---: |  :---: |  :---: |  :---: |  :---: |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |

The syntax for accessing characters is

```python
c = s[i]
```

where `c` is a variable for storing the retrieved character, `s` is the variable of the string `"Halloween"`, and `i` is the index.

## Home on the `range()`

The **`range()`** function generates an incremental set of numbers from one number to another number. It sounds simple, but there's a lot that's going on. So let's unpack everything.

Here's `range()` written out, with all three possible arguments and their positions represented by placeholder values:

```python
range(start, end, step)
```

Let's go through each of those arguments one by one.

| Argument | What it means | Optional? | Default value |
| -------- | ------------- | --------- | ------------- |
| `start` | The number you, well, start counting from. | yes | `0` |
| `end` | The number you stop counting at, plus 1. For example, writing `3` means `range()` will only return up to `2` at the most, and writing `10` means `range()` will only return up to `9` at the most. (You must specify an end value. Otherwise, you'll get a nasty `TypeError`.) | no | N/A |
| `step` | How many numbers you count by from the start value to the end value. Remember how, when you were younger, you used to count by 2's and 3's and 5's and whatnot? You might've even made a game out of it. 2, 4, 6, 8, 10, and so on until you got tired. Same thing in `range()`. | yes | `1` |

# Messing around with strings (or, the main course)

## String indexing and iteration

Remember the `len()` function? It's amazing.

Let's combine everything we've done so far to print every character in string `s` using a `for` loop. Here's what that would look like:

```python
s = "Halloween"
for i in range(len(s)):
    print(s[i])
```

Here's what the Python shell returns when we run the code:

```
H
a
l
l
o
w
e
e
n
```

If you're a bit confused about the syntax of the Python code above (especially with the `range()` part), here's the same code but with the optional and default `range()` arguments included:

```python
s = "Halloween"
for i in range(0, len(s), 1):
    print(s[i])
```

Here, `range()` is telling the `for` loop to assign `i` a value of `0`. When the loop finishes running once, `range()` tells the `for` loop to increase `i` by a value (step) of `1`. These iterations continue until `i` is equal to a value of `8`, which is one less than the value of `len(s)`, which is equal to `9`.

Of course, you don't need to include `0` at the beginning of `range()`, nor do you need to include `1` at the end. But these are the implied and unseen values at work here, and sometimes it helps to make the unseen seen.

So if `i` is first equal to `0`, then the `for` loop is basically telling `print(s[i])` to `print(s[0])`, or to `print('H')`. Then, since there are no more statements within the loop, a new iteration begins, and `i` becomes `1`. Now, `print(s[i])` becomes `print(s[1])` becomes `print('a')` on a new line. And on it goes until `print(s[8])` becomes `print('n')` and the final character, `n`, is outputted onto the shell.

## Bigger steps (or, more `range()` shenanigans)

Now that you're (hopefully) more confident about `range()`, let's start messing around with the `start`, `stop`, and `end` values and changing their defaults. Perhaps it'll be easier for you if you actually represent `start`, `end`, and `step` as variables, like so:

```python
s = "Halloween"

start = 2
end = len(s)
step = 3
 
for i in range(start, end, step):
    print(s[i])
```

And the output of the Python shell:

```
l
w
n
```

## Printing a string backwards (or, *even more* `range()` shenanigans)

You're not out of the woods yet. You've printed all of the characters in a string, and you've even printed some of the characters in a string based on a step value. But what if you wanted to print a string backwards?

Well, here you go:

```python
s = "Halloween"

start = -1
end = -len(s) - 1
step = -1

for i in range(start, end, step):
    print(s[i])
```

Remember those negative indices? Time to put them to use.

| Argument | Value | But why? |
| -------- | ----- | -------- |
| `start` | `-1` | Printing a string backwards means you start from the last character in the string, which in this case is `-1`. You could also write `8`, but `8` is specific to string `s = "Halloween"`, and it would be a little tedious having to modify that value every time you wanted to use a new string. |
| `end` | `-len(s) - 1` | Okay, okay. Start from `-1` as discussed in the previous row, and count backwards by 1 until you hit the character `'H'` in the string `s = "Halloween"`. You should get `-9` (refer to the table of indices up above if you're confused). But remember that thing about automation? "Try not to hard-code values into your programs." So to get `-9` automatically, the function `len()` (which gets the length of a string) seems like a good place to start.<ul><li>`len(s)` returns a value of `8`, since there are 8 characters in string `s`.</li><li>`-len(s)` thus returns the negative value of `len(s)`, meaning `-8`.</li><li>`-len(s) - 1`, which subtracts `-1` from `-len(s)`, thusly returns `-9`, which is what we want.</li></ul>Notice that now, if we redefine string `s` to something like `s = "candy"`, `end` will automatically change to `-6` so that we don't have to change it ourselves. Hooray.|
| `step` | `-1` | You counted backwards by 1 to get the `end` value. That's exactly the same thing as `step`! "Backwards by 1" is just an informal way of saying `-1`. In other words, `range()` increments, or steps, by `-1` per iteration. |

All of this outputs:

```
n
e
e
w
o
l
l
a
H
```

# Edge cases (or, the side dishes)

You've done `for` loops, string indexing, string iteration, and lots of `range()`-related stuff. Time for some more advanced topics.

## Handling index overflow

String `s = "Halloween"` has positive indices of `0` to `8` and negative indices of `-1` to `-9`, so statements like `print(s[6])` and `print(s[-3])` work perfectly fine.

But what happens if you choose an index that doesn't exist in this case, like `42` and `-1729`, and use them in statements like `print(s[42])` and `print(s[-1729])`? You run into an `IndexError` and your day is ruined.

Well, not quite. What if there was some way you could "loop" an index back to one of the valid indices? You're in luck.

```python
s = "Halloween"

i = input("Enter an index: ")
i = int(i)

if i > len(s) - 1:
    i %= len(s)
elif i < -len(s):
    i %= len(s)
    
print(s[i])
```

As usual, we first define a string `s = "Halloween"` with which to work with.

Then, the program prompts the user to type in an index and stores that value in variable `i`. Let's assume the user types `42` as the input. Because `input()` normally gives values in the string data type, the program must convert `42` into an integer type using `int()` so that mathematical operations on the value are possible. (You can also combine the first two lines into something like `i = int(input("Enter an index: "))` if you prefer.)

Now comes the index checking part. The first `if` statement checks to see if the index exceeds the upper indexical bound of string `s`, which in this case is `8`. Again, in the interest of automation, `len(s) - 1` becomes `9 - 1` becomes `8` by itself without programmer interference, which is the ideal scenario.

Since we earlier defined `i` to be equal to `42`, `i` is indeed greater than `len(s) - 1`. The `if` statement successfully proceeds to the next statement `i %= len(s)`, which is just a shorthand way of writing `i = i % len(s)`. Recall that the `%` symbol, or modulo, divides a number on the left side by the number on the right side and returns the remainder of the operation. In this case, `i = i % len(s)` becomes `i = 42 % 9` becomes `i = 6`.

Because the `if` statement has been satisfied, the program skips the `elif` statement during execution and moves on to `print(s[i])`. Now that `i = 6` instead of `i = 42`, `print(s[i])` properly returns the character `e` instead of a scary `IndexError`.

If you had a very big negative index (very small index?) like `-1729`, the `elif` statement runs instead of the `if` statement. Notice that the run condition for `elif` is different than the run condition for `if`: It's `-len(s)`, not `len(s) - 1`. That's because `elif` is checking to see if the index you entered exceeds the *lower*, not upper, indexical bound of string `s`, which is `-9` instead of `8`.

Also, if you want, you can condense the `if` and `elif` statements into a single line, like so:

```python
if (i > len(s) - 1) or (i < -len(s)):
    i %= len(s)
```

Parentheses aren't *technically* required here, as everything else in the `if` statement already has a higher precedence than the `or` keyword, but parentheses help improve readability in more complex lines of code and reduce the chance that you'll actually run into issues later down the line.

## Accessing substrings and string slicing

Let's, for a moment, step away from all of this `if` and `len()` craziness and focus specifically on chopping up and and sticking different parts of strings together. To do that, we'll need to once again use indices.

Bring up your Python shell and type in a string:

```
>>> 'mississippi'
```

Just like in lists and tuples, you can access specific sets of characters, or substrings, within a string by using square brackets, numbers, and separating colons. The first number is where you start, the second number is where you end plus one, and the optional third number is how many numbers you count by. Sound familiar? Yep, it's pretty much just like `range()`!

```
>>> 'mississippi'[0:4]
'miss'
>>> 'mississippi'[0:4:2]
'ms'
```

However, there are some differences between specifying substrings and specifying a `range()`.

```
>>> 'mississippi'[4] # Access character at index 4.
'i'
>>> 'mississippi'[:4] # Access characters from the beginning of the string (index 0) to index 3 (4 - 1 = 3).
'miss'
>>> 'mississippi'[4:] # Access characters from index 4 to the end of the string.
'issippi'
```

You can assign a string to a variable and use the exact same syntax for accessing substrings.

```
>>> example = 'mississippi'
>>> example[0:4]
'miss'
>>> example[4:]
'issippi'
```

All of this work so far has been in service to **string slicing**, which is, well, slicing up a string into smaller pieces, or substrings. You can join these sliced fragments into larger pieces.

```
>>> 'mississippi'[:4] + 'mississippi'[4:]
'mississippi'
```

# Useful modules (or, the condiments)

## Generating an alphabet

If you ever find yourself typing out `abcdefghijklmnopqrstuvwxyz` on your keyboard because

1. you're bored (don't worry, everyone's done it at some point) and/or
2. you need a string of characters for a cryptography assignment,

simply import the **`string` module** and the **`ascii_lowercase` constant** at the top of your program file. Voilà! Now you don't have to worry about typos. **`ascii_uppercase`** is also available in case you want, well, uppercase letters.

```python
from string import ascii_lowercase
from string import ascii_uppercase

lowercase_letters = ascii_lowercase
uppercase_letters = ascii_uppercase
```

Note that since `ascii_lowercase` and `ascii_uppercase` are *constants*, not functions, there aren't any parentheses that go at the end. You'd treat them like variables, except these "variables" are immutable.

YOu also have the option of importing the entire `string` module and not just `ascii_lowercase` and `ascii_uppercase`. However, in order to access those two constants, you would have to prefix them with `string.` so that Python knows where you're getting these values from.

```python
import string

lowercase_letters = string.ascii_lowercase
uppercase_letters = string.ascii_uppercase
```

Whether you only import select functions or values from a module or import the entire module is up to you.

## Generating random numbers

Alright, alright, they're not *actually* random. They're pseudorandom. But we're not running a lottery or anything, so pseudorandomness is good enough for our purposes.

To get (somewhat) random values in your program, import the **`randint()` function** from the **`random` module**. As described before, you can accomplish this in two ways:

```python
# Tactic 1
from random import randint

# Tactic 2
import random
```

Assuming you employed the second tactic, here's how you would use the `randint` function:

```python
random.randint(start, end)
```

`start` establishes the lower bound of your random-ish number generation and `end` establishes the upper bound. Note that, unlike the range of numbers in `range()`, the range of numbers in `randint()` will go up to and *include* the final value. So if you had `random.randint(0, 1)`, it would be possible to get `1` as a result instead of just `0`.

## Analyzing a string

Oh look, more strings. This time you'll be taking functions from the **`str` class** (not to be confused with the `string` module from above). Since the `str` class is built into Python, you don't need to import anything this time around.

Here are some `str` functions that might come in handy:

* **`str.find(item)`** returns the index of the first occurrence of substring `item` in string `str`, or `-1` if `item` isn't found.
* **`str.rfind(item)`** returns the index of the last occurrence of substring `item` in string `str`, or `-1` if `item` isn't found.
* **`str.count(item)`** returns the number of times substring `item` appears in string `str`.

When you're using these functions, replace `str` at the beginning of the function with the string or the name of the variable that you're searching in. For example, if you're trying to find the index that the character `'e'` appears in the string `"alphabet"`, you could do one of the following:

```
>>> "alphabet".find('e') # Directly look for a character in a string.
6
>>> word = "alphabet"
>>> word.find('e') # Using a variable to look for a character in a string.
6
```

# Cryptography (or, the dessert)

You've sliced strings, you've combined them, you've printed them, you've `for`-looped them, you've `range()`d them, and you've indexed them. Now it's time to apply those skills to something practical.

## Lots of vocabulary

If you're sending a message to someone, you probably don't want someone else to snoop in and read what you've written. This is where cryptography comes in. **Cryptography** is the process of making communication secure so that your message is understood only by your intended recipients.

**Encryption** is one of the ways that cryptography works, by converting **plaintext**, your original message, into **ciphertext**, a  (hopefully) secure and mostly unintelligible version of your original message. **Decryption** works the opposite way around, by converting ciphertext into plaintext so that your intended recipient(s) can read what you've written.

In both cases, you'll need a **cipher**—an algorithm for performing encryption and decryption—with which to convert messages back and forth between plaintext and ciphertext. One type of cipher is a **substitution cipher**, where each character of your original message is mapped to another character in a scrambled but systematic **key**.

```python
original_message = "abcdefghijklmnopqrstuvwxyz"
key = "zyxwvutsrqponmlkjihgfedcba"
```

Here, in the process of encryption, `'a'` would become `'z'`, `'b'` would become `'y'`, and so on and so forth. Note that `key` corresponds to each letter of `original_message`, so this cipher has a 1:1 mapping. However, this does not always have to be the case.

```python
original_message = "abcdefghijklmnopqrstuvwxyz"
key = "zzzzzzzzzzzzzzzzzzzzzzzzzz"
```

Here, because key is just a string of 26 z's `original_message` would just be converted into, well, a string of z's.

## Example program

From class, here's an example of what a cryptography program could look like.

```python
from string import ascii_lowercase

def generate_key():
    # return "abcdefghijklmnopqrstuvwxyz "
    return "opqrstuvwxyz abcdefghijklmn"

# Given a message, encrypt it using the key.
message = "hello, world!"
encrypted = ""
decrypted = ""

# Generate an alphabet.
alphabet = ascii_lowercase + " "
print('"' + alphabet + '"')

# Generate the key.
key = generate_key()

# Loop through every letter of message.
# Find a letter from the key to replace it with.
# Assign a new letter to an encrypted message.
for letter in message:
    index = alphabet.find(letter)
    encrypted += key[index]
print(encrypted)

# Loop through every letter of encrypted.
for letter in encrypted:
    index = key.find(letter)
    decrypted += alphabet[index]
print(decrypted)
```



Acknowledgment: Big thanks to Yiu-On Li and Kevin Wang for their help with creating these notes and adding the narrative. :smile:
