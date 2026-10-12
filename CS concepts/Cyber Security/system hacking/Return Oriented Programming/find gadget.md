# 1. useful gadgets:
- pop %rdi; ret (5FC3)

(use online websites for quick disassembly: <https://defuse.ca/online-x86-assembler.htm#disassembly>)
# 2. methods
- gdb find command

```plain-text
find <start address>, <end address>, <hex>, <hex2> ...
```


- objdump

```plain-text
objdump ./binary | grep <hex>
```


