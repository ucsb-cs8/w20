# 10/29 Lecture Note

## Lecture 09 String Processing and Cryptography
+ ### string 
    + indexing
    ```python
    s = Halloween
       #012345678  positive index
       #        -1 negative index
    ```
    + iteration (using range()) 
    ```python
    s = Halloween 
    # index
    for i in range(len(s)):
        print (i)
    
    # letter
    for c in s:
        print (c)

    # use string index
    for i in range(len(s)):
        print (s[i]) #print each letter of s

    # iclicker question
    # How to print a string backwards?
    for i in range("???"):
        print (s[i])

    Answer: "???" = (-1, -len(s)-1, -1)
    # start from the last one, to the first one

    start = 2
    end = 9 #the loop will never reach the end (i + step < end)
    step = 3

    for i in range(start, end, step):
        print (i)
    ```

+ ### module

+ ### other useful functions for string: 
    + find ()
    ```python
    str.find(item) #return the index of the first occurence if valid, or return -1 if item is not in str
    str.rfind(item) #return the index of the last occurence
    ```
    + count ()
    ```python
    str.count(item) #count how many times item occurs
    ```

+ ### cryptography
    + plaintext -> encryption -> ciphertext
    + ciphertext -> decryption -> plaintext

    ```python
    # declare all strings
    message = "hello world"
    encrypted = ""
    decrypted = ""
    # generate an alphabet with space
    from string import ascii_lowercase

    alphabet = ascii_lowercase + " " 
    print ('"' + alphabet + '"')

    # generate the key
    key = alphabet[::-1]

    # loop through every letter of message
    # find a letter from the key to replace it with 
    # assign a new letter to an encrypted message

    for letter in message:
        idx = alphabet.find(letter)
        encrypted += key[idx]
    print(encrypted)

    # look through every letter of the encrypted 
    for letter in encrypted:
        idx = key.find(letter)
        decrypted += alphabet[idx]
    print(decrypted)
    ```
