---
num: Lec 6
lecture_date: 2020-01-22
desc:
ready: false
pdfurl:
---

# Thursday Lecture 06 Notes

## Announcements:
* Pay attention to minor details! They matter a lot. 
* The review is tomorrow (Fri, Jan 24) at 1:30pm in **HFH 1132**. If any details about the time or location change, we will post on Piazza.
* We will post a link to the notes and slides from the review session on Piazza.
* Bring a pencil and eraser to the exam. No bluebook/scantron.


# Review


# Questions:

* Q: If we want to extract a certain part of a string using negative indexing, what kind of format should we use?
  * A: A similar way, using the same logic. Just remember that the last number in the index is NOT included.
  ```python
  alpha = "abcdefghi"
  >>> alpha[-9:-7]
  "ab"
  ```
  As a shortcut if you don’t want to count the characters, use the length of the string provided by the `len` function!
  ```python
  alpha = "abcdefghi"
  >>> alpha[-len(alpha):-7]
  "ab"
  ```
  
* Q: Does capitalization matter when you compare strings?
  * A: Yes! `'y'` is not the same as `'Y'`
  
* Q: Do you use the `return` in the `hello()` function because of the `if`/`else` conditional??
  * A: No. `return`  vs `print` has nothing to do with the conditional of the function. We used `return` because the instructions specified to `return` rather than just `print`.

# Using Conditionals

Example:
```python

raining = input("is it raining? [y/n] ")

if (raining == 'y')
    print("It is raining")
    
elif (raining == 'n'):
    print('it is not raining')

else:
    print("not an option")
    
```

if you wanted to be able to use other inputs (e.g., `'y' 'yes' 'Y'`) to be able to output "It is raining", 
you would do so by changing the comparison in the conditional like this:

```python

if (raining == 'y' or raining == 'Y' or raining == 'yes'):
    print("It is raining")
    
```

Q: could we get around this by putting all possible conditionals in a list or something and then use an in statement???
A: Yes!

```python

if raining in ('y','Y','yes'):
    print("It is raining")
    
```

Q: 

We posted a follow-up about it on Piazza: <https://piazza.com/class/k54kv5vmxdu67o?cid=41>.

