---
num: Lec 17
lecture_date: 2020-03-02
desc:
ready: false
pdfurl:
---

# Python Dictionaries

## Review

### Soliving Recursion
- Step 1: A simple base case (or cases): does not use recursion to produce an answer
    - typically returns a fixed value
    - the simplest possible case
- Step 2: A recursive case, when the function calls itself on the next simplest input
    - Usually has to include a return statement (unless we only need to print)
    - Always has to call the function itself....
    - ....with the input to the recursive function that gets you closer to the base case
- Note: the structure would usually involve having if / else statements 

### Questions to ask to solve recursion
- What's our base case(s)?
    - What's printed or returned?
- What's the next simplest input (first recursive case)?
    - What action do we need to take to get from the first recursive case to the base case?
    
### A skeleton of the recursive function
```python
def recF (input):
    if input ...:
        print/return # base case(s)
    else / elif:
        print/return recF (input # --> base case)
```

## Note on Labs:

Lab grades to be released soon, if you did not name your files/functions correctly, Gradescope will give you a 0. Don't freak out! You can submit a regrade request and Prof. K will rename and reupload you files. Unfortunately, nothing can be done for functions that were not named correctly.

## Recursion Practice (slide 11)

Create a recursive function called `countdown()` that takes a parameter n and recursively counts down from parameter n and recursively counts down from n to 0 (inclusive of both), mirroring the values around the output of 0.
- Example: `countdown(2)` would output:
```
2
1
0
1
2
```

What would our function look like?

Let's pull up our list of questions:
    - Our base case is `n == 0`
    - The action that should be taken in our base case is `print(n)`
    - The first recursive case is `n == 1`
    - The action that should be taken to get from our first recursive case to the base case is `countdown(n-1)`
        - Two parts: action calling the function and an action handling the input itself

Question: Do we need a break after the base case?
- No, because the function ends after the base case

Question: What happens if we replace `print` with `return`?
- All values get returned, so there is nothing left to be the recursive input

Now, let's move on to `countdown_mirror()`
    - Base case doesn't change
    - The additional action is the mirroring part
    
Once you figure out your first recursive case, 99% of the time you're done!

### Slide 16-17:
- Need the result of the `countdown(3-1)` before it is able to `print(2)`, need the result of `countdown(2-1)` before it is able to `print(1)`, need the result of `countdown(1-1)`: which is just print(0)
- Executes from the top to the bottom of the function call

Question: What if we used a return in this function?
`a = return countdown_mirror(n-1)` ==> Not valid syntax, return is a standalone function
- But we can use result
`a = countdown_mirror(n-1)` ==> Won't work either because the result is None

Question: Do I always need to use input `==` something? 
- No! Sometimes your base case includes a range of numbers

## Dictionaries

A new data structure.
- We had basic variables as different variable types (ints, strings, etc)
- Can also have a data type that is a combination of variable types (lists)

Dictionaries are sometimes referred to as tables or maps
- Some sort of word (a key) with definitions provided as a table, and the corresponding definition is a value from the table 
- Mapping!
- ie. username and password

Searching through dictionaries is much faster than lists!

```python
# Demo of the speed difference
```

In order to get an item out of the list, we need to know the index of the item. For dictionaries, we don't really care about that. All we need is the key. For example, if we want to print the number of bananas, all we need is the key (banana).

Question: Can we put a dictionary inside of another dictionary?
- It depends as what you're storing it as
- Keys have to be immutable, but corresponding values can be mutable!

If we are looking for a key in a dictionary that doesn't exist in the dictionary, python will gives us a `KeyError`.

```python
# .get() code
```

By default, `.get()` returns `None` if a key is not present in a dictionary. 

We are able to add a key and a corresponding value to our dictionary
- use .get() to check if the key exists in the dictionary

Question: how would we reassign a value of an existing key?
`D['pear'] = 55`

`from time import perf_counter`
- python's way of keeping track of time
- tells us how long it takes python to perform a function


What this code is doing:
- Opening a file for reading
- Reading all of its input
- Storing it into a large text variable
- Splitting the words
- Converting them to lowercase and stripping special characters
- Incrementing the counter for any words that we find in wordlist
- AND now we also have the time this took in seconds!

Once we have our dictionary, sometimes 

Notice, the values inside a dictionary are their own type called dict_values
- Even though they look like lists/tuples!
- They are mutable values
- Views dynamically update values in dictionary so don't rely on them to be saved!

Question: Are the keys or the values the view type?
- Values! These are the items which will be dynamically updated.

