Here’s a detailed explanation of your questions:

---

### **1. Difference Between `$default=""` and `default=""`**

- **`$default=""`:**
  - This tries to **set the value of the variable whose name is the current value of `default`** to an empty string.
  - For example:
    ```bash
    default="myvar"
    $default="value"  # Equivalent to myvar="value"
    ```
  - It’s incorrect syntax for simply resetting `default`. 

- **`default=""`:**
  - This sets the variable `default` itself to an empty string. This is the correct syntax for initializing or clearing a variable in Bash.

---

### **2. Can `$1` and `$2` Contain Spaces?**

Yes, **arguments can contain spaces** if they are **quoted** when passed to the script. For example:

```bash
./myscript.sh "my file name" "extra flag"
```

- `$1` will contain `"my file name"` (including the spaces), and `$2` will contain `"extra flag"`. 
- Without quotes, Bash interprets spaces as argument separators. For example:
  ```bash
  ./myscript.sh my file name extra flag
  ```
  Here, `$1="my"`, `$2="file"`, `$3="name"`, and so on.

---

### **3. Why Are Quotes Needed in `default="$default $i"`?**

Quoting prevents issues with **word splitting** and **special characters**.

- Without quotes:
  ```bash
  default=$default $i
  ```
  Bash interprets this as **two separate commands**:
  - `default=$default` (assignment)
  - `$i` (an attempted command execution, which would fail if `$i` isn’t an actual command).

- With quotes:
  ```bash
  default="$default $i"
  ```
  - Bash treats `$default $i` as a **single string** and assigns it to `default`.
  - This also ensures any spaces or special characters in `$i` are preserved in the value of `default`.

Example:
```bash
i="value with spaces"
default="existing"
default="$default $i"
echo "$default"
# Output: existing value with spaces
```

Without quotes, spaces in `$i` would cause word splitting and result in unexpected behavior.

---

### **4. Why Is `bash -c "$default"` Safer Than `eval "$default"`?**

- **`eval "$default"`:**
  - Directly interprets the string as Bash code and executes it.
  - **Risk**: If `default` contains malicious code (e.g., `rm -rf /`), it will be executed.
  - Example of an exploit:
    ```bash
    echo 'ls; rm -rf /' > default.txt
    ./myscript.sh default
    # This would delete your root directory.
    ```

- **`bash -c "$default"`:**
  - Launches a **new Bash shell** to execute the string as a command.
  - Slightly safer because it isolates the execution to a child process. If errors occur or if the string fails, they don’t directly affect the parent shell.
  - **Still risky** if the input is untrusted, but it limits the scope of the potential damage.

### How to Make It Even Safer:
Instead of executing arbitrary commands from `default.txt`, validate the input or use a predefined list of allowed commands. For example:

```bash
if [[ "$default" == "allowed_command" ]]; then
    bash -c "$default"
else
    echo "Invalid command."
fi
```

---

### Summary of Key Points:
- **`default=""`** sets the variable; `$default=""` is incorrect for this purpose.
- Arguments like `$1` and `$2` **can** contain spaces if passed with quotes.
- Quotes around `"$default $i"` prevent word splitting and preserve the integrity of the value.
- `bash -c` is safer than `eval` but still risky for unvalidated inputs. Always validate before executing commands.