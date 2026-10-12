

In a bash script, you can read arguments passed to the script, store them in variables, and then compare them to strings using conditional statements. Here’s a quick guide to help you with comparisons in bash.

### 1. Reading Arguments in Bash
When you run a script with arguments, they are accessible as positional parameters:
- `$1` is the first argument, `$2` is the second, and so on.
- `$#` gives the number of arguments.
- `$@` represents all arguments as a list.

For example, if you run a script like this:
```bash
./script.sh apple
```
The value of `$1` will be `"apple"`.

### 2. Comparing Strings
To compare strings in bash, you can use the `if` statement with either `=` or `==` for equality, and `!=` for inequality.

#### Example
Here’s an example where we read the first argument and compare it to a string:

```bash
#!/bin/bash

# Check if at least one argument was passed
if [ $# -eq 0 ]; then
    echo "No argument provided."
    exit 1
fi

# Store the first argument in a variable
input="$1"

# Compare the argument to a specific string
if [ "$input" = "apple" ]; then
    echo "The input is apple."
elif [ "$input" = "banana" ]; then
    echo "The input is banana."
else
    echo "The input is something else."
fi
```

### Explanation
1. `[ "$input" = "apple" ]` checks if `input` is equal to `"apple"`.
   - Use single `=` for POSIX compatibility or `==` if you're using `[[ ]]` instead of `[ ]`.
2. Always put variables in quotes (`"$input"`) to handle cases where the variable might be empty or contain spaces.
3. `elif` lets you chain multiple conditions if you need to check for other values.

### Notes
- You can also check for inequality with `[ "$input" != "string" ]`.
- For integer comparisons, use `-eq`, `-ne`, `-lt`, `-le`, `-gt`, and `-ge`.

With this setup, your script can handle basic comparisons based on arguments passed at runtime!