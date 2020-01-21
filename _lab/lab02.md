---
assigned: 2020-01-21
desc: Magic number
due: 2020-01-28 08:59
layout: lab
num: lab02
ready: false
---

# {{page.num}}: {{page.desc}}

In this lab, you'll review:

* Creating a file that has some functions in it
* Testing those functions interactively at the Python prompt
* Creating a file of automatic test cases for those functions
* Running those test cases
* Submitting your functions and test cases to Gradescope for grading

New skills you'll practice include:
* Working with strings and string functions
* Working with lists
* Indexing strings and lists
* Writing `if`/`else` conditional statements

# Carefully read and follow all instructions below

### Set up your working environment
Before you get started, remember to **arrange and resize your windows** like you did in the "Quick Detour" in Lab00, so that you can see **both** the browser (these instructions) and your files side-by-side.

If you need to install `pytest` refer to Lab01 instructions for how to do it.

### Create `{{page.num}}` directory
It's important to differentiate between the Python shell `>>>` vs the terminal `$`. 

Use the Terminal to create a new `{{page.num}}` directory inside the `cs8` directory.

Refer to Lab00 instructions if you need a reminder of how to use the commands.

As a reminder:

* `cd` returns you to your home directory (e.g., `/cs/student/cgaucho/`, if your username is `cgaucho`)
* `pwd` prints your current working directory
* `cd cs8` changes into the cs8 directory if `cs8` is in the current directory
* `cd ~/cs8` changes into the cs8 directory under your home directory regardless of the current working directory (because `~` is a shortcut for the absolute path of
   your home directory.)
* `cd ..` will move you _up_ one directory from your current directory. 
* `mkdir {{page.num}}` will create a {{page.num}} directory under your current working directory
* `ls` lists the files in your current directory

With that information, you should be able to determine how to
create a `~/cs8/{{page.num}}` directory, and make that directory your current
working directory (the one that comes up when you type `pwd`.)  Do that now. (Remember that creating and navigating directories happens using the terminal shell prompt, also known as the Unix command line, marked by `$`.)


# Step 0: Warm-up -- Using Function Parameters

This step will walk you step-by-step through the instructions for creating a function and adding parameters to it.

This section will also
* help you write down pseudocode and translate it into code 
* clarify the usage of function parameters
* show how to check if a string is empty.

* * *

Remember your very first lab in this course? (We hope so!)  Now, let's turn your `"Hello, World!"` from that lab into a function that can also greet the user by name they provide.

#### Create a function to greet the world
Let's first create a function called `hello()`, which takes no parameters and prints `"Hello, World!"`.
Save it in a file called **hello.py** (one of the advantages of using separate directories for differet labs: you can reuse the file names :-)).

See if you can write this function without looking at the answer below. 

**Do not copy/paste** the code below (it contains errors), and instead, type the correct code into your function.

```python
def hello():
    print(``Hello, World!``)
```

Run the function and call it on the IDLE prompt to verify it works correctly.
```
>>> hello()
```

_If you didn't listen to us and copy/pasted the code anyway, you must have gotten the `SyntaxError: invalid syntax` error, because `print()` expects you to print the strings enclosed in **quotes**._

Now that you have a function `hello()` (in a file **hello.py**), you can begin changing its behavior, depending on what the user provides as input into this function.

#### Include an input argument in the function signature

First of all, change the `print` to `return`.

Now, to change the behavior of this function, you'll need to make it accept an **argument**.
Here, we decided to call it `name` (you can call it something else).

```python
def hello( name ):
```

_Take a look at Step 3 in the previous lab to refresh what each part of the function means/represents._

This argument `name` will be like a switch, which will tell the function what to do.
In this assignment, we want to 
include the user's name in the greeting if there's a name, or if the name is empty, then **return** a generic "Hello, World!".

Let's try to capture it in pseudocode.

#### Pseudocode
```
# Given an input parameter called name
# Check if name is empty
#     If name is empty, 
#        then return "Hello, World!"
#     If name is not empty,
#        then return "Hello, <name>!"
```
Note that in the last line, we will be substituting user's input for `<name>` inside the `return` statement.

