---
num: Lec18
lecture_date: 2020-03-04
desc:
ready: true
pdfurl:
---

# Questions
* Question: Why would you just want to store one object in a tuple?
* Ans: If you store stuff in a tuple, the object will not change.

```python
def printPet(aDict, key):
  age = aDict[key]['age']
  pettype = aDict[key]['type']
  date = aDect[key]['date']
  format_str = "{} is a {} who is {} old and we got it on {}"
  print(format_str.format(key, pettype, age, date))

'''
Output:
printPet(pets,'Cutie')
Cutie is a poddle who is 3 months old and we got it on 03/04/2020
'''
```
_____________________________________________________________________________________________________________________________
# Slicing iClicker Questions
1. 
```python
>>> title = "Miss America"
>>> print( ??? )
'America'
```

Answer: B
```python
print(title[5:])
```
2. 
```python
>>> mylist = [11, 12, 81, 88, 123]
>>> print( ??? )
[81, 88]
```
Answer: C

```python
print(myList[2:4])
```
*** Question: If I put endpoint as len(myList), would it include the last character? ***
* Answer: Yes, it will include it because the length of a list or string will always be one more than the number corresponding to the last index

# Tips and questions to consider for the recursive substring problem:
* You can have multiple base cases!
* What is the simplest case for this problem?
* If your substring is longer than your string, what should you do?
* What if the lengths are the same, what can you do?
* What about if neither of those are true? You can start slicing off characters of the string and continue to compare...

# Dictionaries
*** Question: What are dictionaries good for? ***
* Answer: 
  * If we used a list, we would have to store each key and value pair as a list within a list. Then it will be difficult
to pull out the information I want for certain things. I would have to loop through the list until I found the value that I want.
  * Dictionaries make it much easier to find the values we need.
  * It would make searching for things much faster.
  * We wouldn't have to worry about storing the index for something.
  * The order/indexing doesn't matter for the keys.

*** Question: Does it have to be in a certain order if we are storing multiple things for each key in the dictionary? ***

# Example of a nested dictionary
lets store the type of each cookie, the price of each cookie, the calories in each cookie, and number of cookies we have.

```python
cookieType = ['chocolate chip', 'macnut cookie', 'peanut butter']
cookiePrice = ['$20','$30', '$3']
caloriesPerCookie = [112, 200, 1000]
numOfEachCookie = [3,15, 2001]
```
```python
def printCookie(index, cookieType, cookiePrice, caloriesPerCookie, numOfEachCookie):
    format_str = "The cookie {} ({} items) has {} calories, costs {}"
    print(format_str.format(cookieType[index], cookiePrice[index], numOfEachCookie[index], caloriesPerCookie[index]))
```
This is kind of messy... Lets try using a dictionary
```python

cookies = {'chocolate chip': {'price': '$20',
                                 'amount': 3,
                                 'calories': 112},
           
              'macnut cookie': {'price': '$30',
                                'amount': 15,
                                'calories': 200},
              
              'peanut butter': {'price': '$3',
                                'amount': 2001,
                                'calories':1000}
              }

def printCookie( cookieD, key):
    format_str = "The cookie {} ({} items) has {} calories, costs {}"
    name = key
    price = cookieD[key]["price"]
    amount = cookieD[key]["amount"]
    calories = cookieD[key]["calories"]
    print(format_str.format(name, amount, calories, price))
 ```
*** Question: Could you change the calories and amount to be a string? ***
* Answer: Yes, but leaving it as an integer allows us to more easily do math if we wanted to add more cookies later on.


*** Question: How can we add a new cookie to the dictionary? ***
 ```python
 cookies["mint chocolate"] = {'price': '$5',
                                 'amount': 10,
                                 'calories': 435}
```

Also, notice that we don't have to have all of the information in there. For example, if we did not know the calories, we
could just leave it out like so:
```python
cookies["oatmeal raisin"] = {'price': '$0',
                                 'amount': 367}
```
# Named Tuples
```python
from collections import namedtuple
# Design your named tuple object
Student = namedtuple('Student', 'name perm major')
# create new objects of type Student
s1 = Student("Olivia", 1234567, "CS")
# Access the elements of the object:
print(s1.name, s1.perm, s1.major, sep = " ")
```

# Example with a cookie NamedTuple
```python
>>> Cookie = namedTuple("Cookie", 'name price amount calories')
>>> c1 = Cookie("chocolate chip",'$20', 3, 112)
>>> c1.name
'chocolate chip'
>>> c1.calories
112
```
```python
def printCookie( ntuple ):
    format_str = "The cookie {} ({} items) has {} calories, costs {}"
    name = ntuple.name
    price = ntuple.price
    amount = ntuple.amount
    calories = ntuple.calories
    print(format_str.format(name, amount, calories, price))
```


