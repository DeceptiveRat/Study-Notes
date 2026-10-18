1. redirection operator
- print DATA > output file

2. append operator
- print DATA >> output file

3. pipe
- print items | command

4. two way communication

```plain-text
BEGIN {
    cmd = "tr [a-z] [A-Z]" # Command to convert lowercase letters to uppercase
    print "hello, world !!!" |& cmd # Send input "hello, world !!!" to `tr` command via two-way communication
    close(cmd, "to") # Close the input stream (write stream) to `tr`

    cmd |& getline out # Read output from `tr` command into variable `out`
    print out # Print the transformed output
    close(cmd) # Close the communication with `tr`
}
```
