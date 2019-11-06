# 11/05 Lecture Note

## Lecture 11 File Input/Output Dictionaries
+ ### list commands (review)
    ```python
    list.sort()
    list.reverse()
    ```

+ ### dictionaries
    ```python
    '''
    General form (syntax):
    {<key1>: <value1>, <key2>: <value2>}
    '''
    fruit_dict = {'apple': 18, 'orange': 19, 'banana': 20}
    print(fruit_dict)

    {'apple': 18, 'orange': 19, 'banana': 20}
    
    print("You got", fruit_dict['apple'], "apples!")
    You got 18 apples!

    for fruit in fruit_dict:
        print("You got", fruit_dict[fruit], fruit)

    fruit_dict.pop('banana')
    fruit_dict -> {'apple': 18, 'orange': 19}

    my_fruit = {'apple': 5, 'kiwi': 3}
    fruit_dict.update(my_fruit)
    fruit_dict -> {'apple': 5, 'orange': 19, 'kiwi': 3}

    fruit_dict.get('banana') # banana is not in the dictionary
    fruit_dict.get('banana') == None
    True

    fruit_dict.keys() #return all the keys
    fruit_dict.values() #return all the values
    fruit_dict.items() #return a list with tuples of key and corresponding value 
    ```
+ ### file basics
    + read file
    ```python
    infile = open("123.txt")

    major_dict = {}

    for line in infile:
        print(line)
        mline = line.strip("\n").split('\t'))
        major_dict[mline[0]] = mline[1]
    ```
    + common commands
    ```python
    read() #reads the entire file
    read(n) #reads the next n characters from the input(better for large file)
    readline() #reads everything from the current position to the next '\n'
    readlines() #reads all the lines in the file and returns a list
    ```
