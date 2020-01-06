---
assigned: 2020-01-13
desc: Writing Test Cases
due: 2020-01-20 08:59
layout: lab
num: lab01
ready: false
---

In this lab, you'll practice:

* Creating a file that has some functions in it
* Testing those functions interactively at the Python prompt
* Creating a file of automatic test cases for those functions
* Running those test cases
* Submitting your functions and test cases to Gradescope for grading


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

To install pytest on Windows, see [this tutorial](http://meingraffiti.blogspot.com/2015/09/installing-pytest-on-windows-platform.html)
 
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

# To be conitnued ...
