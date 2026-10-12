can be checked with the following command:

```sh
cat /proc/sys/kernel/randomize_va_space
```

- 0: ASLR disabled
- 1: stack, library, vdso, etc layout randomized
- 2: 1 + region assigned by brk

features:
- the lower 12 bits of libc_base and printf() are not changed (it's the size of the page)
- address difference between libc_base and printf() is always the same

example:
$ ./addr
buf_stack addr: 0x7ffe4c661f90
buf_heap addr: 0x176d260
libc_base addr: 0x7ffad9e1b000
printf addr: 0x7ffad9e7ff00
main addr: 0x400667
$ ./addr
buf_stack addr: 0x7ffcf2386d80
buf_heap addr: 0x840260
libc_base addr: 0x7fed2664b000
printf addr: 0x7fed266aff00
main addr: 0x400667