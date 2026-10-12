1. implicit rules
- n.o is automatically made from n.c with command: 

```makefile
$(CC) -c $(CPPFLAGS) $(CFLAGS) $^ -o $@
```

- n.o is automatically made from n.cc or n.cpp with command:

```makefile
$(CXX) -c $(CPPFLAGS) $(CXXFLAGS) $^ -o $@
```

- n is made automatically from n.o by running command:

```makefile
$(CC) $(LDFLAGS) $^ $(LOADLIBES) $(LDLIBS) -o $@
```

- important variables used:
   - CC: C compiler
   - CXX: C++ compiler
   - CFLAGS: flags for C compiler
   - CXXFLAGS: flags for C++ compiler
   - CPPFLAGS: flags for C preprocessor
   - LDFLAGS: linker flags

```makefile
CC = gcc # Flag for implicit rules
CFLAGS = -g # Flag for implicit rules. Turn on debug info

# Implicit rule #1: blah is built via the C linker implicit rule
# Implicit rule #2: blah.o is built via the C compilation implicit rule, because blah.c exists
blah: blah.o

blah.c:
	echo "int main() { return 0; }" > blah.c

clean:
	rm -f blah*
```
