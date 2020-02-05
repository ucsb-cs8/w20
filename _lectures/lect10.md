---
num: Lec 10
lecture_date: 2020-02-05
desc: range(), Loops
ready: false
pdfurl:
---

# `range()` function

* Full format of the `range()`: `range(start_at, end_before, step_size)`

* Returns a range object
* Can convert a generated range into a list


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
