---
num: Lec 16
lecture_date: 2020-02-26
desc:
ready: false
pdfurl:
---


# Thursday Lecture 2/27: Recursion!!!

* Example: How could you find out how many people are in line if you can only see the person directly in front of you?
    * Each person asks the person in front of them "How many people are in front of you?" Since each person does not know, they will ask the person in front of them. Once the question reaches the first person in line, that person can confidently answer "There is no one in front of me." Then, the second person can answer with confidence that "There is one person in front of me." The 3rd person in line can know "There are two persons in front of me." This can go on and on until the last person in line knows how many people are in the line.


Base case: Theres nothing to do.
Example: Doing dishes
* Simplest case (base case): There are no dishes. You're done!
* Next simplest case: There is one dish. You wash it. Now there are no dishes. You're done!
* Next simplest case: There are 2 dishes. You wash one. Now there is one dish. You wash it. Now there are no dishes. You're done!
* Next simplest case: There are 3 dishes. You wash one. Now there are 2 dishes. You wash one. Now there is one dish. You wash it. Now there are no dishes. You're done!
* etc
```python3
def doDishes(numDishes):
    if numDishes == 0:
        # return "You're done!"
    else:
        # wash one dish
        # return doDishes(numDishes - 1)
```
(* Assume numDishes is a non-negative integer)

# The classic examples: Fibonacci and Factorials
* Factorial
```python3
def factorial(n):
    if (n == 0):
        return 1
    else:
        return (n*factorial(n-1))
```
what if n = 2.1

2.1 - (1 * any integer) will never equal 0. The base case will never be reached, so there will be an infinite recursion. Let's create a new function that calls factorial(n)
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
