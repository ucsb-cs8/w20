# Lecture 10: Cryptography Hints and Mutable vs. Immutable

Remember `range()`? And control flow nesting? There's more!

# String iteration using `range()`

```python
def print_range(num): # num is just a placeholder
    for i in range(num):
        if i < 3:
            print(i)
        else:
            if i < 5:
                continue # Begins a new for loop iteration (goes back to beginning)
            else:
                return i

print_range(9)
```

# Crash course on binary

# More cryptography

Goal: Loop back to beginning of string in case of index overflow.

# Mutable vs. immutable

Everything in Python is an object.

```python
my_bat = "bat"
my_cat = "cat"
```

When creating a variable, you are creating an object and putting a label on it. A variable that has the same value as another value is simply a different reference to the same object.

```python
ur_bat = "bat" # New label, same object.
```

Strings are immutable, while lists are mutable.

**`id()`:** Gives the identity of an object using its memory address. Useful for finding variables that reference the same object, since this ID must be unique. (Try `help(id)` on the Python shell.)

Because strings are immutable, they don't change no matter what you do to them short of replacing the string entirely.

```python
my_cat = "cat"
my_bat = "bat"
your_bat = "bat"

list = ["cat", "bat"]

def swap_pets(pet1, pet2):
    print("From swap: ", pet1, pet2)
    tmp = pet1
    pet1 = pet2
    pet2 = tmp
    print("From swap: ", pet1, pet2)
    return pet2
    # pet1 and pet2 only exist within this function. Once this function stops executing, pet1 and pet2 disappear; trying to call one of them outside of the function results in an error.

print("Before the swap: ", my_cat, my_bat)
pet = swap_pets(my_cat, my_bat)
print("After the swap: ", my_cat, my_bat)
print(pet)
```

Because lists are mutable, be careful about changing them in functions and requiring the original version.

```python
my_cat = "cat"
my_bat = "bat"
your_bat = "bat"

list = ["cat", "bat"]

def swap_pets_list(a_list): # Need to always double check that there are the proper number of items in a list.
    print("From swap: ", a_list[0], a_list[1])
    tmp = a_list[1]
    a_list[0] = a_list[1]
    a_list[0] = tmp
    print("From swap: ", a_list[0], a_list[1])
    return a_list

print("Before the swap: ", list[0], list[1])
pet = swap_pets_list(list)
print("After the swap: ", list[0], list[1])
print(pet)
```
