---
num: Lec 10
lecture_date: 2020-02-05
desc: range(), Loops
ready: true
pdfurl:
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
