1. macros

```c
#ifdef DEBUG 
	#define DEBUG_PRINT(fmt, ...) \
		do { if (debug_mode) printf(fmt, ##__VA_ARGS__); } while(0)
	#define DEBUG_EXEC(code) \
		do { if (debug_mode) { code; } } while(0)
#else
	#define DEBUG_PRINT(fmt, ...)
	#define DEBUG_EXEC(code)
#endif

DEBUG_PRINT("Starting game number[%d]:\n", i);
DEBUG_EXEC(printMatrix(current_state));
```

- can choose to print if debug_mode
- goes away completely if DEBUG is not compiled with -DDEBUG