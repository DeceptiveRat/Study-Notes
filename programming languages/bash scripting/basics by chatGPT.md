### Shell Scripting Basics

Shell scripting is a way to automate tasks in a Unix/Linux environment. A shell script is a text file containing a sequence of commands that are interpreted by a shell (like `bash`, `sh`, or `zsh`).

#### 1. **Creating a Shell Script**
- A shell script file typically has a `.sh` extension but that's not mandatory.
- The first line of any shell script is called the "shebang," and it specifies which interpreter to use. For a Bash script, it looks like this:
  
  ```bash
  #!/bin/bash
  ```

#### 2. **Running a Shell Script**
- To run a script:
  ```bash
  ./script_name.sh
  ```
- If the script doesn't have execute permissions, you can add them:
  ```bash
  chmod +x script_name.sh
  ```

#### 3. **Variables**
- Variables in shell scripts are created by simply assigning a value:
  
  ```bash
  #!/bin/bash
  name="Alice"
  echo "Hello, $name"
  ```

  This script will output: `Hello, Alice`.

#### 4. **User Input**
- You can prompt the user for input using `read`:
  
  ```bash
  #!/bin/bash
  echo "What is your name?"
  read name
  echo "Hello, $name"
  ```

#### 5. **Conditionals**
- Shell scripts support `if` statements to handle conditions:
  
  ```bash
  #!/bin/bash
  echo "Enter a number:"
  read num
  if [ $num -gt 10 ]; then
      echo "The number is greater than 10."
  else
      echo "The number is 10 or less."
  fi
  ```

  - **`-gt`** means "greater than," while other comparison operators include:
    - `-lt`: less than
    - `-eq`: equal to
    - `-ne`: not equal to

#### 6. **Loops**
- A `for` loop in shell scripting is used to iterate over a list or range:
  
  ```bash
  #!/bin/bash
  for i in 1 2 3 4 5; do
      echo "Iteration $i"
  done
  ```

- A `while` loop runs as long as a condition is true:
  
  ```bash
  #!/bin/bash
  count=1
  while [ $count -le 5 ]; do
      echo "Count: $count"
      count=$((count + 1))
  done
  ```

#### 7. **Functions**
- You can define reusable code blocks in shell scripts as functions:
  
  ```bash
  #!/bin/bash
  greet() {
      echo "Hello, $1!"
  }
  
  greet "Alice"
  greet "Bob"
  ```

  Here, `$1` represents the first argument passed to the function. This script will output:
  ```
  Hello, Alice!
  Hello, Bob!
  ```

#### 8. **Command Substitution**
- You can store the output of a command into a variable:
  
  ```bash
  #!/bin/bash
  current_date=$(date)
  echo "Today's date is: $current_date"
  ```

#### 9. **File Operations**
- Reading a file line-by-line can be done using a `while` loop:
  
  ```bash
  #!/bin/bash
  while IFS= read -r line; do
      echo "$line"
  done < "file.txt"
  ```

#### 10. **Exit Status**
- Every command returns an exit status. `0` means success, and any other number indicates an error. You can check this using `$?`:
  
  ```bash
  #!/bin/bash
  ls
  if [ $? -eq 0 ]; then
      echo "Command executed successfully"
  else
      echo "Command failed"
  fi
  ```

### Example Shell Script

Here’s a simple script that combines user input, conditionals, and loops:

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "How many times should I greet you?"
read count

if [ $count -gt 0 ]; then
    for i in $(seq 1 $count); do
        echo "Hello, $name!"
    done
else
    echo "You entered an invalid number."
fi
```

This script will greet the user a number of times based on the input.