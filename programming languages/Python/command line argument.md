
```python3
import sys
print ('argument list', sys.argv)
name = sys.argv[1]
print ("Hello {}. How are you?".format(name))
```



```python3
#!/bin/python3 

import sys
import getopt

def usage():
	print("usage:", sys.argv[0])
	print("options:")
	print("-h: display this help screen")
	print("-r <log name>: name of log")
	print("-t (optinal): when testing")

try:
	opts, args = getopt.getopt(sys.argv[1:], "hr:t")
except getopt.GetoptError as err:
	print(err)
	usage()
	sys.exit(2)

for option, argument in opts:
	if option == "-h":
		usage()
		sys.exit()
	elif option == "-r":
		file_name = argument 
	elif option == "-t":
		testing = True
	else:
		assert False, "unhandled option"
```


reference:
<https://www.tutorialspoint.com/python/python_command_line_arguments.htm>