How would we check if `name is empty`? What does it mean for `name` to be empty?

If the string contains no characters, then it is considered to be empty.
Below are the examples of empty strings:

```python
empty_s1 = ''
empty_s2 = ""
empty_s3 = str()
```

If the string contains no characters, then its **length will be 0**.
You can verify it by running the following on the IDLE command prompt:
```python
>>> empty_s1 = ''
>>> len(empty_s1)
0
>>> empty_s2 = ""
>>> len(empty_s2)
0
>>> empty_s3 = str()
>>> len(empty_s3) == len(str())
True
```
_Note: if we accidentally typed `str()` instead of `len(str())`, we would have gotten `False`, because `0` is not the same as `''`._

#### Convert the pseudocode into code

Now that we have most of the pieces that we need, let's include the pseudocode in our function as comments and start converting it into Python.
```python
def hello( name ):
    """ Given an input parameter called name,
        the function returns "Hello, <name>!"
        if the name is not empty, otherwise,
        the function returns "Hello, World!"
    """
    if len(name) == 0:   # Check if name is empty
    #     If name is empty, 
    #        then return "Hello, World!"
    #     If name is not empty,
    #        then return "Hello, <name>!"
```

We could have used instead used two `if` statements:
* `if len(name) == 0` and 
* `if len(name) != 0`.

However, we are taking advantage of the fact that _only if_ the first `if` statement is `False`, then the `else` block will be automatically executed (run).

```python
def hello( name ):
    """ Given an input parameter called name,
        the function returns "Hello, <name>!"
        if the name is not empty, otherwise,
        the function returns "Hello, World!"
    """
    if len(name) == 0:   # Check if name is empty
        return("Hello, World!")
    else:  # the name is not empty,
        return("Hello, "+ name + "!")
```

