You're right that saving the output to a text file and then reading it back is inefficient. Instead, you can use **`popen()`** to capture the output of a command executed by the system in C. The `popen()` function opens a process by creating a pipe, which allows you to read or write to the standard input or output of the command executed.

Here's an example that demonstrates how to capture the output of a command:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    char buffer[128];
    FILE *fp;

    // Open the command for reading
    fp = popen("ls -l", "r");
    if (fp == NULL) {
        printf("Failed to run command\n");
        exit(1);
    }

    // Read the output a line at a time - output it to standard output
    while (fgets(buffer, sizeof(buffer), fp) != NULL) {
        printf("%s", buffer);
    }

    // Close the pipe
    pclose(fp);

    return 0;
}
```

### How it works:
- **`popen()`** runs a command (`ls -l` in this case) and opens a pipe, which allows you to read the output as if you were reading from a file.
- You can then use **`fgets()`** to read the output line by line and handle it however you need.

This method is much more efficient than writing to and reading from a file!