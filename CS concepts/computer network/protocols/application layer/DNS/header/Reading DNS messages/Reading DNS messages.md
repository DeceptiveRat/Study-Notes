## 1. offset
- used to save space when repeated strings are used
- 2 bytes long
- first 2 bits are set to 11 (11xx xxxx are all valid)
- the next 14 bits are the offset from the beginning of the message

e.g.
0xC00C (1100000000001100):
start at byte 12
