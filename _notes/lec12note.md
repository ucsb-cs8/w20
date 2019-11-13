# 11/07 Lecture Note

## Lecture 12 
+ ### list commands
    ```python
    a = []
    a += "hello" #here += acts like a for loop function which tears down the string into single chars and append them to the list a

    word = list("word")
    word.remove("d")
    word = ["w", "o", "r"]
    ```
+ ### string commands
    ```python
    word = "abcdefg"
    word.replace("a", "z") #replace a with z
    "zbcdefg"

    word.replace("a", "") #replace a with empty string = remove a
    ```

+ ### write into a file
    ```python
    infile = open(filename, 'r')
    outfile = open("output"+filename, 'a') # 'a' here means that we are gonna append our edit text to the former text
    file_list = infile.readlines()

    for line in file_list:
        outfile.write(line) #write new lines into the file we just created to output

    ```
+ ### format print
    ```python
    >>> "{:6}".format(42)
    "    42"
    >>> "{}:{}:{}".format(18,7,6)
    "18:7:6"
    >>> "{2}:{1}:{0}".format(18,7,6) #index
    "6:7:18"

    {a:b} # a is the index of output; b is the total length for the string output
    ```
