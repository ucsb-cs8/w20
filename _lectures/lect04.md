---
num: Lec 4
lecture_date: 2020-01-15
desc:
ready: true
pdfurl:
---

* Tuesday 1/21 11AM: *OPTIONAL* review/overview session to prep for Exam 1

* Docstring vs. Comments
  * Docstring: appear once directly under the function header
  * Comments: appear anywhere in the file

* Parameters: can have no parameters or one or multiple parameters

* Return vs. Print
  * Return: caller receives the treturned value
  * Print: caller receives the None value, only the value is printed and displayed

* User Input:
  * use an input() function
  
* **Examples**
  ```python
  num = input("What is your favorite number?")
  print("You entered", num) # "Echo" the input
  print("Mine", num*2)
  ```
  Output: <br/>
  > What is your favorite number? 8 <br/>
  > You entered 8 <br/>
  > Mine is 88
  
  
  ```python
  num = input("What is your favorite number?")
  print("You entered", num)
  my_num = 2*int(num)
  print("Mine", my_num*2)
  ```
  Output: <br/>
  > What is your favorite number? 8 <br/>
  > You entered 8 <br/>
  > Mine is 16
  
* Strings
  * a string is a sequence of characters(letters, numbers, symbols)
  * How do we represent: `She said: "Pay attention!"` as a string?
    * `"She said: "Pay attention!""`
    
* Printing Strings
  * Arguments inside the `print()` statement, by default, are separated by *spaces*.
  
* \n : new line
* \ : something special will be done right after the backlash

* New Line
  ```python
  print("Hello \n world")
  ```
  Output: <br/>
  > Hello <br/>
  > world

* **Print Examples**
  ```python
  print("\"Hello, world\"")
  ```
  Output: <br/>
  > "Hello, world" 
  
  ```python
  print('\"\"Hello?\" - said Mrs. O\'Brien\"')
  ```
  Ouput: <br/>
  > ""Hello?" - said Mrs. O'Brien"
  
