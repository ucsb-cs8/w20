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

