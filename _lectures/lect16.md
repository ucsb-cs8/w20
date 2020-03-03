---
num: Lec16
lecture_date: 2020-02-26
desc: Recursion is Recursion
reading: Chapter 10
ready: true
---

# Reading
* Chapter 10 in the Perkovic book
* Read the chapter up until “Fractals” (page 338)
* Read from “Linear Recursion” (page 345) up until Section 10.4 “Searching”
* Work through the sample problems and the exercises in the book


# Recursion
* Recrusive functions call _themselves_ to execute the same operations over and over
* Often, a recursive function can be written iteratively (with a loop), but they might behave differently and can be harder to write
* A simple base case (or cases): does not use recursion to produce an answer


* Example: How could you find out how many people are in line if each person can only see the person directly in front of them?
    * Each person asks the person in front of them "How many people are in front of you?" 
    * Since each person does not know the total, they will ask the person in front of them. 
    * Once the question reaches the first person in line, that person can confidently answer "There is no one in front of me."
    * Then, the person before them (the second person in line) can take the answer they got (0 people), add 1 to it, and answer with confidence that "There is one person in front of me." 
    * The 3rd person in line now adds 1 to it, and responds "There are two people in front of me." 
    * This can go on and on until the last person in line knows how many people are in line.

The simplest case is called the **Base case**: There is nothing to do.

**Example: Doing dishes**
* Simplest case (base case): There are no dishes. You're done!
* Next simplest case: There is one dish. You wash it and remove it from the sink. 
   * Now, you are back to the base case -- there are no dishes. You're done!
* Next simplest case: There are two dishes. 
   * You wash one and remove it from the sink.
   * Now, we are back to the previous simplest case when there is one dish. You wash it. 
   * Now, you are back to the base case -- there are no dishes. You're done!
* Next simplest case: There are 3 dishes. You wash one. Now there are 2 dishes. You wash one. Now there is one dish. You wash it. Now there are no dishes. You're done!
* etc.

**Each recursive case _should_ get you closer to the base case.**


```python
def doDishes(numDishes):
    if numDishes == 0:
        # return "You're done!"
    else:
        # wash one dish
        # remove it from the sink
        # return doDishes(numDishes - 1)
```
(* Assume `numDishes` is a non-negative integer)


See slides for additional examples of recursion (e.g., Droste Effect, Sierpinski triangle).


# Solving recursion
* A simple **base case** (or cases): does not use recursion to produce an answer
   * typically returns a fixed value
   * the simplest possible case
* A **recursive case**, when the function calls itself on the next simplest input
   * Usually has to include a `return` statement (unless we only need to print)
   * Always has to _call the function itself_ ...
   * ... with the input to the recursive function that gets you _closer to the base case_
* Note: the structure would usually involve having `if / else` statement(s) to decide which case to run
* Goal: find a set of rules that reduce all other cases toward the base case.


When designing a recursive solution, we need to answer the following questions:

* What's our base case (or cases)? 
* What action should be taken in the case case? What is `print`ed or `return`ed?
* What's the **first recursive case** (next simplest input)? 
* What action do we need to take to **get from the first recursive case to the base case**? 



# A skeleton of the recursive function

```python
# Note, this is just a pseudocode skeleton structure
def recF(input): 
   if input ...
      print/return # base case / cases 
   else / elif
      print/return recF( input => base case ) 

# => stands for "that gets you closer to"
# so, the recursive case is supposed to use
# the input that gets you closer to the base case
```


# The classic examples: Fibonacci and Factorials

## Factorial

Factorial represents the number of permutations (combinations) of arranging a set of `n` items.

```
n n! Resulting combinations of n items
1 1  {1}
2 2  {1,2}, {2,1}
3 6  {1,2,3}, {1,3,2}, 
     {2,1,3}, {2,3,1},
     {3,1,2}, {3,2,1}
``` 

In other words...
```
• 0! = 1 # An empty set can only be ordered one way, so 0! = 1
• 1! = 1
• 2! = 2∙1=2
• 3! = 3∙2∙1=6
• 4! = 4∙3∙2∙1 = 24

Looks like we have a formula:
n! = n∙(n – 1)!
```

So, for any given `n`, to compute the factorial of `n`, we need to find the product of the successive numbers between 1 and `n`.

Let's try expressing this in Python. 

But first, we need to answer:
* What's our base case (or cases)? 
   * What's `print`ed or `return`ed?
* What's the next simplest input (**first recursive case**)? 
   * What action do we need to take to **get from the first recursive case to the base case**? 


If we correctly answer these questions, we would have the pseudocode / algorithm for the solution:

* What's our base case (or cases)? `0! or 1!`
      * What's `print`ed or `return`ed?
         * We need to `return 1`
* What's the next simplest input (**first recursive case**)? That would be `2!`.
   * What action do we need to take to get from the first recursive case to the base case? 
      * We need to `return` the `2` multiplied by the previous factorial, which is `1!`
      * To get the "previous factorial" from the step above using our current input `2`, we need to use `(2-1)! = 1!`
      
Let's check if the above logic works for the next recursive case, which is `3!`.

* Next recursive case: input `3` (i.e., compute `3!`) 
   * **What action do we need to take to get from this input to the case that's closer to the base case?**
      * We need to `return` the `3` multiplied by the previous factorial, which is `2!`
      * To get the "previous factorial" from the step above using our current input `3`, we need to use `(3-1)! = 2!`
      * Note that this correctly gets us back to the first recursive case, which is `2!`, and from there, we know that `2!` goes to the base case.
      * Woohoo! Recursion works.
 
 And now in Python:

