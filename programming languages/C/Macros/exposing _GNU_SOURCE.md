The error `storage size of 'hints' isn't known` happens when the compiler sees the *name* of the struct (`struct addrinfo`), but has not seen the actual *definition* (the list of variables inside it) by the time you try to create an instance of it.

Even though you included `<netdb.h>`, the definition is likely being hidden by your compiler settings.

### The Solution

You need to define a **Feature Test Macro** at the very top of your file, **before** any `#include` statements.

Add this line to the very top of your code:

```c
#define _POSIX_C_SOURCE 200112L

#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
// ... rest of your code
```

Alternatively, if you are on Linux and want access to all extensions, you can use:

```c
#define _GNU_SOURCE
```

-----

### Why is this happening?

This usually happens because of **compiler standards**.

1.  **Strict Standards:** If you compile with a flag like `-std=c99` or `-ansi`, the compiler tries to be strictly compliant with the ISO C standard.
2.  **POSIX vs. ISO C:** `struct addrinfo` is not part of the original ISO C language; it is part of the **POSIX** (Unix) standards.
3.  **Hidden Definitions:** When strict mode is on, the header files inside `<netdb.h>` check which standard you are using. If you don't explicitly say "I want POSIX features," the header file intentionally "hides" the `struct addrinfo` definition to ensure the code remains strictly ISO C compliant.

By defining `_POSIX_C_SOURCE 200112L` (or higher), you are telling the preprocessor: *"I know I am using C, but please also enable the definitions from the 2001 POSIX standard."*

### One other possibility

If the macro fix does not work, ensure that your compiler is actually targeting a system that supports `getaddrinfo`. However, on any modern Linux, macOS, or Unix system, the Feature Test Macro is the standard fix.

Would you like me to help you fill out the logic for `getaddrinfo` inside your `openSocket` function now that the struct is recognized?