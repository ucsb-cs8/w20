# 10/24 Lecture Note

## Pre-lecture
+ Exam 1 Q2.5
    ```python
    50**20**30 == (50**20)**30
    False
    ```

+ Exam 1 Q7
    ```python
    def print_string(text):
    print (text)

    def return_string(text):
    return (text)

    text1 = print_string("Hi")
    >>> Hi

    text2 = return_string("Bye")
    >>> 

    print (text1)
    >>> None

    print (text2)
    >>> Bye
    ```
## Lecture 08 Loops and Strings
+ ### "for" loop
    ```python
    num_letters = 0
    for pet in ["cat", "dog", "giraffe"]:
        for letter in pet:
            num_letters += 1
        print (pet, num_letters)
    
    >>> cat 3
    >>> dog 3
    >>> giraffe 7
    ```

    ```python
    word = input("Give me a word:")

    illegal_chars = "$&!?"
    #same as illegal_chars = ["$", "&", "!", "?"]

    for letter in word:
        for i in range(len(illegal_chars)):
            '''
            char = illegal_chars[i]
            if letter == char:
                print("Found", letter)
            '''
            if letter == illegal_chars:
                print("Found", letter)
    ``` 

    ```python
    word = input("Give me a word:")

    num_letters = len(word)
    i = 0
    while i < num_letters:
        print(word[i])
        i += 3
    ```

    ```python
    word = input("Give me a word:")
    step = input("Step size:")
    step = int(step)

    print ("Word", word)
    print ("Step size", step)

    num_letters = len(word)
    i = 0
    while -len(word)< i < num_letters:
        print(word[i])
        i += step
    ```
+ ### Interrupting loops
    + continue
    + break

