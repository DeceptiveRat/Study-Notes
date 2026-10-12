In C, macros are preprocessor directives that provide a way to define reusable code snippets, constants, or conditional code compilation based on specific conditions. They are defined with `#define` statements, which tell the preprocessor to replace occurrences of a macro name with the specified code before actual compilation. Here’s a breakdown of various aspects of macros, including macro functions, conditional macros, and some advanced uses.

### Basic Macros with `#define`

A basic macro in C is defined with `#define`, which associates a name with a piece of text or code. For example:
```c
#define PI 3.14159
#define MAX_SIZE 100
```

These macros are simply constants. When the code is compiled, every occurrence of `PI` is replaced with `3.14159`, and `MAX_SIZE` with `100`.

### Macro Functions

Macros can also be used to define function-like constructs. Macro functions are written in the same way as regular macros but take parameters:
```c
#define SQUARE(x) ((x) * (x))
#define MAX(a, b) ((a) > (b) ? (a) : (b))
```

However, macro functions don’t check for types and may lead to unexpected behavior if not carefully written due to a lack of scoping and type-checking. For instance, in `SQUARE(x)`, `x` is evaluated twice, which can have unintended effects if `x` is an expression with side effects (e.g., `SQUARE(x++)`).

### Conditional Compilation Macros

Conditional compilation macros allow code to be compiled only if certain conditions are met. This is particularly useful for ensuring compatibility across different platforms or compilers. Commonly used directives include `#ifdef`, `#ifndef`, `#if`, `#else`, `#elif`, and `#endif`.

Here’s an example:
```c
#ifdef DEBUG
#define DEBUG_PRINT(x) printf("Debug: %s\n", x)
#else
#define DEBUG_PRINT(x)  // Empty statement, does nothing in release mode
#endif
```

In this case, if `DEBUG` is defined (e.g., through `#define DEBUG`), `DEBUG_PRINT` will print debugging information; otherwise, `DEBUG_PRINT` does nothing.

### Advanced Use of `#ifdef` and `__attribute__`

In the example you provided:
```c
#ifdef __GNUC__
#define NORETURN __attribute__ ((__noreturn__))
#else
#define NORETURN
#endif
```

This checks if the code is being compiled with GCC (GNU Compiler Collection), identified by the predefined macro `__GNUC__`. If `__GNUC__` is defined, the macro `NORETURN` is defined as `__attribute__ ((__noreturn__))`. Otherwise, `NORETURN` is defined as empty. 

#### `__attribute__((__noreturn__))`
This is a GCC-specific attribute that tells the compiler that a function will not return. When applied to a function, it helps the compiler optimize code by understanding that this function is terminal, meaning it will terminate the program or otherwise not return control to the calling function. This attribute is often used with functions like `exit()` or `abort()`, which do not return.

### Using `#ifdef` with Platform-Dependent Code

The `#ifdef` directive can be useful for conditional compilation across different platforms. For instance:
```c
#ifdef _WIN32
#define OS_NAME "Windows"
#elif defined(__linux__)
#define OS_NAME "Linux"
#elif defined(__APPLE__)
#define OS_NAME "macOS"
#else
#define OS_NAME "Unknown"
#endif
```

This macro defines the string `OS_NAME` based on the operating system being used. `_WIN32`, `__linux__`, and `__APPLE__` are predefined macros for Windows, Linux, and macOS, respectively.

### Other Useful Macros

1. **`#ifndef` and `#define`**: These are often used in header guards to prevent multiple inclusions of the same file:
   ```c
   #ifndef MY_HEADER_H
   #define MY_HEADER_H

   // Content of the header file

   #endif
   ```

2. **`__LINE__` and `__FILE__`**: These predefined macros expand to the current line number and file name in the source code. They’re useful for debugging:
   ```c
   #define DEBUG_LOG(msg) printf("DEBUG: %s:%d: %s\n", __FILE__, __LINE__, msg)
   ```

3. **Token-Pasting (`##`)**: This allows you to concatenate tokens in a macro, which is useful for generating variable names dynamically:
   ```c
   #define MAKE_VAR(name, num) name##num
   int MAKE_VAR(foo, 1) = 10;  // Expands to: int foo1 = 10;
   ```

4. **Stringification (`#`)**: This turns the argument of a macro into a string:
   ```c
   #define STRINGIFY(x) #x
   printf(STRINGIFY(Hello World));  // Expands to: printf("Hello World");
   ```

### Summary of Pros and Cons of Macros

#### Pros:
- Can improve performance, as macros are inlined directly in the code.
- Provide flexibility in conditional compilation.
- Useful for constants and platform/compiler-specific functionality.

#### Cons:
- Lack type safety.
- Hard to debug since errors in macros are not always obvious.
- Code can become difficult to read or maintain, especially with complex macro functions.

Macros are a powerful feature of C, but because they can introduce subtle bugs and unexpected behavior, it's often best to use `const`, `inline` functions, and `enum` where possible instead of macros, as these alternatives provide type safety and are generally easier to debug.