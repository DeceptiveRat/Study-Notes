1. use nasm to create .o file

```sh
nasm code.asm -f elf64 -o code.o
```


2. objcopy to create .bin file

```sh
objcopy code.o --dump-section .text=code.bin
```


3. xxd to get bytes

```sh
xxd -p code.bin
```


4. awk can be used to format the output


```plain-text
xxd -p shellcode.bin | awk '{for(i=1;i<length($0);i+=2) printf "\\x%s", substr($0, i, 2); printf "\n";}'
```
