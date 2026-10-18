# 1. syntax
1. BEGIN block

```plain-text
BEGIN {awk-commands}
```

- executed once on start up

2. BODY block

```plain-text
/pattern/ {awk-commands}
```

- executed on every line

3. END block

```plain-text
END {awk-commands}
```

- executes at end

# 2. options
1. -v
- assign value to variable

2. --dump-variables[=files]
- prints sorted list of global variables and their final values to a file

3. --lint[=fatal]
- enables checking of non-portable or dubious constructs
- when argument fatal is provided, it treats warning messages as errors

4. --posix
- turns on strict POSIX compatibility

5. --profile
- generates pretty-printed version of the program in file