Woohoo! We now have a new function `hello`, which takes 1 argument. 
Since this definition **overwrote** the previous definition (in which you didn't have to provide an argument), Python will complain if you forget to provide it with the input argument.

```
>>> hello()
Traceback (most recent call last):
  File "<pyshell#77>", line 1, in <module>
    hello()
TypeError: hello() missing 1 required positional argument: 'name'
```

As long as we provide a string, our function knows what to do.
```
>>> hello("CS 8")
'Hello, CS 8!'
>>> hello("42")
'Hello, 42!'
>>> hello("")
'Hello, World!'
```

#### Troubleshooting

Note that if we do not provide the input as a string, Python will complain, saying `TypeError: object of type 'int' has no len()`.
```
>>> hello(42)
Traceback (most recent call last):
    ...
    if len(name) == 0:   # Check if name is empty
TypeError: object of type 'int' has no len()
```

OK, we are done with the warm-up!


* * *

# "Four is the magic number"

This assignment is based on a brain teaser. Look at the output below is see if you can figure out the pattern. If not, don't worry -- we'll guide you to the solution. 

The riddle starts by telling you "Four is a magic number". 
For any number you select, it is possible to "somehow" create a sequence, which will ultimately end in "Four is the magic number".

For example:
* 5 is 4 and four is the magic number.
* 6 is 3 and 3 is 5 and 5 is 4 and four is the magic number.
* 11 is 6 and 6 is 3 and 3 is 5 and 5 is 4 and four is the magic number.

```
0 =>
  Zero is four and four is the magic number
1 =>
  One is three and three is five and five is four and four is the magic number
2 =>
  Two is three and three is five and five is four and four is the magic number
3 => 
  Three is five and five is four and four is the magic number
4 =>
  Four is the magic number
5 => 
  Five is four and four is the magic number
6 =>
  Six is three and three is five and five is four and four is the magic number
7 =>
  Seven is five and five is four and four is the magic number
8 =>
  Eight is five and five is four and four is the magic number
9 =>
  Nine is four and four is the magic number
10 =>
  Ten is three and three is five and five is four and four is the magic number
```

Hopefully, by now you are able to see a pattern. 
If not, no worries! Let's see if working on the helper functions will give you a better clue.

## Step 1.0: Create a file called `magic_number.py` in your `~/cs8/{{page.num}}` directory

Choose “File => New File” in IDLE to bring up an “untitled” window, then type the functions into that window (i.e., in the new file).

**IMPORTANT**: Make sure to save your file with the exact filename we requested. Naming it with some other name will confuse Gradescope and result in a score of 0, even if your work is correct.


 ## Step 1.1: Add the preliminary information 

Write a comment with your name and PERM number in that file (in general, you should write this on each of your submitted source files).

Next, since we will be using `pytest` to verify that our functions work correctly, let's import that module:

```python
import pytest
```

## Step 1.2: Add the function definition

Add the following function definition into your file.

```python
def numToStr( num ):
    """ 
    Checks that the provided `num` is an integer 
    between 0 and 10 (inclusive).
    Returns the spelled-out name of the provided number in English.
    """
    return 42 # TODO: replace this stub with the correct code
```
**Important requirement**:
If the input is less than 0 or greater than 10, then the function should return `None` (either explicitly or implicitly, i.e., if no return is specified for those cases).

**Remember**: `None` is a special value that has its own type (`NoneType`), which means it is **not** the same as `"None"`, which is a string.


Even before you create your solution for this step, you can move to the next step to write test functions (which should originally all fail).

## Step 1.3: Add the test functions

Add the following function definitions into your file. These are a special kind of function called _a test case_. These particular test cases are written in the style used by the `pytest` testing framework, and they follow these rules:

*    The name of each test cases function must start with `test_`.
*    Each test case ends (typically) with a line of code that starts with the keyword `assert`, followed by a boolean expression.
     *   If the expression is `True`, the test case passes.
     *   If the expression if `False`, the test case fails.
*    Each test case function must have a different name.

_Take a look at the previous lab's Step 5 to review how you wrote test cases there._

```python
def test_numToStr_0():
   assert numToStr(0) == "zero"

def test_numToStr_10():
   assert numToStr(10) == "ten"

def test_numToStr_11():
   assert numToStr(10) == None
```

Finally, run the code, and ensure that you don’t have any syntax errors in your Python code.

## Step 1.4: Test your code by hand

Because we want to be sure that you continue to practice the skill, test your code by hand first.

That is, select "Run Module" in IDLE, and then type in a few function calls at the **Python Shell Prompt**. Here are a few:

```
>>> numToStr(4)
42
>>> numToStr(7)
42
>>> 
```

OK, we see that the function will continue to provide us with the same answer, consistent with the return value in our function definition. The point is that
* you need to know how to check the value of a function call by typing it in.
* you need to see that right now, the function *always* returns 42, no matter what.

There is a reason for that.  We call this a **"stub value"**.  It returns the wrong answer _on purpose_ so that we can check that all of the tests fail. We want to see all of the tests fail, and after we fix the function, we can see all of the tests pass. That's the general idea:

* We want so see *all tests fail* when the function is wrong.
* Then if they *pass* when the function is right, we *trust* the test.

# Step 1.5: Run `pytest` on the file so far

As a reminder, you run pytest OUTSIDE of IDLE, at the regular **Terminal** prompt (`$`).

You may find it helpful to bring up a second terminal window and use

```
cd ~/cs8/{{page.num}}
```

to get into the correct directory.  Then use:

```
python3 -m pytest magic_number.py
```

You should see three test failures. If you do, then you ready to fix the code so that it works, which is the next step.

(If you need a refresher on how to interpret the output of `pytest`, refer back to [lab01](/lab/lab01/]).)

If you got a `SyntaxError: invalid syntax`, then verify that you are running the command **not in IDLE** (which has the `>>>` prompt), but in Unix using the **Terminal** (which has the `$` prompt).

# Step 1.6: Fixing the code for `numToStr`

As usual, if you have failing test cases, the thing to do is fix the code so that the test cases pass.

* * *
There are many ways to approach the solution of this problem.
We recommend you to use a **list** that includes the spelled-out name of each number from 0 to 10 (inclusive) in English.

