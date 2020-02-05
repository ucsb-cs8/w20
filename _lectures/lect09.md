---
num: Lec 9
lecture_date: 2020-02-03
desc:
ready: true
pdfurl:
---



# HW05 and HW06
- Both due Sat 2/8 at 11AM
- https://ucsb-cs8.github.io/w20/work_list/Syllabus has a link to the book in the library reserve
- Read the book before the lab
- Practice the concepts: don’t just try to solve the specific problem

# Survey
- Thank you for the survey!
- I wish the professor would check email more often
    - Professor is more active on piazza
- I am not able to make any open lab hours or ninja skills sessions
    - Adding more time slots to office hours
- I wish we could get more into code structure 
    - Walk through a specific example
- Survey is not closed yet!
- Anonymous link on syllabus to submit feedback

# What we will be reviewing today:
+ Creating Functions
+ Using Strings
+ Getting User Input
+ `while` loops
+ `pytest`
+ `random` module

# `pytest` function skeleton:
```{r}
def test_function_XXX():
    assert functino(X) == return_value
    
def test_function_YYY():
	assert_function(Y) == return_value
```
- Here we are defining a new function
- We will always start with `test_`
- Usually testing our function with multiple inputs
- Have to differentiate our `pytest` function from one version to another
    - This is why we define two different functions (XXX and YYY)
- Floating point values do not behave as ecpected when we check equality (`==`)
    - This is why we use the `approx()` function
        - Sets a certain degree of precision
        - If the answer on the left matches the answer on the right within that degree of precision python will say these two values are equal
        - This is the **only** time we use the `approx()` function ie. wouldn’t make sense for a string

# "Helper" functions
- As soon as you are copy and pasting your code and changing only one value, this should be your sign that you need a function!
- The one value you are changing when you copy and paste is the **input parameter** in your function
- Advantages:
    + Your code will be shorter
    + When debugging, you only need to fix your **one** error rather than scrolling and fixing your error everywhere you pasted it
    
# `random` module
```{r}
print (“Random”, random.randint(25, 50))
```
- 25 is the starting point, 50 is the ending point
    - This is an inclusive range
- From the lab: `seed` is an initial value that gets plugged into the formula and predicts every number that comes after it


```python
import random
print("Random", random.randint(1, 10))
```

    'Random' 7



```python
print("Random", random.randint(1, 10))
```

    'Random' 7



```python
print("Random", random.randint(1, 10))
```

    'Random' 1


The number really is random! We get a different output everytime.


```python
the_num = random.randint(1,10)
print("Computer selected ", the_num) # Verify that the computer is giving us the ouput we expect.
guess = input("Select a number between 0 and 10: ") # Asking the user for a number.
print("You selected: ", guess) # Printing the input back to the user
```

    'Computer selected ' 6
    Select a number between 0 and 10: 7
    'You selected: ' 7


What might be a potential problem?
- The input the user gives could be a string or an integer.
- We are asking the user to give a guess within a range that we are not using.
- We are using **hard coded variables**; we should try to use variables

How do we do this? define two variables `r start_num` and `r end_num`


```python
start_num = 1
end_num = 10
the_num = random.randint(start_num, end_num)
print("Computer selected ", the_num)

prompt = "Select a number between " + str(start_num)
prompt += " and " + str(end_num)
'''
Here we take start_num and end_num and concatenate them into the string, but we have to
convert the number into a string first so python doesn't give us a TypeError!
We use += to add the updated value of prompt to end_num 
''' 

guess = input(prompt)
print("You selected: ", guess)
```

    'Computer selected ' 9
    Select a number between 1 and 102
    'You selected: ' 2


Now we will try to convert the computer's ouput into a string so it matches the type of the user input.

Check Monday's lecture notes to see code for converting the user's input into an int so it matches the computer's output.

### Pseudo code:
- Convert the_num into str
- While the user did not guess correctly
- Check if the user's guess is the same as the_num
    - If True (they are the same) 
        - Print "You got it!"
    - Else
        - Ask the user for another guess


```python
the_num = str(the_num) # Overwriting the old value of the_num
guess = None
'''
Notice that we have to create this variable before the while loop begins so it 
exists when the function ends.
'''

while guess != the_num:
    guess = input(prompt) 
    print ("You selected: ", guess)
    
    if guess == the_num:
        print ("You got it!")
        break
    '''
    Don't need to include an else because if guess does not equal the_num, 
    we will loop through the while loop again
    
    Break will get us out of the while loop, don't want to check equality again
    '''
print ("The End")
    
```

    Select a number between 1 and 109
    'You selected: ' 9
    Select a number between 1 and 104
    'You selected: ' 4
    Select a number between 1 and 107
    'You selected: ' 7
    Select a number between 1 and 103
    'You selected: ' 3


```python
i = 0
break_num = 8

print("Break in action")
print("Stop after", break_num)

while i <11:
    if i == break_num:
        break
    print(i)
    i += 1

print("Continue in action")
i = 0
divisible_by = 3

while i < 10:
    if i % divisible_by == 0: #Checks if i is divisible by our variable, divisible_by, by checking if the remainder is 0
        print (i, " is divisible by ", divisible_by)
        i += 1 # Without this line, we would get stuck in an infinite loop
        continue
    print(i) # Notice there is an implicit else here
    i += 1

print ("Done")
```

    Break in action
    'Stop after' 8
    0
    1
    2
    3
    4
    5
    6
    7
    Continue in action
    0, ' is divisible by ' 3
    1
    2
    3 ' is divisible by ' 3
    4
    5
    6 ' is divisible by ' 3
    7
    8
    9 ' is divisible by ' 3
    Done



```python
print("Pass in action")
i = 0
divisible_by = 3

while i < 10:
    if i % divisible_by == 0: #Checks if i is divisible by our variable, divisible_by, by checking if the remainder is 0
        print (i, " is divisible by ", divisible_by)
        i += 1 # Without this line, we would get stuck in an infinite loop
        pass
    print(i) # Notice there is an implicit else here
    i += 1

print ("Done")
```

    Pass in action
    0 ' is divisible by ' 3
    1
    2
    3 ' is divisible by ' 3
    4
    5
    6 ' is divisible by ' 3
    7
    8
    9 ' is divisible by ' 3
    10
    Done


When you see a `pass`, this is usually an indicator that something is not yet inplemented, or you can rewrite your code without using the `pass`.

We have now seen `pass`, `continue`, and `break` in action. These allow us to redirect the flow.

Let's now try asking the user if they want to keep going after the function ends.


```python
answer = 'y' # The user's input won't be a number anymore, now it will be a yes or no

while guess != the_num:
    guess = input(prompt) 
    print ("You selected: ", guess)
    
    if guess == the_num:
        print ("You got it!")
        answer = input("Do you want to continue? ")
        if answer == 'y':
            the_num = str(random.radnint(start_num, end_num))
print ("The End")
```

    Select a number between 1 and 103
    'You selected: ' 3
    Select a number between 1 and 106
    'You selected: ' 6
    Select a number between 1 and 109
    'You selected: ' 9
    Select a number between 1 and 103
    'You selected: ' 3




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
