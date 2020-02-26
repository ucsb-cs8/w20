---
num: Lec 16
lecture_date: 2020-02-26
desc:
ready: true
pdfurl:
---

# Recursion
* Recrusive functions call themselves to execute the same operations over and over
* Often, a recursive function can be written iteratively (with a loop), but they might behave differently
* A simple base case (or cases): does not use recursion to produce an answer

```python
def factorial(n):
  if(n == 0):
    return 1
  else:
    return (n * factorial(n-1))
'''
factorial(3)
  3 * factorial(3-1)
    2 * factorial(2-1)
      1 * factorial(1-1)
        1
'''

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

# new function
def getFactorial(n):
  if type(n) != int
    print ("Error: incorrect input type", type(m))
    return
  if n < 0:
    print("Error: incorrect input value", n)
    #return
  else:
    return factorial(n)    
```



