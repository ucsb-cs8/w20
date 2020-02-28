---
num: Lec 10
lecture_date: 2020-02-05
desc: range(), Loops
ready: true
reading:
---

```python
num = 1
while num < 11:
  if num == 8:
    break
  print(num)
  num += 1
print("Done with while")
```


# `range()` function

* Full format of the `range()`: `range(start_at, end_before, step_size)`

* Returns a range object
* Can convert a generated range into a list

```python
start_at = 1990
end_before = 2021
step_size = 10

our_range = range(start_at, end_before)
our_range = list(our_range)
print(our_range)

num = start_at
new_list = []
while num < end_before:
  print(num)
  new_list.append(num)
  num += step_size
print(new_list)

```


# `while` loop 
**A condition-controlled loop that
repeats while a condition is true
(i.e., until a condition is false).**

## `while` loop structure

```
while loop-continuation-condition:
  #loop body
  statement
  [statement]
  
```

Make sure that `loop-continuation-condition` eventually becomes false
* Otherwise, you get an infinite loop
* To stop an infinite loop, press Ctrl+C from the command window

The keywords allow you to interrupt the regular flow of loops are:

* `continue`

* `break`


# `for` loop

**A count-controlled loop that
repeats a specified number of
times.**


## `for` loop structure

```
for VARIABLE in COLLECTION:
    #loop body
    statement
    [statement]
```

No need to use the counter variable inside the loop (demo)


______________________________________________________________________________
# Thursday (2/6) Lecture 10 Notes

* Q: When should the i start at 0 vs 1?
  * A: When using i as an index, it tells us where we are starting at the beginning of the word or list, etc. So for this case, we usually start with 0.


# Lab04 Questions

* Q: How to use `pytest.approx` with lab04?
  * A: Give it the correct, exact answer (do not use rounded value shown in lab instructions).
If you use the approximated value, the value will not match what the function returns because the precision of the function is much higher than that of the approximation.
  * For pytest, you can do `pytest.approx(100 + 100*(5/100/12)) == my_func(100, 5, 1)`

* Q: Should we round our answers for lab04?
  * A: No

* Q: Do we have to include pytests in our file solution?
  * A: No, but feel free to submit your second file of pytests if you do create a second file


# Code from Lecture
## While loop practice
```python
# Print all even numbers from 11 to 50 (not including 50)

num = 11
stopNum = 50

while num < stopNum:
    if num % 2 == 0:
        print(num)
    num += 1
```

```python
# Print 5 numbers divisible by 7 from [20,30]

start = 20
stop = 80
num = start
count = 1 # could also start at 0. If you start at zero, later you would use < rather than <=

print("matches the second if: ")
while num <= stop:
    if num % 7 == 0: 
        if count <= 5: # Check that you have not yet printed 5
            print(num)
            count += 1
        else:
            break
    num += 1
```
***Question: Why is the second "if" indented?  Why is the "else: not indented?***
***Question: What happens if the "else" is in-line with the first "if" instead, like so?***

```python
print("Else matches the second if: ")
while num <= stop:
    if num % 7 == 0: 
        if count <= 5: # Check that you have not yet printed 5
            print(num)
            count += 1
    else:
         break
    num += 1
```

## Lab04 Attempt

```python
account = 100
rate = 5
# so after the first month, the rate is .05/12 = 0.00417

monthly_rate = rate / 100 / 12

value_in_account = account * (1 + monthly_rate)


print(value_in_account)

# For pytest, you can do pytest.approx(100 + 100*(5/100/12)) == my_func(100, 5, 1)
```

## range() function
```python

start_at = 14
end_before = 29
step_size = 3

our_range = range(start_at, end_before, step_size)
print(type(our_range))
print(our_range)
print(list(our_range)) # convert into a list


# Simulate the range with a while loop

num = start_at
while num < end_before:
    print(num)
    num += step_size


def rangeAsList(start, end, step):
    #returns range as a list
    num = start
    lst = []
    while num < end:
        lst.append(num)
        num += step

    return lst # must be outside of the while loop!
    
new_range = rangeAsList(start_at, end_before, step_size)
print("Custom range as a list")
print(new_range)
```

```python
start_at = 0 # default
end_before = 10
step_size = 1 # default

print("Range with all 3 values:")
print("start_at",start_at,"end_before",end_before,"step_size",step_size)
our_range = (start_at, end_before, step_size)
print(our_range)

print("Range with 2 values:")
print("start_at",start_at,"end_before",end_before)
our_range = (start_at, end_before)
print(our_range)

print("Range with 1 value:")
print("end_before",end_before)
our_range = (end_before)
print(our_range)
```


```python
start_at = 14 
end_before = 29
step_size = 3


num = start_at
while num < end_before:
    print(num)
    num += step_size


print("now, with a for loop")

for num in range(start_at, end_before, step_size):
    print(num)

```

```python
step_size = 1 # default

word = "CS8"
i = 0

print("Print word with a while loop")
while i < len(word):
    print(word[i])
    i += 1

print("Print word with a for loop")
for i in range(len(word)): # same as range(0, len(word), 1)
    print(word[i])

print("Print word with 'for character in word'")
for character in word:
    print(character)
    
```

```python
for course in ["CS8", "CS16", "CS24"]:
    if course == "CS16":
        print("I'm done")
        break
    print("I want to take", course)
```

what happens if I switch "break" to "continue"?

```python
for course in ["CS8", "CS16", "CS24"]:
    if course == "CS16":
        print("I'm done")
        continue 
    print("I want to take", course)
```

***Question: How can we use nested for loops to iterate through each character in a list of words?***

## Nested for loops

```python
for course in ["CS8", "CS16", "CS24"]:
    print("Every character in", course)
    for letter in course:
        print(letter)
```  


```python
word = "CS8"
i = 0
while i < len(word)
  print(word[i])
  i += 1

for i in range(0, len(word), 1):
  print(word[i])

num = 8
i = 0
while i < num:
  print("Hello, World!")
  i += 1
  
for i in range(num):
  print("Hello, World!")
```
