---
num: "lec13"
desc: "String Formatting + File I/O + Dictionaries"
ready: true
lecture_date:  2019-11-12
reading: Chapters 4.1, 4.3, 6.1
---

```python
s = """We
are
going
to
have
FUN!
"""

# upper / lower case
# Useful for dictionary ordering
print(s)
print(s.lower()) # convert s to all lower-case characters
print(s.upper()) # convert s to all upper-case characters

#### Some more examples with String Formatting
price = 18.10
print("The price is ${}. That's cheap!".format(price))
print("The price is ${}. {}".format(price, "WOW!"))

#print("{} {}".format(price)) #ERROR
print("{} {}".format(price, 1, 2)) # OK, ignores third value

# Format specification
# { : } Left side of colon says which .format parameter # to use
# We can say:

print("{3:} {2:} {1:} {0:}".format('a','b','c','d'))

# This prints out d,c,b,a
# On the right we specify a FIELD WIDTH (i.e., how many spaces
# on the page to devote to this value)

print("==={}===".format(price))
print("==={:20}===".format(price)) # right justified (int or float)
print("==={:20}===".format("CS8")) # left justified (string)
print("==={:20}===".format(True)) # right justified (True == 1)
# We can use '>' or '<' to justify left / right
print("==={:<20}===".format("CS8")) # left justified (string)
print("==={:>20}===".format("CS8")) # right justified (string)
print("==={:^20}===".format("CS8")) # centered (string)

num_spaces = 20
format_str = "==={:<" + str(num_spaces) + "}==="
print(format_str.format("CS8")) # left justified (string)


# more examples
price = 12345.6
print("==={}===".format(price))
print("==={:10.2f}===".format(price)) # 12345.60
print("==={:10.5f}===".format(price)) # 12345.60000 (5 decimal spaces)
print("==={:3.2f}===".format(price)) # overflows allocated space

# can identify specific types that should be expected with 's' - string,
# 'd' - int, 'f' - float
course = "Computer Science"
num = 8
print("Discipline is {:12s}; course number is {:2d}; textbook cost ${:0.2f}".format(course, num, price))

print("Discipline is {:12}; course number is {:2}; textbook cost ${:0.2}".format(course, num, price))
# still works without s or d
# (we use these to do safe type checking if we're
#expecting certain types).
# Removing 'f' will display value in scientific
# notation: 1.2e+04
```

```
from random import randrange
# help(randrange)

def rollDie():
    return randrange(1,7)

diceTally = [0,0,0,0,0,0,0]

for rolls in range(100):
    value = rollDie()
    diceTally[value] += 1

print(diceTally)

def printDistribution(distributionList):
    for x in range(1,7):
        print(x, ": ", distributionList[x], sep='')
#        print("{:2d}: ".format(x), '*' * distributionList[x])

printDistribution(diceTally)
```
