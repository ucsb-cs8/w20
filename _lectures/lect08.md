---
num: Lec 8
lecture_date: 2020-01-29
desc:
ready: true
pdfurl:
---
# Tuesday, January 28th Lecture
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
____________________________________________________________________________________________________________________________
# Thursday, January 30th Lecture
  
 ## Announcements
* If you are struggling a lot, try to get help ASAP. It’s going to get more difficult from here

* Q: How do I contact prof k on piazza?
  * A: If you click “instructors”, it will be visible to all the instructors and only the instructors. 


## In-class participation quiz

* Hopefully for questions that you didn’t know how to write in Python, you still wrote a pseudocode

### 0) 
```python
x_var = 2 #integer
```

### 1)

```python

name = input(“name:”)
age = input(“age:”)
age = int(age)
print( ‘Hello, ‘, name ,“! ” , “Twice your age is “ , age*2, sep = ‘’)

```

Or

```python

name = input("name:")
age = input("age:")
age = int(age)
print( "Hello, " + name + "!" +  "Twice your age is " + str(age*2))
#  Note: if you use the + operators, you must convert your age back into a string!!!
```


Q: What if the person types their age as a string?<br/>
A: An error will occur.

Q: Could I use an eval function (if they entered “18” as a string)?<br/>
A: Yes, but eval can be dangerous.


### 2)
```python
if N % 2 == 0:
	print(“Even”)
else:
	print(“Odd”)

```

Or 

```python
if N % 2 != 0:
	print("Odd")
else:
	print("Even")

```


* General Note: after a conditional statement, there must be a colon. In the following lines, anything indented is within that conditional statement.


### 3)

Think through the pseudocode. Start with a function name. What does the function take in as a parameter?
Next: 

```python
def less_than5(lst):
	# go thru. all elements of lst
	# get the element
	# check if <5
	# if < 5, print(element)
	# do I need an else statement? No. B/c if it doesn’t satisfy the if, it will continue to loop through

```
```python
my_nums = [1,1,2,3,5,8,13,21,34,55,98]
def less_than5(lst):
    '''
    Given a list, print out all of the elements that are less than 5.
    TODO: Return the list with those elements.
    '''
    i = 0 # is a conventional variable used for indexing
    while ( i < len(lst)):# go thru. all elements of lst. Stop after last element
        elt = lst[i]
        if elt < 5:
            print( "found", elt)
        # print("Index",i, "is", elt) # this will show the index position for each iteration
        i += 1 # Note: you must have the increment after you use the indexing
    
```

another way to do this is using ```pass```
Generally, it is best to format your code in a way that you never need to use ```pass```, but this is an example of how it works: 
```python
def less_than5(lst):
    elt = lst[i]
    if lst[i] >= 5:# check if element is >=5. Ignore if >=5
        pass # used when a block of code is not supposed to do anything
    else:
        print( "found", elt)
    i += 1
```
* We will be working with while loops for a while so that we can understand how it and the for loops work.


* Q: How to print out the sum of all the (number) elements in a list?
  * sum([1,2,3,4])
  * For the lab (lab02), do not use the sum function.


Q: Is pass the same thing as return?<br/>
A: No. The return exits out of the function. The pass just exits out of that one block and continues to the rest of the code.
