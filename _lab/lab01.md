---
assigned: 2020-01-14
desc: Writing Test Cases
due: 2020-01-21 08:59
layout: lab
num: lab01
ready: true
---

# {{page.num}}: {{page.desc}}

In this lab, you'll practice:

* Creating a file that has some functions in it
* Testing those functions interactively at the Python prompt
* Creating a file of automatic test cases for those functions
* Running those test cases
* Submitting your functions and test cases to Gradescope for grading


### Set up your working environment
Before you get started, remember to **arrange and resize your windows** like you did in the "Quick Detour" in Lab00, so that you can see **both** the browser (these instructions) and your files side-by-side.

# Lab01 Slides

You can view the accompanying slides to lab01 [here](https://drive.google.com/open?id=1OA7xF50ffKJbs5mdWFAsuEenmQV5O22S).

# Step 0: Install pytest for your account (or on your machine)

This lab is one that you may find you need to do on the CSIL machines.
It's important to differentiate between the Python shell `>>>` vs the terminal `$`. 

It is probably the case that `pytest` is not installed for your version
of Python3.  You can check by typing `python3` at the Terminal prompt
to get to the Python Shell Prompt `>>>`, and then typing `import pytest`.

If you get an error message like the one shown below, then pytest is not installed. However, if you `do not` get an error message, skip to Step 1.

```
[cgaucho@csil-12 ~]$ python3
Python 3.4.3 (default, Aug 9 2016, 15:36:17) [GCC 5.3.1 20160406 (Red Hat 5.3.1-6)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pytest
Traceback (most recent call last):
File "", line 1, in ImportError: No module named 'pytest'
>>> exit()
[cgaucho@csil-12 ~]$ pip3 install --user pytest
```

In order to exit the python shell in terminal press Ctrl+D or type exit() in order to return to the normal terminal. 

To install pytest, type this command into the terminal session
(the Unix Terminal prompt) to install pytest for your CSIL account:


```
pip3 install --user pytest
```

To install pytest on Windows, see [this tutorial](http://meingraffiti.blogspot.com/2015/09/installing-pytest-on-windows-platform.html).
 
You can also *try* this command on Mac.  It might work, or it
might not.  If it does&mdash;great, then you can do this lab on your own
machine.  If not, then you'll need to do it on CSIL.

The output should look something like this:

```
[cgaucho@csil-12 ~]$ pip3 install --user pytest
You are using pip version 7.1.0, however version 9.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Collecting pytest
  Downloading pytest-3.2.1-py2.py3-none-any.whl (186kB) 100% 188kB 1.5MB/s
Collecting py>=1.4.33 (from pytest)
  Downloading py-1.4.34-py2.py3-none-any.whl (84kB) 100% 86kB 2.0MB/s
Requirement already satisfied (use --upgrade to upgrade): setuptools in /usr/lib/python3.4/site-packages (from pytest)
Installing collected packages: py, pytest
Successfully installed py pytest
[cgaucho@csil-12 ~]$
```

To tell whether it worked or not, try the `import pytest` command again:


```
[cgaucho@csil-12 ~]$ python3
Python 3.4.3 (default, Aug 9 2016, 15:36:17) [GCC 5.3.1 20160406 (Red Hat 5.3.1-6)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pytest
>>>
```

The lack of an error message (just another `>>>` prompt) means "it worked!".
We are going to use the Python prompt in the next step anyway, so just stay
at the Python prompt.  (Or if you need to get out of Python, use CTRL-D to return
to the Unix shell prompt.)

# Step 1: Warmup--experiencing floating point inaccuracy

In this step, you will see how to import another Python module (`math`) and look at the inaccuracies that we can run into when working with floating point numbers (`float`s). You will learn how to plan for this inaccuracy and will be testing these commands on the Python shell before starting the lab assignment in a new file.

If you are not already at the Python prompt, bring up a terminal window, and type `idle3`.  This should give you the Python Shell Prompt (`>>>`) where you can type in some expressions and see the resulting values.

Type in the `import math`, followed by `math.sqrt(2)`.  It should look like this:

```
>>> import math
>>> math.sqrt(2)
1.4142135623730951
>>> 
```

Note that the `import` statement gives us access to `math.sqrt()`. The name that comes after the keyword `import` is called a _library_ or a _module_ (here we are importing the `math` library). This allows the program to use other code like `math.sqrt()` that we didn't write ourselves (someone else wrote it for us). There are a lot of libraries that come with programming language (such as `math`), and some libraries that can be downloaded and imported into your program (see Section 1.2 in Perkovic). In either case, using libraries helps developers focus on solving their problems and manage their code without having to re-implement certain functionality (like making a sqrt function from scratch).

The value we get back is the square root of 2, which is an irrational number&mdash;its decimal representation goes on forever.  Unfortunately, real world computing devices typically store numbers with a finite number of decimal places&dagger;. So, the representation we see for the square root of two is an approximation.

<div style="font-size:80%">
(&dagger;&nbsp;Technically, "binary places", or "binary digits" rather than "decimal places". For purposes of this discussion it amounts to the same thing.  Also, some computer systems do work with "symbolic" representations of numeric quantities, e.g., retaining √2 or π as symbolic values rather than as numerical approximations. On those systems, you can get exact results, without losing precision, at the expense of speed.  We won't discuss that kind of software in this course.)
</div>
<br/>
We can see this if we multiply `math.sqrt(2)` by itself.  Try it:

```
>>> math.sqrt(2) * math.sqrt(2)
2.0000000000000004
>>> 
```

See that pesky `4` digit in the ten quadrillionths place?   My goodness, we are really, really close to 2.0, but if we ask whether the values are equal, Python says no:

```
>>> math.sqrt(2) * math.sqrt(2) == 2.0
False
```

In fact, Python is very clear about the difference between `2.0` and `math.sqrt(2) * math.sqrt(2)`, and can even tell us 
how big that difference is.  The `4` digit is only the tip of the very, very, very small iceberg:

```
>>> math.sqrt(2) * math.sqrt(2) - 2.0
4.440892098500626e-16
>>> 
```

We can deal with this in our code by subtracting the expected value from the result, taking its absolute value, and finally checking if it is less than some tolerance. This might come in handy in your future coding experiences, but for now we'll leave it here.

```
>>> a = 5
>>> b = 5.00001
>>> a == b
False
>>> abs(a - b) < .001
True
```

We should plan to program with the knowledge that some mathematics operations are approximations  (especially irrational numbers). 
<strong>When we test software involving floating point numbers, we must allow for some inaccuracy</strong>.   This "allowable inaccuracy" is sometimes called the <em>tolerance</em>, and it might be a small value such as `0.001` (1x10<sup>-3</sup>, or `0.000001` (1x10<sup>-6</sup>).

In Python, we can write `0.001` as `1e-03`, and `0.000001` as `1e-06`.  (The lowercase `e` is the way that Python represents scientific notation.)

You can see that Python, by default, formats numbers in this notation once the fifth decimal place is reached:

```
>>> 0.01
0.01
>>> 0.0001
0.0001
>>> 0.00001
1e-05
>>> 0.000001
1e-06
>>>
```

We'll come back to that idea later in this lab.

As a reminder, CTRL-D gets you out of the Python Shell Prompt (`>>>`)
and returns you to the Unix shell prompt.

# Step 2: Make a `~/cs8/{{page.num}}` folder

In the previous lab, you should already have created the 
`~/cs8/lab00`. You are now going to create a folder
`~/cs8/{{page.num}}` for the files for this lab.

In general, it is a good idea to keep your work for this class
under `~/cs8`, in folders called `lab00`, `lab01`, `lab02`, etc.

This isn't exactly *required* (no-one is going to check), but it is
a good habit to develop.  Here's why: all the rest of the
instructions will be written based on the assumption that you did
things this way.  And if you continue to take CS courses at UCSB,
you'll often find that's the case from one course to the next.
Plus, it helps you organize your files from different labs.

So, we strongly encourage you to do it.

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

Then, you are ready for the next step.


# Step 3: Create a file called `convert.py` in your `~/cs8/{{page.num}}` directory

The contents of `convert.py` should be as shown below: it should contain three Python function definitions that, at the moment, are incorrect.

Choose “File => New File” in IDLE to bring up an “untitled” window, then typese the functions into that window (i.e., in the new file).
Note that the formulas for converting between Feet, Inches, and Cm are incorrect. That’s deliberate, so just go with it for now. We’ll fix those at a later step.

```python
def ftToIn(feet):
    ''' TODO: add the docstring '''
    return (feet * 0)  #TODO: Fix this line of code
 
def inToCm(inch):
    ''' TODO: add the docstring '''
    return (inch * 0) #TODO: Fix this line of code
 
def ftToCm(feet):
    ''' TODO: add the docstring '''
    return (feet * 0) #TODO: Fix this line of code

```
The code above is how we define functions in Python. We will work on defining our own functions throughout the course.

**IMPORTANT**: Make sure to **save your file** with this **exact filename**: **`convert.py`**. Naming it with some other name will confuse Gradescope and result in a score of 0, even if your work is correct.

On a very high level, the `def ftToIn(feet)`, `def inToCm(inch)`, and `def ftToCm(feet)` are what we call a function header/signature.
* In the function signature of `def ftToIn(feet)`, the keyword `def` tells python we are defining a function,
* `ftToIn` is the name of the function and
* `feet` is the function's parameter enclosed in parentheses (note, there can be zero or more parameters for a function, but in this case there is only one). You can think of parameters as variables that the function can use (note that calling `ftToIn(0)` is telling the computer to call `ftToIn` and set `feet = 0`).
* The `return` keyword is used to pass back a value to whoever called the function.

	* In this case, the function `ftToIn(feet)` returns the inch value of a feet measurement we passed into the function (using the input argument `(feet)`).
	* The function `inToCm(inch)` returns the centimeter value of an inch measurement we passed into this function (using the input argument `(inch)`).
	* The function `ftToCm(feet)` returns the centimeter value of a feet measurement we passed into this function (using the input argument `(feet)`).

# Step 4: Test your code by hand

To test this code, we'll first do what many programmers do: test the code by hand.

That is, we'll run the file in IDLE, and then "call the function" (i.e. enter some function calls in the Python shell) to see what results we get. These functions are supposed to convert between feet, inches, and centimeters. Let's see if they work properly when you are given 0 feet and 0 inches.

Use the "Run Module" menu command to run the code: doing so will define the functions (i.e., make Python aware that they exist and what they are supposed to do according to the provided function definitions). You can then try entering these function calls at the Python Shell prompt. You should see output similar to what is shown below:

```
>>> ftToIn(0)
0
>>> inToCm(0)
0
>>> ftToCm(0)
0
```

As you can see, for those three particular values, the function appears to return the correct answer: 0 feet is 0 inches, 0 inches is 0 centimeters, and 0 feet is indeed 0 centimeters.
So clearly, testing with a single value is not enough. Indeed, if we test with another value, such as 5 feet and 60 inches we see that the output is incorrect:

```
>>> ftToIn(5)
0
>>> inToCm(60)
0
>>> ftToCm(5)
0
```

One of the problems with testing by hand is that it is tedious, and folks have a tendency to skip it. So, experienced programmers have learned that it is generally a better idea to automate the process of testing. We’ll learn how to do that next. We'll see that when we set up six tests that we ran above: three of them will pass, and three of them will fail.

# Step 5: Setting up automated tests

Add this line at the top of your `convert.py` file:

```python
import pytest
```

Then, add the following code to your `convert.py` file _after_ the function definitions for `ftToIn`, `inToCm`, and `ftToCm` to define six automated tests:

```python
def test_ftToIn_zero():
    assert ftToIn(0.0) == pytest.approx(0.0)

def test_inToCm_zero():
    assert inToCm(0.0) == pytest.approx(0.0)

def test_ftToCm_zero():
    assert ftToCm(0.0) == pytest.approx(0.0)

def test_ftToIn_five():
    assert ftToIn(5.0) == pytest.approx(60.0)

def test_inToCm_60():
    assert inToCm(60.0) == pytest.approx(152.4)

def test_ftToCm_five():
    assert ftToCm(5) == pytest.approx(152.4)
```

These are automated tests that use a module(library) known as `pytest`. When defining tests using the pytest library, we typically define functions that:
* have names that start with `test_`,
* include the name of the function they are testing,
* end with exactly one `assert` statement--that is, the keyword `assert` followed by a boolean expression.

If the expression after `assert` is true, the test passes, otherwise it fails, and gives us an error message which explains what went wrong.

**Note** that all tests for our function `ftToIn` will begin with `test_ftToIn_`. In order to differentiate between the different test cases for the same function, we will need to include something else in the name of the test function that helps us test different cases. This is why we added `zero` and `five` to the end of the _test function's name_, so that we have two test functions that each test a different case:
* `test_ftToIn_zero`: tests the result of calling `ftToIn(0)`
* `test_ftToIn_five`: tests the result of calling `ftToIn(5)`

Similarly for the other functions and their tests.

We are using `pytest.approx()` here because any time you are testing with floating point numbers.
As we discussed earlier, we have to be aware that there may be some inaccuracy. Using `pytest.approx()` is a cleaner way of subtracting the expected value from the actual value, taking the absolute value, and checking if it is less than some tolerance which we touched on in Step 1. Using `pytest.approx()` allows for a tolerance of `1.0e-04`.

(Recall our discussion of what happens when you multiply `math.sqrt(2.0)` by itself. Here, it is probably overkill since we are not using any irrational numbers, but it is still safer to always use some way of approximating equality when dealing with floating point.)

Your entire file should look as follows at this point:
```python
import pytest

def ftToIn(feet):
    ''' TODO: add the docstring '''
    return (feet * 0)  #TODO: Fix this line of code
 
def inToCm(inch):
    ''' TODO: add the docstring '''
    return (inch * 0) #TODO: Fix this line of code
 
def ftToCm(feet):
    ''' TODO: add the docstring '''
    return (feet * 0) #TODO: Fix this line of code


def test_ftToIn_zero():
    assert ftToIn(0.0) == pytest.approx(0.0)

def test_inToCm_zero():
    assert inToCm(0.0) == pytest.approx(0.0)

def test_ftToCm_zero():
    assert ftToCm(0.0) == pytest.approx(0.0)

def test_ftToIn_five():
    assert ftToIn(5.0) == pytest.approx(60.0)

def test_inToCm_60():
    assert inToCm(60.0) == pytest.approx(152.4)

def test_ftToCm_five():
    assert ftToCm(5) == pytest.approx(152.4)
```

After entering this, save the file and use "Run Module" to make sure there are no error messages (error messages are displayed as red output in the Python Shell Window). If there are any, make sure to fix them before running the next step.

# Step 6: Running the test cases

Running the test cases requires us to go **outside of IDLE** back to the **terminal shell prompt**. Make sure to use `quit()` or Ctrl-D to exit the python shell (`>>>`). Once you are back on the command line prompt (that has a `$`) continue on.

Your current directory needs to be the same one that your `convert.py` file is stored in. That should be `~/cs8/{{page.num}}`, but if it is not, then fix things so that the `convert.py` file is in that directory, and your current working directory is set to that directory. If you need help, ask for assistance.

You should be able to type the `ls` command (or on Windows, `dir`) at the terminal shell prompt and see the `convert.py` file listed.

```
your-prompt-here $ ls
convert.py
your-prompt-here $
```

When that is the case, type this command after the `$` in your terminal window:
```
python3 -m pytest convert.py
```

You should see output like what is shown below. It may be a little overwhelming at first. Once you know what you are looking for, it is very easy to read. After the output, there is a guide to understanding it.


```text
169-231-175-204:lab01 cgaucho$ python3 -m pytest convert.py
================ test session starts =================
platform darwin -- Python 3.6.2, pytest-3.2.1, py-1.4.34, pluggy-0.4.0
rootdir: /Users/cgaucho/cs8/lab01, inifile:
collected 6 items

convert.py ...FFF            [100%]

====================== FAILURES ======================
__________________ test_ftToIn_five __________________

    def test_ftToIn_five():
>       assert ftToIn(5.0) == pytest.approx(60.0)
E       assert 0.0 == 60.0 ± 6.0e-05
E        +  where 0.0 = ftToIn(5.0)
E        +  and   60.0 ± 6.0e-05 = <function approx at 0x106853940>(60.0)
E        +    where <function approx at 0x106853940> = pytest.approx

convert.py:23: AssertionError
___________________ test_inToCm_60 ___________________

    def test_inToCm_60():
>       assert inToCm(60.0) == pytest.approx(152.4)
E       assert 0.0 == 152.4 ± 1.5e-04
E        +  where 0.0 = inToCm(60.0)
E        +  and   152.4 ± 1.5e-04 = <function approx at 0x106853940>(152.4)
E        +    where <function approx at 0x106853940> = pytest.approx

convert.py:26: AssertionError
__________________ test_ftToCm_five __________________

    def test_ftToCm_five():
>       assert ftToCm(5) == pytest.approx(152.4)
E       assert 0 == 152.4 ± 1.5e-04
E        +  where 0 = ftToCm(5)
E        +  and   152.4 ± 1.5e-04 = <function approx at 0x106853940>(152.4)
E        +    where <function approx at 0x106853940> = pytest.approx

convert.py:29: AssertionError
============ 3 failed, 3 passed in 0.07s =============
169-231-175-204:lab01 cgaucho$ 
```

Ok, let's now break down this output.

# Step 7: Understanding the output of pytest

Here's how to understand `pytest` output. 

1. <b>Get the big picture first from the `convert.py ...FFF` line</b>. 

   Look for a line near the beginning that has the name of your file, followed by a list of either dots, 
   letter `E` or letter `F` characters, like this one:

   ```
   convert.py ...FFF
   ```
   
   In this case, the `.` characters are tests that passed.  If you have four tests, then ideally, you'd want to see four dots, like this `convert.py ....`, which means that four tests for <tt>convert.py</tt> all successfully passed. 
   
   Instead, here, we see `...FFF`, which means we had three tests that succeeded and three tests that failed.   Later in the output, we'll see more detail about
   each of those failures.
   
2. <b>Understand the overall structure of the output.</b>

   The rest of the output will be divided into sections, one for each
   failure.  Here is what it look like with the
   details taken out so that you can see the big picture more easily:
   

```text
================ test session starts =================
   (blah blah here that you can ignore)
   
   convert.py ...FFF
====================== FAILURES ======================
__________________ test_ftToIn_five __________________
...
(details about the first test case failure are here)
...

___________________ test_inToCm_60 ___________________
...
(details about the second test case failure are here)
...

__________________ test_ftToCm_five __________________
...
(details about the third test case failure are here)
...
   
============ 3 failed, 3 passed in 0.07s =============
```
   
   Note that the last line gives us a nice summary: `3 failed, 3 passed in 0.03 seconds`.   
   
   We now know that 
   we need to focus on the three failures.   
   And the headers tell us which test cases failed, namely 
   `test_ftToIn_five`, `test_inToCm_60`, and `test_ftToCm_five`.
   So let's focus on those next, by first looking in detail at the first one:
 
3. <b>Focus in on the first test case failure.</b>
 
   Let's focus just on the detailed output for the first test case failure,
   `test_ftToIn_five`.  What does all of the detailed output mean?

   <style>
   div.explain-pytest table * td:first-of-type { width: 18em; font-size: 90%; }
   </style>
   
   Below is a breakdown of why the assertion turned out to be false, showing every step in the calculation.  Let's break it down one line at a time:
   
   <div class="explain-pytest" markdown="1">
   
   | line of output | meaning |
   |----------------|----------|
   | `def test_ftToIn_five():` |  first line of the failing test case |
   |`E      assert 0.0 == 60.0 ± 6.0e-05` | This is the assertion that turned out not to be true |
   |`E       +  where 0.0 = ftToIn(5.0)` | This tells us why `0.0` was on the left hand side of the `==`.  It was the result of computing `ftToIn(5.0)` |
   |`E       +  and   60.0 ± 6.0e-05 = <function approx at 0x106853940>(60.0)` | This tells us why `60.0 ± 6.0e-05` was on the right hand side of the `==`.  It shows the expected value (`60.0`) and the tolerance (` ± 6.0e-05`).
   |`E       +    where <function approx at 0x106853940> = pytest.approx` | This tells us that `pytest.approx` was used to calculate the tolerance. |
   | &nbsp; | &nbsp; |
   |`convert.py:23: AssertionError` | This shows which line in the file `convert.py` had the failed assertion, namely, line 23.  That helps us find the error faster if we are dealing with a large file of code.|
   
   </div>

   If we look at this, we can see that amidst all of the clutter is the
   crucial fact that `ftToIn(5.0)` returned `0.0` when what we were
   expecting was `60.0`, with a tolerance of `± 6.0e-05`.
            
# Step 8: Fixing the code

So, if you have failing test cases, the thing to do is fix the code so
that the test cases pass.

To do that you'll need to correct the formulas.

Keep in mind that in Python:

* The `*` symbol is used for multiplication.  In algebra, we can write
  `1.8x` to mean `1.8` multiplied by `x`, however, this does not work
  in Python.  In Python you must write `1.8` * `x` if you want to
  multiply the variable `x` by `1.8` (or `1.5` * `a` if you want to
  multiply the variable `a` by `1.5`, or `1.2` * `count` if you want to multiply the variable `count` (which could encode any value (i.e. `count` = `10`)) by `1.2` ...).

* The `+` and `-` symbols are used for addition and subtraction

* The `/` symbol is used for division, e.g '9/5' means nine
  divided by five.  

Also, the order of operations in Python is that multiplication and
division are done before addition and subtraction. Some examples: 

* If `x` is 5, then `x + 2 * 3` gives us 11, not 21.  The
  multiplication is performed before the addition.

* If `x` is 16, then `x - 6 / 2` gives us 13, not 5.  The division is
  performed before the subtraction.

* If you want to force the addition or subtraction to be done first,
  you *must use parentheses*, e.g., `(x + 2) * 3` or `(x - 6) / 2`.

Use the following conversions to correct the formulas in your functions:
```
    1 inch = 2.54 cm
    1 foot = 12 inches
```

When you replace return `feet*0` with the correct formula for converting feet measurement to inches, you should **remove the comment** that says `# TODO: Fix this line of code` and **update the docstring** accordingly (briefly explain what the input is and what the function returns).

You'll also want to replace the similar line in the other functions as you fix them.

When you have the test cases passing, try running the pytest command again (shown below)&mdash;remembering that:

* it <b>must be done from the Unix terminal shell</b>, NOT the Python shell.
* the current working directory of that terminal session must be
   the directory/folder where your `convert.py` file is located

```
python3 -m pytest convert.py
```

When you see all passing tests, your output will look like this. Also, the last line will be a pleasant shade of green instead of an angry looking red.

```
169-231-175-204:lab01 cgaucho$ python3 -m pytest convert.py
======================== test session starts =========================
platform darwin -- Python 3.6.2, pytest-3.2.1, py-1.4.34, pluggy-0.4.0
rootdir: /Users/cgaucho/github/cs8/lab01, inifile:
collected 6 items                                                     

convert.py ....

====================== 6 passed in 0.04 seconds ======================
169-231-175-204:lab01 cgaucho$ 
```

# Step 9: Submit your `convert.py` file to Gradescope

Before you submit your code to Gradescope, make sure that your file 
* is named `convert.py`
* does not have any `TODO` comments left in the code.
* contains a comment at the top of the file that says `Submitted by <name>, PERM, for CS 8 (W20)`. (Please, replace `<name>` and `PERM` with your first and last name and PERM number respectively.)

You are ready to submit your work to Gradescope.


Navigate to the Lab assignment "Lab01" and upload your `convert.py`, similar to how you submitted `hello.py` for Lab00. Gradescope will check if your functions are correct. If your tests do not pass, go back to these functions and double-check your conversion formulas and function syntax.


## Final Step:  Log Out

Actually, this is the final step of <em>every lab</em>.

In fact, you should do this every time you walk away from a lab computer, either in Phelps 3525 or CSIL.

Here's how:

* Find the System Menu at the top right of the screen.
* Select your name and in the dropdown click on "Log Out"


**Acknowledgment**: Special thanks to Sara Mandic who helped to update this lab.
