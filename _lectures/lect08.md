---
num: Lec 8
lecture_date: 2020-01-29
desc:
ready: true
pdfurl:
---

```python
  # Given a list, print out all elements of the list
  # that ar less than 5
  
  my_list = [8, 1, 1, 7]
  
  # go through every element
  # for each elemnt
  # check its value
  # if less than 5 print it 
  # if not less than 5, skip it
  # go to the next element
  num_el = len(my_list)
  print("There are", num_el, "in the list")
  i = 0
  while i < num_el: # stop when at the end of the list
    # print("Index", i)
    # WHILE BLOCK
    # get each element
    print("Index", i, "->", my_list[i])
    # check its value
    if my_list[i] < 5: # if less than 5 print it 
      print("Found", my_list[i])
    # else: 
    # go to the next element
    i = i + 1 # i += 1
  ```
  
  * highlight whole region you want to comment and go to 'FORMAT'--> 'COMMENT OUT REGION'
  * another way to comment out chunks of code: use """ in the beginning and end
  
  ```python
    my_list = [3, 4, 5]
    num_el = len(my_list)
    print("There are", num_el, "in the list")
    
    i = 0
    while i < num_el : # stop when at the end of the list
      new_list = []
      print("Index", i, "->", my_list[i])
      if my_list[i] < 5:
        new_list.append(my_list[i])
      i += 1
    print(new_list)
  ```
  * OUTPUT: index out of range
  
  
  ```python
    my_list = [3, 4, 5]
    num_el = len(my_list)
    print("There are", num_el, "in the list")
    
    new_list = []
    i = 0
    while i < num_el : # stop when at the end of the list
      i += 1
      if my_list[i] < 5:
        new_list.append(my_list[i])
    print(new_list)
  ```
