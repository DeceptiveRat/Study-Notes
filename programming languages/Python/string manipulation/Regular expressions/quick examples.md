- find matches and save to a file

```sh
#!/bin/python3 

import re

with open('output.txt', 'r', encoding='utf-8') as file:
        content = file.read()

# Find all strings that end with "円"
matches = re.findall(r'\b\S+円', content)

# Write the matches to a new file
with open('trimmed.txt', 'w', encoding='utf-8') as output:
        output.write('\n'.join(matches))
```


- match IP address - [1]

```python3
user = re.search(r"\b(?:[0-9]{1,3}\.){3}[0-9]{1,3}\b", line)
```


- remove only part of match

```python3
line = re.sub(r"^(\d{1,2}/\d{1,2}/\d{1,2}, \d{1,2}:\d{2}):\d{2}", r"\1", line)
# 9/20/24, 23:31:23 ~~~ => 9/20/24, 23:31 ~~~
```


- find all matches of regex - [2]

```python3
result = re.findall(r"(\[?[0-9]{1,2}/[0-9]{1,2}/[0-9]{1,2}.*?)(?=\[?[0-9]{1,2}/[0-9]{1,2}/[0-9]{1,2}.*?|$)", line)
```


- greedy vs non-greedy - [3]

```python3
# greedy
text = re.sub(r" (\(.*\))", r"\1", text)
# matches first ( with last )

# non-greedy
text = re.sub(r" (\(.*?\))", r"\1", text)
# matches first ( with first )
```


- matching binary data

```python3
    pattern_bytes = b'\x03\x00{7}.{3}'
    pattern = re.compile(pattern_bytes, re.DOTALL)
```
