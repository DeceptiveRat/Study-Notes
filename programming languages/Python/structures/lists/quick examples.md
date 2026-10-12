- sorting 2d list

```python3
# Source - https://stackoverflow.com/a/18564382
# Posted by dawg, modified by community. See post 'Timeline' for change history
# Retrieved 2026-06-14, License - CC BY-SA 3.0

>>> li=[[1, 0.23],
... [2, 0.39],
... [4, 0.31],
... [5, 0.27]]
>>> sorted(li,key=lambda l:l[1], reverse=True)
[[2, 0.39], [4, 0.31], [5, 0.27], [1, 0.23]]
```
