- placeholder: %[flags][width][.precision]type 

```python3
# Python program showing how to use string modulo operator(%)

print("Geeks : %2d, Portal : %5.2f" % (1, 05.333)) 

print("Total students : %3d, Boys : %2d" % (240, 120))   # print integer value

print("%7.3o" % (25))   # print octal value

print("%10.3E" % (356.08977))   # print exponential value
```

output:
Geeks :  1, Portal : 5.33
Total students : 240, Boys : 120
    031
3.561E+02

- zfill: pad strings with 0, right justified
- {[variable name]:[< or > for alignment][size]}

```python3
print(f"{IP:16}: {count:4}")
""" output
83.149.9.216    :   23
24.236.252.67   :    1
93.114.45.13    :    6
"""
```
