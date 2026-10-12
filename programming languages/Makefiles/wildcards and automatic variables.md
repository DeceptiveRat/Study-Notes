1. * wildcard
- searches filesystem for matching file name
- should wrap in wildcard function

```makefile
# Print out file information about every .c file
print: $(wildcard *.c)
	ls -la  $?
```

- may be used in target, prerequisites, or in wildcard function
- can't be used in a variable definition
- it's left as is when no matches

```makefile
thing_wrong := *.o # Don't do this! '*' will not get expanded
thing_right := $(wildcard *.o)

all: one two three four

# Fails, because $(thing_wrong) is the string "*.o"
one: $(thing_wrong)

# Stays as *.o if there are no files that match this pattern :(
two: *.o 

# Works as you would expect! In this case, it does nothing.
three: $(thing_right)

# Same as rule three
four: $(wildcard *.o)
```


2. % wildcard
- matching mode: matches one or more character in string (called stem)
- replacing mode: takes stem matched and replaces string
- most often used in rule definitions and some specific functions

3. automatic variables

```makefile
hey: one two
	# Outputs "hey", since this is the target name
	echo $@

	# Outputs all prerequisites newer than the target
	echo $?

	# Outputs all prerequisites
	echo $^

	# Outputs the first prerequisite
	echo $<

	touch hey

one:
	touch one

two:
	touch two

clean:
	rm -f hey one two
```


reference: 
- <https://makefiletutorial.com/>