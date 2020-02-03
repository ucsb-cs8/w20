---
num: Lec 9
lecture_date: 2020-02-03
desc:
ready: true
pdfurl:
---

* Random module:

```python
import random
print ("Random", random.randint(25,50))
```


```python
# print ("Random", random.randint(25,50))
first_num = 1
last_num = 10
the_num = random.randint(first_num, last_num)

prompt = "Select a num between " + str(first_num)
###print(prompt)
#prompt = prompt + " and " + str(last_num)
prompt += " and " + str(last_num) + ": "
###print(prompt)

while guess != the _num:
  guess = input(prompt)
  guess = int(guess)
  # check if user's guess is the_num
  if guess == the_num:
    print("Yes!! Winner!!")
  else:
    print("Guess again")
print("The End")
```
