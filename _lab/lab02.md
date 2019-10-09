---
assigned: 2019-10-09
desc: Writing Functions, Tests, and using tkinter
due: 2019-10-23 08:59
layout: lab
num: lab02
ready: true

---

In this lab, you'll get more practice with:

* Wrting functions
* Testing functions with pytest
* Creating namedtuple object
* Using tkinter module

## This lab must be done solo.

# Step 1: Verify that `pytest` is working on the machine you plan to work on

Similar to lab01, you can check whether `pytest` is installed by typing in the following command in the Python shell prompt (`>>>`). 

```
[cgaucho@csil-12 ~]$ python3
Python 3.4.3 (default, Aug 9 2016, 15:36:17) [GCC 5.3.1 20160406 (Red Hat 5.3.1-6)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pytest
>>>
```
If it returns no error message (like is shown above), then `pytest` is installed. 
If you get an error, refer back to [lab01](lab/lab01/) for instructions on installing `pytest`.

# Step 2: Make a `~/cs8/{{page.num}}` folder.

The easiest way to create a new folder is to do the following, which will work from any directory:

`mkdir -p ~/cs8/{{page.num}}`

This form of the `mkdir` command, with the `-p` option/flag, has the advantage that

* It creates the entire path of directories in case any of the intermediate directories don't exist (that is, it will create a `~/cs8` directory too if it isn't there yet).
* If the directory being create already exists, it won't complain.
* Since the directory being created starts with `~`, which is the shortcut to the user's home directory, the command works regardless of the current directory.

Then, to get yourself into that directory, type:

`cd ~/cs8/{{page.num}}`

Again, it should work from any directory.

# Step 3: Create a file called `{{page.num}}.py` in your `~/cs8/{{page.num}}` directory

Refer to [lab00](lab/lab00) for how to create a new file.

### Step 3.0: Add the preliminary information

To start out {{page.num}}, **, write a comment with your name and PERM number in `{{page.num}}.py` (in general, you should write this on each of your submitted source files).**
   
Next, write the line:

```
import pytest
```

### Step 3.1: Add the function definition

Add the following function definition into your {{page.num}}.py file.

```
def perimRect(length, width):
   """ Compute perimeter of a rectangle """
   """ Using the formula: ADD THE FORMULA HERE """
   return -42.0 # stub  @@@ replace this stub with the correct code @@@   
```

### Step 3.2: Add the test functions
 
Add the following function definitions into your file. These are a special kind of function called a <em>test case</em>.  These particular test cases are written in the style used by the `pytest` testing framework, and they follow these rules:

1. The name of each test cases function must start with `test_`.
2. Each one ends (typically) with a line of code that starts with the keyword `assert`, followed by a boolean expression.
   * If the expression is `True`, the test case <em>passes</em>.
   * If the expression if `False`, the test case <em>fails</em>.
3. Each test case function must have a different name (hence: `test_perimRect_1`, `test_perimRect_2`, `test_perimRect_3`, etc.). They don't have to be consecutive numbers&mdash;we could use `_a`, `_b`, `_c` or anything really, as long as they are all different. In general though, your parameter, variable, and function names should be descriptive for better readability.

```
def test_perimRect_1():
   assert perimRect(4,5) == 18

def test_perimRect_2():
   assert perimRect(7,3) == 20

def test_perimRect_3():
   assert perimRect(2.1,4.3) == pytest.approx(12.8)
```

Finally, run the code, and ensure that you don't have any syntax errors in your Python code.

# Step 4: Test your code by hand

Because we want to be sure that you continue to practice the skill, test your code by hand first.

That is, select "Run Module" in IDLE, and then type in a few function calls at the Python Shell Prompt. Here are a few:

```
>>> perimRect(4,5)
-42.0
>>> perimRect(7,3)
-42.0
>>> 
```

Ok, we see that the function will continue to provide us with the same answer, consistent with the return value in our function definition. The point is that
* you need to know how to check the value of a function call by typing it in.
* you need to see that right now, the function *always* returns -42.0, no matter what.

There is a reason for that.  We call this a "stub value".  It returns the wrong answer *on purpose* so that we can check that all of the tests fail. We want to see all of the tests fail, and after we fix the function,we can to see all of the tests pass. That's the general idea.

* We want so see *all tests fail* when the function is wrong.
* Then if they *pass* when the function is right, we *trust* the test.

# Step 5: Run pytest on the file so far

As a reminder, you run pytest OUTSIDE of IDLE, at the regular terminal prompt (`$`).

You may find it helpful to bring up a second terminal window and use

```
cd ~/cs8/{{page.num}}
```

to get into the correct directory.  Then use:

```
python3 -m pytest {{page.num}}.py
```

You should see three test failures. If you do, then you ready to fix the code so that it works, which is the next step.

(If you need a refresher on how to interpret the output of `pytest`, refer back to [lab01](/lab/lab01/]).)

