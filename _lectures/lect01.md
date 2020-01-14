---
num: Lec 1
lecture_date: 2020-01-06
desc: Getting Started
ready: true
pdfurl:
---

* Introductions

* Course Structure and Policies

* All slides will be posted on the course website under "[Lectures](<https://ucsb-cs8.github.io/w20/lec_list/>)" -> "Link to Lecture Slides" 
* Algorithm and pseudocode

* Running Python in IDLE
```python
print("Hello, World!")
```

* Breaking the code to see the errors
  * Notice that IDLE has helpful color-coding and highlighting to help you
  * Remove the last parenthesis `)`
    * Error in IDLE: unexpected EOF while parsing
  * Remove the last double quote `"`
    * the rest of the text after the removed quote turns green
    * Error in IDLE: unexpected EOL while parsing
  * Misspell `print` as `prnit`
    * `print` was previously displayed in purple (to indicate that Python knew that it a special keyword), `prnit` is now shown in black
    * Error in the Python Shell: `NameError: name 'prnit' is not defined`
