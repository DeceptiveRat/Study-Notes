There are a few issues and improvements you can make to your Makefile to achieve what you want. Here's a breakdown:

1. **SOURCES and OBJECTS logic**: You are trying to generate object files based on a filename passed into the Makefile, but there's an issue with the way the pattern substitution is done in your `SOURCES` and `OBJECTS` variables.
   
2. **FILENAME logic**: You are trying to replace `.c` in `FILENAME` for `SOURCES` and `OBJECTS`, but you haven't defined `FILENAME` before using it. Additionally, the pattern for `SOURCES` is incorrect.

3. **Handling additional fixed files**: Since you're compiling the fixed object file (`fixedFile.o`) alongside the generated object file, you should add it to your linking step.

Here is a corrected version of your Makefile based on your needs:

### Corrected Makefile:

```makefile
CC=gcc
CFLAGS=-c -Wall
LDFLAGS=

# The file name changes but will default to 'DEFAULT' if not provided
FILENAME ?= DEFAULT

# The source file is based on FILENAME, and OBJECTS holds the corresponding .o file
SOURCES = $(FILENAME).c
OBJECTS = $(FILENAME).o

# The fixed file that always stays the same
FIXED_OBJECT = fixedFile.o

# The final executable name is based on the FILENAME
EXECUTABLE = $(FILENAME)

# The default target, which builds the executable
all: $(EXECUTABLE)

# Debug mode with extra flags
debug: CFLAGS += -DDEBUG -g
debug: $(EXECUTABLE)

# Debug mode without optimizations
debugNoOpt: CFLAGS += -DDEBUG -g -O0
debugNoOpt: $(EXECUTABLE)

# The rule to link the objects into the final executable
$(EXECUTABLE): $(OBJECTS) $(FIXED_OBJECT)
	$(CC) $(LDFLAGS) $(OBJECTS) $(FIXED_OBJECT) -o $@

# Rule to compile .c files into .o files
%.o: %.c
	$(CC) $(CFLAGS) $< -o $@

# Clean up object files and executables
clean:
	rm -f $(OBJECTS) $(EXECUTABLE)
```

### Explanation of Changes:

1. **`FILENAME ?= DEFAULT`**: This line ensures that if you don't provide a filename (e.g., by running `make FILENAME=myfile`), it will default to `DEFAULT`. You can override `FILENAME` when calling `make`.

2. **`SOURCES = $(FILENAME).c`**: This defines the source file as `FILENAME.c` so that `FILENAME` can be dynamic.

3. **`OBJECTS = $(FILENAME).o`**: This defines the object file to match the source file (`FILENAME.o`).

4. **`FIXED_OBJECT = fixedFile.o`**: This specifies the fixed object file that will always be part of the linking.

5. **Linking both `$(OBJECTS)` and `$(FIXED_OBJECT)`**: The rule for linking includes both the dynamically generated object file and the fixed object file when building the final executable.

6. **Pattern rule (`%.o: %.c`)**: This rule allows you to compile any `.c` file into its corresponding `.o` file, replacing the specific `.c.o:` rule.

### How to Use It:

- If you want to compile a file called `myfile.c` with the fixed object `fixedFile.o`, you can run:
  ```bash
  make FILENAME=myfile
  ```

This will generate:
1. `myfile.o` from `myfile.c`
2. Link `myfile.o` and `fixedFile.o` into an executable named `myfile`