If you got a `SyntaxError: invalid syntax`, then verify that you are running the command not in IDLE (which has the `>>>` prompt), but in Unix (which has the `$` prompt).

# Step 6: Fixing the code for `perimRect`

As usual, if you have failing test cases, the thing to do is fix the code so that the test cases pass.

We hope you remember (or know how to find) the formula for the perimiter of a rectangle. First, write it as a comment in the appropriate section in your file.
Next, you'll have to convert that formula into Python, and use the variables `length` and `width` to get your function to work properly.   

Once you have the code correct, try testing both using interactive testing as well as by running `pytest`.

You are by no means finished with this lab. But, we want to encourage you to make a submission to Gradescope now anyway. Here is why:

1. After you upload your file, it will provids a backup copy of your work in case something goes wrong with your computer (yes, this happens and you want to make sure there is a backup somewhere).
    
2. You also will be able to see some progress towards completion of the lab&mdash; partial credit for completion of this step.

Once you've submitted and you see that you got more than 0 points, you are ready to continue with the rest of the lab.

# Step 7: Write an `areaTriangle` function and test cases.

You will write your own function `areaTriangle(base, height)` and some test cases in your `{{page.num}}.py` file.
Be sure you define your function's signature with the** exact name** shown here (otherwise, the tests on Gradescope are not going to pass).

It's also a good habit to define comments for all the functions you write. Include a comment for `areaTriangle` to describe what this function does. Note that the function comments have to either be in a string (as explained in the textbook), enclosed in triple single-quotes or in triple double-quotes (as shown in the `perimRect` function). Your function should return the area of a triangle using the base and height parameter values.

You should try to make the function pass the test cases that you put in.

In some cases you'll be given the test cases. In other cases, you have to supply these test cases yourself.

At each step, you should first try to get the test cases to pass by running `pytest` at the Unix command line as discussed above.

* Please do this BEFORE submitting to Gradescope.
* Please DO NOT upload your file to Gradesope without testing locally first.

Once you see your tests are passing, THEN submit a version to Gradescope to see if you also pass the test cases the instructor defined in Gradescope.

If you pass your own tests, but NOT the instructor supplied tests, then try to see if you can figure out why. Are there some cases that you did not consider?

In this step, you must define three test cases to test `areaTriangle`. The code for the first test case looks like this

```
def test_areaTriangle_1():
	assert areaTriangle(4,5) == 10
```

The second and third test case should be one that you come up with yourself. The restrictions are:

* the test functions must be called `test_areaTriangle_2` and `test_areaTriangle_3`
* they should have an `assert` statement
* the `assert` keyword should be followed by a call to `areaTriangle` with different parameter values in each test. 
* the call to the function is then followed by a test for equality using `==`, which is followed by the value that you expect `areaTriangle` to return for those argument values.

Once this is done, then:

* test your code with "Run Module" to make sure your code compiles without errors (i.e. no red messages).
* use `python3 -m pytest {{page.num}}.py -k areaTriangle` to run just the test cases for the `areaRect` function (there should be three of them, and three skipped test cases for perimRect).

Once everything passes correctly with `pytest`, submit your `{{page.num}}.py` file to Gradescope again to see if your submission passes the `areaTriangle` tests. You should see that you now have earned the next set of points if the `perimRect` and `areaTriangle` tests pass. 

# Step 8: Write and test a function using `namedtuples`.

In this step, you will write a function that computes the price of `n` copies of a `namedtuple` representing a Book object. Copy and paste the following code in your `{{page.num}}.py` file.

```
from collections import namedtuple

Book = namedtuple("Book", "title author price")
b1 = Book("Ready Player One", "Ernest Cline", 16)
```

Recall from lecture, this is how we defined a Book object with a `title`, `author`, and `price` attributes. We construct a specific book representing the_ Ready Player One_ book written by Ernest Cline that costs 16 dollars. We store this specific book representation in the variable `b1` (a name that we chose). 

Using this information, write the function `computePrice(n, book)` that returns the price of `n` copies of a book. Similar to `perimRect` and `areaTriangle` functions, write a brief comment in your `computePrice` function describing what the function does.

Write three test functions to test if `computePrice` works as expected. The code for the first test case looks like this

```
def test_computePrice_1():
	assert computePrice(0, b1) == 0
```

Write two more test cases, `test_computePrice_2` and `test_computePrice_3` with different values for `n`. Be sure to test if your code works with "Run Module" and use `python3 -m pytest {{page.num}}.py -k computePrice` to run just the test cases for the `computePrice` function.

Once everything passes correctly with `pytest`, submit your `{{page.num}}.py` file to Gradescope again to see if your submission passes the `computePrice` tests. You should see that you now have the correct number of points if the `perimRect`, `areaTriangle`, and `computePrice` tests pass. 

The last part of the lab gets you to explore how to create graphics using Python.

# Step 9: Using `tkinter` to draw a face

