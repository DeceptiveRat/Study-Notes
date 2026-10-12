RELocation Read Only (RELRO) removes write permissions on data segments where they are not needed

## 1. partial RELRO
.got.plt , .data, .bss have write permission

## 2. full RELRO
.data, .bss have write permission

with full RELRO, library functions are all bound when the binary is loaded, so GOT doesn't have write access