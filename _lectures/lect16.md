---
num: Lec16
lecture_date: 2020-02-26
desc: Recursion is Recursion
ready: true
---


# Thursday Lecture 2/27: Recursion!!!

* Example: How could you find out how many people are in line if each person can only see the person directly in front of them?
    * Each person asks the person in front of them "How many people are in front of you?" 
    * Since each person does not know the total, they will ask the person in front of them. 
    * Once the question reaches the first person in line, that person can confidently answer "There is no one in front of me."
    * Then, the person before them (the second person in line) can take the answer they got (0 people), add 1 to it, and answer with confidence that "There is one person in front of me." 
    * The 3rd person in line now adds 1 to it, and responds "There are two people in front of me." 
    * This can go on and on until the last person in line knows how many people are in line.

The simplest case is called the **Base case**: Theres nothing to do.

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

**Each recursive case gets you closer to the base case.**


```python3
def doDishes(numDishes):
    if numDishes == 0:
        # return "You're done!"
    else:
        # wash one dish
        # remove it from the sink
        # return doDishes(numDishes - 1)
```
(* Assume `numDishes` is a non-negative integer)


# The classic examples: Fibonacci and Factorials

## Factorial

```python3
def factorial(n):
    if (n == 0):
        return 1
    else:
        return (n*factorial(n-1))
```

what if `n = 2.1`

`2.1 - (1 * any integer)` will never equal 0. The base case will never be reached, so there will be an infinite recursion. 
Python cannot handle an infinite recursion, so it will produce an error: `RecursionError: maximum recursion depth exceeded in comparison`. This is the error that you'll see if your function never reaches **the base case**.

Let's create a new function that calls `factorial(n)`
if and only if the user inputs a valid type:

```python3
def getFactorial(n):
    '''
    check that n is an integer>=0
    return n
    Otherwise, print an error
    '''
    if type(n) != int:
        print("Error: incorrect type")
    elif n < 0:
        print("Error: incorrect value", n)
    else:
        return factorial(n)
```
* Question: What if the user inputs -2.1
* Question: couldn't you do the same using only if statements and return statements?
  * Answer: Yes, here is an example of that:
```python3
def getFactorial(n):
    '''
    check that n is an integer>=0
    return n
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

* 1 1 2 3 5 8 13
* 1 2 3 4 5 6 7
```python3
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

    # How do we generalize this
```
We can generalize this like so:

```python3
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
