Exponents can be calculated with ‘**’

Division is done with ‘/’ like C but the result is not floored. To floor the result use ‘//’

Unlike Java, int cannot be concatenated with strings and must be converted to a string with ‘str(int)’

Functions are defined using ‘def <function name>():’

Boolean operations are done using and, or and xor not &, | and ^

### - if statements syntax:
if (condition):
	do
elif (condition):
	do
else:
	do
	
### - Lists:
- Have brackets []
- Starts with 0 index
- Can go through items on the list like [1:4]. This is inclusive for the left and exclusive for the right (1, 2, 3)
- [-1] accesses the last item in the index
- len() can be used to get the length of the list
- append() can be used to append item to the list
- pop() can be used to delete the last item from the list. Or put in an index to delete that item


### - Tuples:
- They do not change
- They use parenthesis ()
- brackets are used to access items using indices

### - Looping:
- for xx in xx:
- while condition:
- use indents instead of {}
- for x in range(y) would loop from x=0 ~ y-1

### - Importing modules
- import xx 
- sys and os are important to import for pentesting
- ‘from xx import xx’ can be used to import a part of a module not all of it
- ‘import xx as xx’ can be used to import with alias

### - Advanced strings
- split() can be used to split a string into lists. The base delimiter is space
- join() can be used to join lists together 
- \" allows you to have a double quote inside a string
- strip() removes additional blank spaces
- ‘print("My favorite movie is {}." .format(xx))’ - formatting can be used to format the print function

### - Dictionaries
- uses {}
- key/value pairs
- ‘dictionaryVar["new key"] = new value’ can add a new key/value pair into the dictionary
- ‘dictionaryVar.update({new key:new value})’ works too
- the key can be used as an “index” to update the value
- get() can be used to get the value using a key

### - Sockets
- AF_INET -> IPv4
- SOCK_STREAM -> TCP