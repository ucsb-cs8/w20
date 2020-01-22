---
num: Lec 5
lecture_date: 2020-01-20
desc:
ready: true
pdfurl:
---

* Truth Tables:
  * T and T -> T
  * T and F -> F
  * F and F -> F
  
  * T or T -> T
  * T or F -> T
  * F or F -> F
  
* What is the result of the comparison?
  ```python
  'nature' > 'nurture'
  ```
  * Answer: False because 'a' is less than 'u' since it comes first in the alphabet
  
  ```python
  'week' > 'weekend'
  ```
  * Answer: False
  
```python
raining = False
sunny == True
weekend = True

if raining == True:
  print("bring an umbrella")
elif sunny == True:
  print("remember your skateboard")
  if weekend == True:
    print("Let's go swimming")
  else
    print("Study outside")

print("Have a great day!")
```
Output: <br/>
  > "Wear sunscreen!"
  > "Let's go swimming"
  > "Have a great day!"
