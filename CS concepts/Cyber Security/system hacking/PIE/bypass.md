## 1. obtain code base
similar to obtaining base address of library

## 2. partial overwrite
address of code region is always the same in lower 12 bits. If the difference in address is less that 1 byte, we can just overwrite it. 