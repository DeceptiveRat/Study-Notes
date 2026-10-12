1. basics
- bt: stack frame
- start (s): start from beginning
- run (r): run from beginning until breakpoint
- break (b): set breakpoint

```sh
(gdb) b <function name or line number>
(gdb) b 114 if i==99
(gdb) b common.c:27
```

- x: view address

```sh
(gdb) x/9xb <variable name or address>
0x7fffffffd7a6: 0x01    0xff    0x01    0xff    0x01    0xff    0x00    0x01
0x7fffffffd7ae: 0x00
(gdb) x/9c <variable name or address>
0x7fffffffd7a6: 1 '\001'        -1 '\377'       1 '\001'        -1 '\377'       1 '\001'        -1 '\377'       0 '\000'        1 '\001'
0x7fffffffd7ae: 0 '\000'
(gdb) x/9d 0x7fffffffd7a6
0x7fffffffd7a6: 1       -1      1       -1      1       -1      0       1
0x7fffffffd7ae: 0
```

- finish: execute until stack frame return
- 