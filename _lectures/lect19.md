---
num: Lec19
lecture_date: 2020-03-09
desc: Review
ready: true
---
* Algorithm: a solution to a problem, typically written in a human-understandable language(pseudocode)

* Pay attention to conditionals!

* You can find the list of the UCSB major/minor codes here: <https://registrar.sa.ucsb.edu/faculty-staff/resources-for-faculty-staff/major-minor-codes>

```python
ucsb_majors = {}
try:
  infile = open("major_codes.txt")
except:
  print("This files does not exist.")
  print("ERROR:", err)
else:
  for line infile:
    # line = line.split('\t').strip() #strip the white space
    line_to_write = line
    line = line.strip() # remove white psace
    line = line.splot('\t')
    # print("Key = ", line[0].strip()
    key = line[0].strip() # make sure there's no extra white space
    # ucsb_majors[key] = line[1]
    if ucsb_major.get(key) != None:
      print(line)
      ucsb_majors[key] = line[1]
      continue
    else:
      outfile.write(line_to_write)
    
    print(line)
infile.close()
outfile.close()
```
