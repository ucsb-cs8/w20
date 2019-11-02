# Lecture 10: Cryptography Hints and Mutable vs. Immutable

Codemakers and codebreakers back in the day didn't have to learn Python (despite their job title), but it probably would've made their lives much easier if they did. Or maybe it would've done the opposite. Eh, depends on how you look at it.

Oh, right, cryptography! Here's more on `range()` and control flow nesting so that you too can live out your childhood dreams of slow-motion dives and personal theme songs.*

\**Disclaimer: Slow-motion dives and personal theme songs not included.*

# Function function, what's your function?

Hooking up variables and keywords and statements! Let's make a function.

```python
def print_range(num):
```

The **`def`** keyword tells Python to, well, *def*ine a function, so always include this. After `def` is `print_range`, which is the name you want to give your function.

Then there's a set of parentheses and that `num` thing. `num` is a variable, but if you really want to be specific, you would say that this variable is a **parameter** because it's inside of a function. Putting a ~~variable~~ parameter in like this allows you to use `num` inside your function and do cool things with it.

It's important to note that `num`, here, is just a placeholder for when you give it a value later in the program with a **function call**, like `print_range(42)`. You could call `num` anything else, like `mac_and_cheese` or `absurdly_long_parameter_that_no_one_should_have_to_read` or good old `x`, but we'll stick with `num` because it's short and sweet and descriptive all the same. As long as you spell `num` as `num` when you use it inside of your function, all will be fine.

(If you don't want or need a parameter for your function, you would just define the function without one, like `def print_range()`. Note that you'd still keep the parentheses, though.)

Oh, and don't forget the colon at the end. A function definition isn't complete without a colon. It'd be a little like if a spy didn't have at least one trench coat in their closet, in which case it would, without question, completely and utterly invalidate their life's work. You heard it here first.

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
