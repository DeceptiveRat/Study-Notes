- String[x:y] 
- len(string)
- split()
- save formatted string to variable

```python3
# quick
i=42
filename = "frame_%06d.png" % i

# str.format()
filename = "frame_{:06d}.png".format(i)

# f-strings
filename = f"frame_{i:06d}.png"
```
