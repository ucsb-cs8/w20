---
num: "lec20"
desc: "Recursion + Exam Review"
ready: true
lecture_date:  2019-12-05
reading: Chapter 10
---

# Code from lecture

```python
def sumOdd( L ):
    """
return a sum of odd integers in L
recursive solution
If the list is empty or contains odd values
return the sentinel value of None
    """
    if len(L) == 1: # base case
        if (L[0] % 2 == 1): # odd
            return L[0]
        elif (L[0] % 2 == 0): # even
            return None
    else: # recursive case
        last_el = L.pop()
        if (last_el % 2 == 1):
            return last_el + sumOdd(L) # input the smaller list
        else:
            return sumOdd(L)
```

These were the cases (input and output) we identified that we can test our algorithm on:

```
[] --> None
[1] --> 1
[2] --> None
[1,1] --> 2
[2,2] --> None
[1,2] --> 1
```

Notice that the above solution does not handle the empty list. How would you modify the code to correctly return `None` if the list is empty?

This is just one possible implementation of this function. Alternatively, you can be processing the list starting from the first element instead.

A great question/discussion during the lecture pointed out that `None` as a sentinel value allows us to distinguish it from 0, which is a valid sum if our list is not empty and contains, for example, `[-1, 1]`.
