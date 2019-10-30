---
assigned: 2019-10-30
desc: Encryption and Decryption
due: 2019-11-06 08:59
layout: lab
num: lab04
ready: true
---

In this lab you'll learn to:

* Deconstruct the essential cryptographic processes of encryption and decryption
* Create encryption and decryption algorithms that use a secret key
* Write "helper" functions that are called by other functions
* Use built-in string methods
* Convert an integer to a binary representation
* Decode a message from your instructor :-)


# Step 1: Log on and bring up a terminal window

# Step 2: Create a directory in your cs8 directory named {{page.num}}.

(Remember the commands `cd`, `ls`, and `mkdir`)

# Step 3: Start IDLE

The terminal command for this is `idle3`.  When you have the IDLE window up, you are ready for some programming!

# Step 4: What to program?

First, some important background on cryptography.

Encryption is a procedure that is used to transform a message (referred to as plaintext) in order to prevent anyone except the intended recipient from reading that data. The output of the process is called ciphertext, and it should be unintelligible without knowledge of the key and decryption algorithm.

Decryption is the reverse procedure: the process of making the encrypted data readable.

A Caesar cipher is one of the simplest and most widely known encryption algorithms. In this algorithm, each letter of the plaintext is replaced by a letter some fixed number of positions later in the alphabet. For example, with a shift number of 4, A would be replaced by E, B would become F, and so on. Later in this step, you will figure out how to write a decryption algorithm for the Caesar cipher.

Note that for this algorithm to work, the letters of the alphabet (and any other characters that should be allowed in the plaintext), as well as their order, **must be fixed and should be the same** for both encryption and decryption. For example, if you encrypt with the 26 letter English alphabet and decrypt with the 27 letter Spanish alphabet (including ñ), you won't get the correct decrypted plaintext back.

Functions to Implement:

1. `createAlphabet()` - return alphabet
2. `encryptCaesarCipher(plainText, key)` - return cipherText
3. `decryptCaesarCipher(cipherText, key)` - return plainText

Function Details:

1. `createAlphabet()` - return alphabet. Write a function that returns a string of all the characters that you want to include in your encryption algorithm.  We will call this string alphabet and it should include all the lower case letters, followed by all the uppercase letters, then a space, a comma, a period, a hyphen ('-'), a tilde ('\~'), and a pound symbol ('#'). There should be no spacing between the symbols in the alphabet; the only exception being the single space you are asked to add after the uppercase letters. Ensure that your alphabet is correct before proceding to prevent unexpected results.

Typing letters manually is tedious and error-prone, so you shouldn't do it. Instead, use the module `ascii_lowercase` imported from the `string` library to construct the alphabet string.

2. `encryptCaesarCipher(plainText, key)` - return cipherText.  Now write a function to perform encryption using the Caesar cipher. The first few lines of this function need to create your alphabet using the helper function `createAlphabet()` you created.

    Then you will have to use a `for` loop to go through the characters of your `plaintext` and for each character you will have to choose the character from the alphabet that is `key` positions forward in the alphabet. Be very careful for the cases where you will have to cycle around the ends of the alphabet. 
    Be mindful of the values of `key`. Consider the cases where the value of `key` is unreasonable. In such cases the function should return the string: "Invalid key".
    Do not hard-code the length of the alphabet as a fixed number in your code - we might be testing your code with the alphabets of different lengths.


3. `decryptCaesarCipher(plainText, key)` - return cipherText. Finally, write a function that decrypts the Caesar Cipher. Think: what process would you follow if you were doing the decryption by hand?


4. Test your functions by encrypting any string, and then decrypting the result to verify that you can recover the original input string. Try interesting test cases: short strings, long strings, strings with odd characters, large key values, creative key choices, etc.

    Note: what happens if you first "decrypt" some plaintext, and then "encrypt" it? Why does this happen?

# Step 5: Binary Key

In this step we'll introduce a variation to the Caesar cipher, resulting in a new cipher called the CS8 Cipher. Now, the offset defined by the key will still be constant, but sometimes the shift will be a _forward_ shift and other times it will be a _backward_ shift. Whether it is forward or backward will be dictated by the binary representation of the key, which we will call the binary key. For example, a value of 2 is represented in binary as `10`, i.e., two bits containing 1 followed by 0.
At each step of the encryption, the algorithm will look at the next bit of the binary key. If it is `1`, the shift will be **forward**, and if it is `0`, the shift will be **backward**.

Here are the new functions you will need to implement:

1. `createBinKeyFromKey(key)` - return binKey. Write a function that converts your key (which is an integer) to binary format (as a string of 0's and 1's). The built-in Python function `bin` takes an integer parameter and converts it to a binary string starting with `0b` followed by the binary conversion. For example, `bin(9)` returns '0b1001'. Can you find a way to slice off the first two characters? (Hint: remember the slicing operator `:`.)

2. `encryptCS8Cipher(plainText, key)` - return cipherText.  Now write a function that uses the same idea as the Caesar Cipher but instead of using the key by itself to find the character in the alphabet that will replace the current character, it will also use the binKey. The first few lines of this function need to:

    - create your alphabet
    - create binKey

    To do these you will call the helper functions you created earlier. Then you will have to use a `for` loop to go through the characters of your plaintext and for each character you will have to perform the following procedure: 
    * Pick the next character of the binKey (if the length of the binKey is smaller than the length of the plainText, then you have to cycle back around from the beginning of binKey). 
    * If the character in binKey is ‘1’ then you will have to choose the character from the alphabet that is `key` positions **forward** in the alphabet. If the character in binKey is ‘0’ then you will have to choose the character from the alphabet that is `key` positions **backward** in the alphabet.

    Here is a visualization of the encryption process:

    ![cipher visualization](cipher.gif)

3. `decryptCS8Cipher(plainText, key)` - return cipherText. Finally, write a function that will decrypt our CS8 Cipher. The procedure should be straightforward if you completed the previous part of the lab. Try to work out the solutions by hand first, if stuck. 

4. Decode this message from your instructor using key = `513`:

    `#vyxACdjwk#pAjErCHdRWdCqrBdlxddnwCdrBdsljCdqnAndCfRvjtndCqnRZryqnACnGkRuxxtduxw-,AdjwmdlxfcnA`

# Step 6: Saving your files

Save your functions in a Python file named `{{page.num}}.py` in your directory **{{page.num}}**.

# Step 7: Submit your work to Gradescope

Congratulations, you are finished with this lab!  

_Acknowledgments: Thanks to Ana Nika and Matthew Buoni for the initial version of this lab, and to Noah Stier and Jose Cuellar for adapting it for this assignment._
