---
assigned: 2019-10-23
desc: encryption and decryption
due: 2019-10-30 08:59
layout: lab
num: lab04
ready: false
---

In this lab you'll learn to:

* Understand the essential cryptographic processes of encryption and decryption
* Create encryption and decryption algorithms that use a secret key
* Write "helper" functions that are called by other functions
* Use built-in string methods
* Convert an integer to a binary representation
* Decode a message from your instructor :-)

![Blowfish](blowfish.jpg)

"Yes, the file is encrypted with the Blowfish algorithm....I'll have to hack it.  Give me five minutes."

# Step 0:  Partner with another student at the beginning of this lab.

 If you do not have a partner, your TAs can pair you up with another student. You will switch back and forth between the roles of Driver and Navigator. Again, the TAs can help you synchronize this.

# Step 1: Log on and bring up a terminal window

# Step 2: Create a directory in your cs8 directory named lab04.

(Remember the commands `cd`, `ls`, and `mkdir`)

# Step 3: Start IDLE

The terminal command for this is `idle3`.  When you have the IDLE window up, you are ready for some programming!

# Step 4: What to program?

First, some important background on cryptography.

Encryption is a procedure that is used to transform a message (referred to as plaintext) in order to prevent anyone except the intended recipient from reading that data. The output of the process is called ciphertext, and it should be unintelligible without knowledge of the key and decryption algorithm.

Decryption is the reverse procedure: the process of making the encrypted data readable.

A Caesar cipher is one of the simplest and most widely known encryption algorithms. In this algorithm, each letter of the plaintext is replaced by a letter some fixed number of positions later in the alphabet. For example, with a shift number of 4, A would be replaced by E, B would become F, and so on. Later in this step, you will figure out how to write a decryption algorithm for the Caesar cipher.

Functions to Implement:

1. `createAlphabet()` - return alphabet
2. `createBinKeyFromKey(key)` - return binKey
3. `encryptCS8Cipher(plainText, key)` - return cipherText
4. `decryptCS8Cipher(cipherText, key)` - return plainText

Function Details:

1. `createAlphabet()` - return alphabet. Write a function that returns a string of all the characters that you want to include in your encryption algorithm.  We will call this string alphabet and it should include all the lower case letters and upper case letters, space, comma, period, hyphen, tilde, etc.  Can you think of a way to form your alphabet without manually typing each character?  Your function should be of the form `createAlphabet()` and should return a string alphabet.

    Hint: Numerical values (ord) between and including 32 and 126 seem to include all of the characters contained in most text.

2. `createBinKeyFromKey(key)` - return binKey. Write a function that converts your key (which is an integer) to binary format (as a string of 0's and 1's). The built-in Python function `bin` takes an integer parameter and converts to a binary string starting with 0b followed by the binary conversion. For example, bin(9) returns '0b1001'. Can you think of a way to slice off the first two characters?

3. `encryptCS8Cipher(plainText, key)` - return cipherText.  Now write a function that uses the same idea as the Caesar Cipher but instead of using the key by itself to find the character in the alphabet that will replace the current character, it will also use the binKey. The first few lines of this function need to:

    - create your alphabet
    - create binKey

    To do these you will call the helper functions you created in steps 1-2.
Then you will have to use a for loop to go through the characters of your plaintext and for each character you will have to perform the following procedure. Pick the next character of the binKey (if the length of the binKey is smaller than the length of the plainText, then you have to cycle back around from the beginning). If the character in binKey is ‘0’ then you will have to choose the character from the alphabet that is key positions forward in the alphabet. If the character in binKey is ‘1’ then you will have to choose the character from the alphabet that is key position backward in the alphabet. Be careful for the cases that you will have to cycle around the alphabet.

    We have the following example: `{Alphabet: 'abcdefghijklmnopqrstuvwxyz', plainText: 'always', key: 4, binKey (repeated): '100100', cipherText: 'wpawcw'}`.

4. `decryptCS8Cipher(plainText, key)` - return cipherText. Finally, write a function that decrypts the CS8 Cipher. This might take some thought!


5. Test your functions by encrypting any string, and then decrypting the result to verify that you can recover the original input string. Try interesting test cases: short strings, long strings, strings with odd characters, creative key choices, etc.

    Note: what happens if you first "decrypt" some plaintext, and then "encrypt" it? Why does this happen?

6. Decode this message from your instructor, using key = `513`:

    ```|65.9(;<3;N065:GF 6OY(9,F>,33YI5F@6<9F>;SF;6F),\*6GC5.F(F/(\*E?9FaSO```

# Step 5: Saving your files

Save your functions in a Python file named lab04.py in your directory lab04.

# Step 6: Submit your work via Gauchospace

Each individual must turn in their own assignment, even if you worked in pairs.  In addition to lab04.py, you also need to include a file called pairPartners.txt.  This file should contain two lines: your name and your Pair Programming partner's name exactly as they appear on Gauchospace.
