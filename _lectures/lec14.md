---
num: "lec14"
desc: "Exam 2 Review"
ready: true
lecture_date:  2019-11-14
reading: Chapters 2-6
---

# Code for the practice exam

### Q2.1 What is printed after this code executes?

```python
x=2
while(x>0):
     if (x%2 == 0):
         print(x)
     x=x-1
print(x)
```

### Q2.2 How would the output change if we modify the above code as follows?

```python
x=3
while(x>0):
    if (x%2 == 0):
        print(x)
x=x-1
print(x)
```


```python
def is_string1( text ):
    return (text == str)

def is_string2( text ):
    print (text == str)

text1 = is_string1("Hi")
text2 = is_string1(42)
text3 = is_string2("Bye")
text4 = is_string2(42)
print ("Compare text variables")
print (text1, " & ", text2)
print (text3, " & ", text4)
```