In this step, we will use the Python module `tkinter` used to draw simple graphics. This module has many features that you can read about using this link <https://docs.python.org/3/library/tk.html>, but for this step we will only use a small subset of `tkinter`'s functionality. The goal of this step is not to go through the details of `tkinter` (this will take more than one quarter of instruction to do so), but to use a simple subset of functionality to draw a face using a single function.

For this step, create a new file called `{{page.num}}_face.py` in your `~/cs8/{{page.num}}` directory.

First, we will create a canvas to draw things on. Copy and paste the following code in your `{{page.num}}_face.py`.

```
import tkinter # Imports the tkinter library in your program

window = tkinter.Tk() # Create a window to draw graphics on

canvas = tkinter.Canvas(window, width=500, height=500)
# Create a 500x500 pixel canvas

canvas.pack() # Places the canvas in the window
```

You can think of the canvas with `(x,y)` coordinates, but it's a little different than a typical cartesian coordinate graph. Think of the canvas with an origin point `(0,0)` as the **upper left corner** of the window. 
* `x` values increase as you move right along the window,
* `y` values increase as you move down the window. 
* Any negative `x` or `y` value will not be displayed on the window since all coordinates within the canvas should have positive values.

We can draw ovals on our canvas using the `create_oval(x1, y1, x2, y2)` function. 
* `x1` and `y1` defines the upper left point
* `x2` and `y2` defines the lower right point of a rectangle.
* `create_oval` draws an oval within this rectangle boundary defined by the upper-left and lower-right points.

Run the following code to illustrate the coordinate system. This code does not necessarily need to be part of your final submission, but it is a helpful visualization:

```python
canvas.create_oval(0, 0, 10, 10, fill="black")
canvas.create_line(5, 5, 5, 500, fill="red")
canvas.create_line(5, 5, 500, 5, fill="blue")
```

The above code draws a circle centered at (5, 5) to mark a point near the origin, it draws the y axis in red, and it draws the x axis in blue. You can see the origin in the **upper left**: this is a common convention in computer graphics, and it reflects the convention used in matrix indexing, where the top left matrix element is usually referred to as element (0, 0).

Copy and paste the following function definition and function call in your `{{page.num}}_face.py` file.

```python
def drawFace():
	""" Draw a face on the canvas """
	# Draw head
	canvas.create_oval(100, 100, 400, 400)

	# Draw left eye
	# TODO

	# Draw right eye
	# TODO

	# Draw mouth
	# TODO
    
drawFace() # Call the function to draw a face
```

The first thing to note is that `drawFace` does not return a value. Functions may or may not return a value depending on what they may be used for. In this case, the purpose of `drawFace` is to simply display something on the screen. Without a `return` statement in a function, the `None` type is returned.

Select "Run Module" to see your window and a "head" drawn on it (IDLE creates a graphics window when you run this module. If you don't see it, it might be hidden behind other windows on your computer screen).

This function already draws a circle with a diamater of 300 pixels representing the face's head. We can also fill the circle with a color by passing in an optional parameter to `create_oval`. For example, we can draw a green circle for the head by adding the `fill="green"` parameter like this

```
canvas.create_oval(100, 100, 400, 400, fill="green") 
```

`tkinter` accepts many pre-defined color strings such as `"red"`, `"blue"`, `"yellow"`, `"black"`, `"dodger blue"`, etc. A list of predefined color strings can be found here: <https://wiki.tcl.tk/37701>.

Complete the `drawFace()` function definition (completing each of the "TODO" parts) by drawing the remaining parts of the face. Your face drawing must
* have the eyes and mouth contained within the head
* have the left and right eye be the same size and color
* the eyes, head, and mouth must be different colors
* the left and right eye must be above the horizontal center of the head
* the mouth must be below the horizontal center of the head
* the left and right eye must be symmetrical with respect to the vertical center of the head

An example face can look like this

![tkinter Face](face.png)

# Step 9.5: Bonus! Draw a Mickey Mouse face

This is an extra credit, bonus exercise for you to have fun with tkinter.

Below is a reference image. You'll need to use your skills from step 9 to create the head, ears, eyes, nose, and mouth - they won't look exactly like the picture, and some approximation will be necessary since the mouth is not a perfect ellipse. Feel free to be creative. :-)

Save your file as `{{page.num}}_bonus.py` and upload it to Gradescope.

![Mickey Mouse face](mickeymouse.png)

# Step 10: Uploading your files to Gradescope

Navigate to the Lab assignment "Lab02" on Gradescope and upload your `{{page.num}}.py` and `{{page.num}}_face.py`. 
Even though Gradescope will not auto-check your drawing, you must upload `{{page.num}}_face.py` file to receive credit for this step.
If you did the bonus part, upload that file here as well.

Your Gradescope submission containing the functions you wrote will be autograded. Our TAs will grade your `pytest` functions and your face drawing manually.
This lab is out of 100 points. 
