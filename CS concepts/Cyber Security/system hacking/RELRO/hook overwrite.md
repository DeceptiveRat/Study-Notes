typical hooks for library functions: malloc hook, free hook

hooks are located in writable areas in libc.so, and thus, overwritable

* hooks have been removed from Glibc 2.34 *