---
num: Lec 14
lecture_date: 2020-02-19
desc: Objects (Mutability), Nested Loops, String Formatting
ready: false
reading:
---

# Wednesday, February 19th Lecture

``` python
# Generate num(candidate primes)
for num in range(start, end, step)
  #check the divisors
  for div in range(2,num/2 + 1):
    if num % div is divisible
      print (         )
      break
    #save the prime number
```

Example of printing columns and rows:

``` python
mtable = [[2, 3, 11], [5, 78, 99], [5777, 9978, 99]]:
for row in mtable:
  for elt in row:
    print (elt, " ", end = "")
  print()
```
* ISSUE: not in columns because it is only separated by a space ==> not formatted correctly

# Questions

What is the difference between `break` and `continue`?
  * Continue: go to the top of the loop
  * Break: get out of the loop completely
  
=======


# Lecture 14 (Thursday)
# Review

* range
* while/for loops
* File i/o
* cryptography


Pseudocode for the prime number function (lab06)...

* Generate numbers between start and end

* use range() ??? to loop through every num from start to stop

* use another loop to generate divisors

* check if each num is prime by dividing num by all the divisors

```python
start = 2 # Example values
end = 8 # Example values
list_primes = []
for num in range(start, end):
    isPrime = True
    # use another loop to generate divisors
    for div in range(2, num//2 + 1):
        # check the divisors
        if num % div == 0:
            isPrime = False # will set isPrime to False once num is divisible by one of the divisors
            break # will exit inner for loop
        # if there are none, add the number to the list of primes
        if (isPrime==True): # Add a boolean flag to check that we only add the num to list if it is prime
            list_primes.append(num)
```           
* Q: What would happen if isPrime is initialized outside of the for loop???
    * A: isPrime will be set to False for the rest of both for loops since it will never be reset back to True

* Q: Why is the break used?
    * A: Once we know that a number is divisible by another number, we know that it is not prime, so there
    is no reson to check the rest of the divisors. Using the break allows us to break out of the inner for loop
    (but continue with the outer for loop)



## Mutability of objects

1. What is printed out after running the following code segment?

```python
pet = 'cat'
pet.replace("c","b")
print(pet)
```

* Q: Why do we not get an error because we intended to modify something immutable?
    * A: The replace is a function, and it is written in a way that it creates a NEW object rather than trying ot modify the original object. Since this new object is not set equal to a variable, it is not saved.


# LAB06 example
2. What is printed out after running the following code segment?

```python
tmp = [1,2,3]
myL = []
for i in range(4):
    myL.append(tmp)
myL[0][0] = 42

print(tmp)
```

* Q: If we do ```print(myL)```, why does it optput 42 each time? (like so: [[42,2,3],[42,2,3],[42,2,3]]  )
    * A: Even if you only change the first element of the list, since all the lists were initialized to be the same, all of the lists will be changed when the first list is changed. <br/>
    * How could we change this so that it only changes the value of the first one?

```python
myL = []
for i in range(4):
    tmp = [1,2,3]
    myL.append(tmp)
myL[0][0] = 42

print(tmp)
print(myL)

```
If we initialize tmp inside of the loop, a new tmp variable is created in each iteration of the for loop. That way, even though all of these lists look the same when they are initialized,
they are not actually the same, so mutating one at the end by doing ```myL[0][0] = 42``` will not change the values of the others.<br/>

We can visualize this by printing out the id of each list like so. In the first example, the ids are the same.


```python
myL = []
tmp = [1,2,3]
for i in range(4):
    myL.append(tmp)
    print(id(tmp))
myL[0][0] = 42

print(tmp)
print(myL)

```

Compare it with: 

```python
myL = []
for i in range(4):
    tmp = [1,2,3]
    myL.append(tmp)
    print(id(tmp))
myL[0][0] = 42

print(tmp)
print(myL)

```

3. What is printed out after running the following code segment?

```python
my_pets = ["bat", "cat"]
ur_pets = my_pets
ur_pets.append("owl")
print(my_pets)
```
Answer: [...]

4. What is printed out after running the following code segment?

```python
my_pets = ["bat", "cat"]
ur_pets = ["bat", "cat"]
ur_pets.append("owl")
print(my_pets)
```
Answer: [...]

# Formatting Output

```python
for num in range(0, 10):
    print("{0:10.3f}".format(num))
```
