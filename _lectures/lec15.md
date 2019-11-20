---
num: "lec15"
desc: "2D lists"
ready: true
lecture_date:  2019-11-19
reading: Chapter 5.2 and 5.3
---

# Variations of `for` loops

```python

word = "hello"
lst = [word, 1,2,3,4]

if (len(word) == len(lst)):
    for e in word:
        print(e)
        lst[e] = lst[e]*2
        print(e, lst[e], word[e])
    


# Adding your own index

word = "hello"
lst = [word, 1,2,3,4]

index = 0
step = 3
if (len(word) == len(lst)):
    for letter in word:
        print(e)
        index += step
        #lst[e] = lst[e]*2
        print(e, lst[index], word[index])
    

# Iterating through a list

word = "helloo"
lst = [word, 42, 1,2,3,4]

index = 0
step = 3
if (len(word) == len(lst)):
    for item in lst:
        print(item)
        """
        index += step
        #lst[e] = lst[e]*2
        print(e, lst[index], word[index])
        """
    
```


# 2D (two-dimensional) Lists

```python
"""
x = [42]*3

y = [0]

y.append(x)
y.append([0]*5)

print(x)
print(y)
"""

def print_screen( rows, cols):
    for i in range(rows):
        for j in range(cols):
            print("*", end="")
        print("\n", end="")

def print_screen( screen, rows, cols):
    for i in range(rows):
        for j in range(cols):
            print(screen[i][j], end="")
        print("\n", end="")
"""
def print_screen( screen, rows, cols):
    for i in range(rows):
        for j in range(cols):
            print(screen[i][j], end="")
        print("\n")
"""
def new_screen(rows, cols):
    """
    rows: number of rows in the array
    cols: number of columns in the array
    Returns a new array
    with `rows` elements that are 0
    """
    lst = []

    for i in range(rows):
        new_col = [0]*cols
        #print(new_col)
        lst.append( new_col )

    return lst
    
 
```

### Running in IDLE

```python
>>> my_screen = new_screen(5, 8)
>>> print_screen(my_screen, 5,8)
00000000
00000000
00000000
00000000
00000000
>>> my_screen[-2][0] = 1
>>> my_screen
[[0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [
1, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0]]
>>> print_screen(my_screen, 5,8)
00000000
00000000
00000000
10000000
00000000
>>> 
```