```python
numbers = [ "one", "two", "three", ...]
```

Keeping in mind that list indexing starts at **`0`**, how could you use this to your advantage to return the correct value? (E.g., `numToStr(1)` should return `"one"`.)
Implement your answer by updating your definition of the function `numToStr()`.
_Hint:_ You would need to complete the list of numbers and include the example list `numbers` in your code, before the `return` statement.

* * *

Once you have the code correct, try testing both using interactive testing as well as by running `pytest`.

At each step, you should first try to get the test cases to pass by running pytest at the Unix command line as discussed above.

*   Please do this BEFORE submitting to Gradescope.
*   Please DO NOT upload your file to Gradesope without testing locally first.

Once you see your tests are passing, THEN submit a version to Gradescope.

You are by no means finished with this lab. But, we want to encourage you to make a submission to Gradescope now anyway. Here is why:

1. After you upload your file, it will provide a backup copy of your work in case something goes wrong with your computer (yes, this happens and you want to make sure there is a backup somewhere).
    
2. You also will be able to see some progress towards completion of the lab&mdash; partial credit for completion of this step.

Once you've submitted and you see that you got more than 0 points, you are ready to continue with the rest of the lab.

# Step 1.7: Seeing the magic in action

Below is the skeleton code for printing the riddle for any number between 0 and 10.

```python
def print_magic( num ):
    if num < 0 or num > 10:
        return # exit the function

    num_str = ... # TODO call numToStr with num as an input

    while num != 4:
        print(num, "is", ...) # TODO: figure out the last piece of the puzzle
        num = ... # TODO: num should become the new value from above
        num_str = # TODO update num_str: call numToStr using new num 
    print("four is the magic number") # output once the loop is finished
```

When you complete the code correctly and run it in IDLE, you should see the following output.

```
>>> print_magic(1)
1 is 3
3 is 5
5 is 4
four is the magic number

>>> print_magic(10)
10 is 3
3 is 5
5 is 4
four is the magic number
```

Note that if we give it a number outside of the expected range, the function should not print anything. 
```
>>> print_magic(11)
>>>
```

#### Troubleshooting

If you are getting `IndexError: list index out of range`, then double-check that the list in the `numToStr` function has the correct number of elements (should be 11 total, since we are starting at zero).

Another error you might run into is `TypeError: object of type 'int' has no len()`. If you see it, verify that when you call `len()`, the variable you give it contains a string object. If you accidentally gave it an integer object or `None`, it will produce this error. (Note that you can check the type by printing the value or `type()` of that object as part of debugging your code.)


# Bonus (optional) TO BE ADDED

# Last Step: Submit your files to Gradescope

Before you submit your code to Gradescope, make sure that your files 
* are named `hello.py` and `magic_number.py`
* do not have any `TODO` comments left in the code.
* contain a comment at the top of the file that says `Submitted by <name>, PERM, for CS 8 (W20)`. (Please, replace `<name>` and `PERM` with your first and last name and PERM number respectively.)

You are ready to submit your work to Gradescope.


Navigate to the Lab assignment on Gradescope and upload your `.py` files, similar to how you submitted `hello.py` for Lab00. 

**Important**: you need to upload **both** files _at the same time_. You can hold down Ctrl (or Cmd/command) key while clicking on the files to select them to upload.

Gradescope will run a few tests to check if your functions are correct. If your tests do not pass, go back to these functions and double-check your logic and function syntax.

**Passing Gradescope tests doesn't guarantee that your solution is correct.** 
Make sure to test your code thoroughly yourself. We will be including **additional hidden tests after the due date** in Gradescope to verify that your code is running as was specified in the lab instructions.


## Final Step:  Log Out

Actually, this is the final step of <em>every lab</em>.

In fact, you should do this every time you walk away from a lab computer, either in Phelps 3525 or CSIL.

Here's how:

* Find the System Menu at the top right of the screen.
* Select your name and in the dropdown click on "Log Out"


**Acknowledgment**: This lab was designed at UCSB by YKK for CS 8 (W20).
