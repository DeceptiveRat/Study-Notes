## 1. opening
1.1. open()
- arguments:
   - file name
   - mode
      - r
      - w
      - a
      - r+
      - *b
   - encoding
- example:
f = open('workfile', 'w', encoding="utf-8")
- it is recommended to use "with" keyword

```python3
with open('workfile', encoding="utf-8") as f:
    read_data = f.read()
```


- it is possible to loop over file object

```python3
for line in f:
    print(line, end='')
```


## 2. reading
2.1. read()
- read entire file
- usage:
f.read(20)

2.2. readline()
- reads single line

reference:
<https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files>