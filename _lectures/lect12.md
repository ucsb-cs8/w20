---
num: Lec 12
lecture_date: 2020-02-12
desc:
ready: false
pdfurl:
---

# Wednesday Lecture Notes...

## Using Loops With a Negative Increment

```python3 
i = 3
while i >= 0: #Notice we use > rather than < because we are going backwards
    print(i)
    i = i - 1 #same as i -= 1
```

This will output:

```
3
2
1
0
```

The same while loop as a for loop using the range function looks like:

```python3
for i in range(3, -1, -1): #In order to include the 0, we must use -1 as the stop value
    print(i)
```

These are pretty straight-forward when the elements we want to print are integers, but what if we wanted to loop through a list or a string, accessing each element?
## Looping through a String or List
```python3
text = "Hello"

i = 0
while i < len(text):
    print(text[i])
    i += 1
```
The same while loop as a for loop with the range function looks like:

```python3
text = "Hello"
for i in range(0, len(text),1):
    print(text[i])
```
The same while loop as a for loop using text as an iterable looks like:

```python3
text = "Hello"
for char in text:
    print(char)
```

***Question: When should I use the range vs when should I use the other for loop?***
Answer: Use the iterable version when you only care about the value/element and you do not care about the index position. If the index position matters, use the range-based for loop. If you are unsure, use the range-based for loop since you can still access the elements of the string or list by using indexing, and you will also be able to know the index position.

## Nested Loops

If you want to print a right triange of stars like so:
```
*   
**  
*** 
****
```
Such that the base and height are equal, how could you do that? <br/>
Notice that for this triangle with 4 rows and 4 columns,
```
when r=0 and c=0, there should be a *
when r=1 and c=0, there should be a *
when r=1 and c=1, there should be a *
when r=2 and c=0, there should be a *
when r=2 and c=1, there should be a *
when r=2 and c=2, there should be a *
when r=3 and c=0, there should be a *
when r=3 and c=1, there should be a *
when r=3 and c=2, there should be a *
when r=3 and c=3, there should be a *
```

```python3
num = 4
result = ''
for row in range(0, num, 1): # same as range(num)
    for col in range(num):
        if row >= col:
            result += '*'
    result += '\n'
    
print(result)
```
If you were given a list of strings like so: 
```
l = ["one","two","three"]
```
How could you print each element of l backwards, like so:
```
e
n
o

o
w
t

e
e
r
h
t
```

```python3
l = ["one","two","three"]
for element in l: # we dont need the index to look at each element in order
    for i in range(len(element) - 1, -1, -1): # the index DOES matter for printing each word backwards, so we will use range
        print(element[i])
    print('\n')
```
***Question: How could you print each letter on the same line?***
```python3
l = ["one","two","three"]
for element in l: 
    for i in range(len(element) - 1, -1, -1):
        print(element[i], end = '')
    print('\n')
```
