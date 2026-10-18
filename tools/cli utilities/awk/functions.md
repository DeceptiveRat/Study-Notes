# Arithmetic functions
1. atan2(y,x)
returns arctangent of (y/x) in radians
2. cos(expr)
3. exp(expr)
returns the exponential value of expr
4. int(expr)
truncates expr to an integer
5. log(expr)
returns the natural logarithm of a variable
6. rand
returns a random float between 0 and N
7. sin(expr)
8. sqrt
9. srand([expr])
generates random value using seed. If expr isn't provided, use time of day

# String functions
1. asort(arr[,d[,how]])
sort arr
2. asorti(arr[,d[,how]])
3. gsub(regex, sub, string)
replace every occurrence of regex with sub. string is optional with a default of $0
4. index(str, sub)
checks if sub is in str. If so, return start of sub
5. length(str)
6. match(str, regex)
returns index of first longest match of regex in str
7. split(str, arr, regex)
splits str into fields by regex and store in arr. If regex is omitted, FS is used
8. printf(format, expr-list)
9. strtonum(str)
leading 0 => octal, leading 0x => hexadecimal
10. sub(regex, sub, string)
replaces first occurrence of regex with sub
11. substr(str, start, l)
return substring in str starting at start with length l
12. tolower(str)
13. toupper(str)

# Time functions
1. systime
returns current time of day as number of seconds since the Epoch
2. mktime(datespec)
converts datespec string into a timestamp of the same form as returned by systime. datespec: YYYY MM DD HH MM SS
3. strftime([format [, timestamp[, utc-flag]]])
formats timestamps according to specification in format

```plain-text
awk 'BEGIN {
	print strftime("Time = %m/%d/%Y %H:%M:%S", systime())
}'
```

prints
Time = 12/14/2014 22:08:42

# Bit manipulation functions
1. and
2. compl
3. lshift
4. rshift
5. or
6. xor

# ETC functions
1. close(expr)
closes file of pipe
2. delete
delete an element from an array
3. exit(expr)
stops execution of a script. Accepts optional expr which is AWK's return value
4. fflush([output-expr])
flushes buffer associated with open output file or pipe
5. getline
get next line
6. next
cause current processing to stop. Starts again with next line
7. nextfile
cause current processing to stop. Starts again with next file
8. return
used within user defined function to return value
9. system
execute command and return exit status

# User defined functions
syntax:

```plain-text
function function_name(argument1, argument2, ...)
{
	function body
}
```
