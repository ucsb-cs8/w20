# 11/12 Lecture Note

## Lecture 13 String Formatting 
+ ### pre-lecture
    + iclicker question (string is immutable)
        ```python
        MS = "Mississippi"
        MS.replace("i", "!")
        print(MS)
        "Mississippi" # string is immutable

        MS = MS.replace("i", "!") # assign a new string will overwrite the former one
        print(MS)
        "M!ss!ss!pp!"
        ```
    + be careful of list (it's mutable!!!)
        ```python 
        my_list = ['var1', 'var2', 'var3']
        for i in my_list:
            my_list.remove(i)
        print(my_list)
        ['var2'] 
        # since when i = 'var1', it automatically remove 'var1', and 'var2' take position 0. When it moves on to next item, 'var3' has the index of 1 and therefore dropped.
        ```
+ ### string formatting
    + syntax 
    ```python
    "{ : }".format()
    # left side of colon is index
    # right side is formatted length
    ```
    + difference between numbers and strings
    ```python
    price = 18.1
    print("==={}===".format(price))
    '===18.1==='
    print("==={:8}===".format(price))
    '===    18.1==='
    print("==={:8}===".format("1"))
    '===1       ==='
    print("==={:8}===".format(True) # here True has a boolean value of 1 which is considered as an integer
    '===       1==='
    '''
    In conclusion, int, float and boolean value is right justified, whereas string is left justified
    '''
    ```
    + center / left / right
    ```python
    # total length is 5
    {:<5} # left justified
    {:^5} # centered
    {:>5} # right justified
    ```
    + using string operation to set length

    ```python 
    num_s = 5
    print("~~~{:" + str(num_s) + "}~~~".format(123))
    '~~~  123~~~'
    print("~~~{:" + str(num_s) + "}~~~".format("123"))
    '~~~123  ~~~'
    # note the difference between number and string
    ```
    + float formatting
    ```python
    price = 12345.6
    print("==={}===").format(price))
    '===12345.6==='
    print("==={:10.2f}===").format(price))
    '===12345.60  ===' # 12345.60
    print("==={:10.5f}===".format(price))
    '===12345.60000===' # 12345.60000 (5 decimal spaces)
    print("==={:3.2f}===".format(price)) 
    '===12345.60===' # overflows allocated space
+ ### random
    ```python
    from random import * # import all 
    random() # generate a float number between 0 and 1
    # use int(random()*50) to generate an integer between 0 and 50
    randrange(a, b)
    randrange(50, 100) # generate a number between 50 and 100
    ```
    + roll a dice
    ```python

    def print_counts(counts):
        for i in range(1,7):
            print(i, ":", "*" * counts[i])

    from random import randrange
    
    rolls = []
    counts = [0, 0, 0, 0, 0, 0, 0]
    for roll in range(10):
        die_roll = randrange(1,7)
        rolls.append(die_roll) # list is mutable, therefore we don't need to assign it
        counts[die_roll] += 1 # counter
    print (rolls)
    print (counts)

    print_counts(counts) # call the function to return the distribution
    ```
