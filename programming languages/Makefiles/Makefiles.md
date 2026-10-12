Rule:

```makefile
targets: prerequisites
	command
	command
	command 
```

- *targets* are file names. Typically one per rule
- *commands* are steps used to make the target(s). Start with a tab character
- *prerequisites* are also file names. These files need to exist before the commands are run. Also called dependencies

## The essence of Make

```makefile
hello:
	echo "Hello, World"
	echo "This line will print if the file hello does not exist"
```

Typically, when a target is run, the commands will create a file with the same name as the target.




```c
// blah.c
int main() {return 0;}
```

```makefile
# Makefile
blah:
	cc blah.c -o blah
```

When there is no argument to the make command, the first target is run. 



```makefile
# Makefile
blah: blah.c
	cc blah.c -o blah
```

When we run make:
- the default(first) target is selected
- will run only if blah doesn't exist, or blah.c is newer than blah


```makefile
# Makefile
blah: blah.o
	cc blah.o -o blah # Runs third

blah.o: blah.c
	cc -c blah.c -o blah.o # Runs second

# In case blah.c doesn't exist
blah.c:
	echo "int main() { return 0; }" > blah.c # Runs first
```

- Make selects the target **blah**
- **blah** requires **blah.o** so make searches for the **blah.o** target
- **blah.o** requires **blah.c** so make searches for the **blah.c** target
- **blah.c** requires no dependencies so it is run
- command for **blah.o** is then run since the dependencies are met
- command for **blah** is then run since the dependencies are met


```makefile
# Makefile
some_file: other_file
	echo "this will always run, and second"
	touch some_file

other_file:
	echo "this will always run, and first"
```

This will always run both targets

## Make clean



```makefile
# Makefile
some_file:
	touch some_file

clean:
	rm -f some_file
```
## Variables
Variables can only be strings

Typically := is used, but = works, too

```makefile
# Makefile
files := file1 file1
some_file: $(files)
	echo "look at this variable: " $(files)
	touch some_file

file1:
	touch file1

file2:
	touch file2

clean:
rm -f file1 file2 some_file
```


Single or double quotes have no meaning to Make. However they are useful to shell/bash and you need them in commands like printf

```makefile
# Makefile
a := one two # a is set to the string "one two"
b := 'one two' # not recommended. b is set to the string "'one two'"
all:
	printf '$a'
	printf $b
```

The two commands behave the same



# Targets

```makefile
# Makefile
x := dude

all:
	echo $(x)
	echo ${x}
	
	echo $x # bad practice, but works
```



```makefile
# Makefile
all: one two three

one:
	touch one
two:
	touch two
three:
	touch three

clean:
	rm -f one two three
```
## Multiple targets

```makefile
# Makefile
all: f1.o f2.o

f1.o f2.o:
	echo $a

# equivalent to f1.o:	echo f1.o f2.o:	echo f2.o
```



---
resources:
<https://makefiletutorial.com/>