```python
def factorial(n):
    if (n == 0):
        return 1
    else:
        return n*factorial(n-1)
```

Now, the call of `factorial(3)` results in the following **call stack** (similar to the steps we traced above):

```python
factorial(3)
  3 * factorial(3-1)
      2 * factorial(2-1)
          1 * factorial(1-1)
              1
```

**Note**: if we forget to include the `return` inside the recursive case, then the function will **return nothing**, which means the return _value_ will be `None`.


## Checking for invalid input

* What if `n` is set to be `"two"`?

```python
>>> factorial("two")
...
    return n * factorial(n-1)
TypeError: unsupported operand type(s) for -: 'str' and 'int'
```
The `TypeError` points at the fact that we cannot use a subtraction between `str' and 'int'`.

* What if `n` is `2.1`?

```python
>>> factorial(2.1)
  ...
    return n * factorial(n-1)
  [Previous line repeated 1021 more times]
  File "/....py", line 2, in factorial
    if n==0:
RecursionError: maximum recursion depth exceeded in comparison
```

`2.1 - (1 * any integer)` will never equal 0. The base case will never be reached, so there will be an infinite recursion. 
Python cannot handle an infinite recursion, so it will produce an error: `RecursionError: maximum recursion depth exceeded in comparison`. 
This is the error that you'll see if your function never reaches **the base case**.

### Writing helper functions

However, we **should not** check if we got the correct input _within_ the recursive function, 
because the code of the recursive function runs _every time_ that function is called.
Instead, we want to check the input **once**, to decide if it is safe call the recursive function.
In this case, the recursive function will be the _helper function_.


Let's create a new function `getFactorial(n)` that calls `factorial(n)` 
_if and only if_ the user inputs a valid value of the valid type.

Below is one potential version with a very generic error.

```python
# One potential version
def getFactorial(n):
    '''
    Check that n is >= 0
    and is an integer.
    If it is not, print an Error,
    Otherwise, return the value n!
    '''

    if type(n) == int and n >= 0:
      return factorial(n)
    else:
      print("Error")
```

Here's another potential version with the two check separated using `if / elif`:

```python
def getFactorial(n):
    '''
    check that n is an integer>=0
    return n!
    Otherwise, print an error
    '''
    if type(n) != int:
        print("Error: incorrect type")
    elif n < 0:
        print("Error: incorrect value", n)
    else:
        return factorial(n)
```

* Question: Could you do the same for type checking using only `if` statements and `return` statements (instead if `if` and `elif`)?
  * Answer: Yes, you can: as long as you include the `return` that stops the function. Otherwise, you need an `elif`, so that you do not proceed with the rest of the function, since you do not want to call `factorial(n)` with an invalid `n`. 
  
  Here is an example of how you can write this function using only `if` statements and `return` statements:
  
```python
def getFactorial(n):
    '''
    check that n is an integer>=0
    return n!
    Otherwise, print an error
    '''
    if type(n) != int:
        print("Error: incorrect type")
        return
    if n < 0:
        print("Error: incorrect value", n)
        return
    else:
        return factorial(n)
```

**Note**: if we forget to include the `return` inside the recursive case, then the function will **return nothing**, which means the return _value_ will be `None`.

```python
>>> getFactorial(2)
>>> num = getFactorial(2)
>>> print(num)
None
```

Once we add the `return`, we can correctly check if the function correctly handles it if the user inputs `-2.1`.

```python
>>> getFactorial(2)
2
>>> getFactorial(4)
24
>>> getFactorial(2.1)
Error: incorrect type
>>> getFactorial(-2)
Error: incorrect value -2
>>> getFactorial("two")
Error: incorrect type
```


We can also get very descriptive and output the incorrect type and the value of the provided input.

```python
# new function
def getFactorial(n):
   '''
   check that n is an integer>=0
   return n!
   Otherwise, print an error
   '''
   if type(n) != int
      print ("Error: incorrect input type", type(m))
      return
   if n < 0:
      print("Error: incorrect input value", n)
      #return # see what happens if there's no return
   else: # n is a valid input
      return factorial(n)    
```



## Fibonacci numbers
A Fibonacci number is a number in a sequence of numbers (the Fibonacci sequence), such that each number is the sum of the two preceding ones. 
The Wikipedia article has a lot of fascinating information about the [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number) (did you know that they are related to the golden ratio?).
Sometimes, you see the Fibonacci sequence starting from 0 and 1.
In lecture, we started them at 1 and 1.

* `1 1 2 3 5 8 13 ...` Fibonacci numbers (values)
* `1 2 3 4 5 6 7  ...` the index `n` of each number (e.g., 1st, 2nd, 3rd Fibonacci number)

```python
def fibonacci(n):
    '''
    returns the nth fibonacci term
    '''
    if n == 1:
        return 1
    if n == 2:
        return 1
    if n == 3:
        return fibonacci(1) + fibonacci(2)
    if n == 4:
        return fibonacci(2) + fibonacci(3)
    if n == 5:
        return fibonacci(3) + fibonacci(4)

        ...

    # How do we generalize this?
```

We can generalize this like so:

```python
def fibonacci(n):
    '''
    returns the nth fibonacci term
    '''
    if n == 1:
        return 1
    if n == 2:
        return 1
    else:
        return fibonacci(n - 2) + fibonacci(n - 1)
```  

# Recursion in CS 16 and beyond

If you continue taking CS classes, you'll see recursion again in CS 16 and beyond:
* Recursion on the linked lists 
* Binary search
* Traversing networks
* Web-based operations
