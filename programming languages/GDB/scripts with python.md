# - custom command

```python3
import gdb 
 
class printDPArray(gdb.Command): 
	def __init__(self): 
		super(printDPArray, self).__init__("printDP", gdb.COMMAND_USER) 
 
	def invoke(self, args, from_tty): 
		for i in range(6): 
			for j in range(6): 
				dpVal=gdb.parse_and_eval("dp["+str(i)+"]["+str(j)+"]") 
				print(str(dpVal) + " ") 
			print("\n") 
 
printDPArray()
```


- __init__ is called when it is constructed. Use format like that
- invoke is called when it is invoked.
- invoke gets 3 arguments so even if they aren't used, take them


```python3
import gdb

class printItemlist(gdb.Command):
	def __init__(self):
		super(printItemlist, self).__init__("printItemlist", gdb.COMMAND_USER)

	def invoke(self, args, from_tty):
		gdb.execute("set $currentPtr = *itemHead->nextItem")

		for i in range(int(args[0])):
			print(f"printing item {i}...")
			val = gdb.parse_and_eval("$currentPtr.item->x")
			print(f'x: {val}')
			val = gdb.parse_and_eval("$currentPtr.item->y")
			print(f'y: {val}')
			val = gdb.parse_and_eval("$currentPtr.item->z")
			print(f'z: {val}')
			val = gdb.parse_and_eval("$currentPtr.item->weight")
			print(f'weight: {val}')

class printBaglist(gdb.Command):
	def __init__(self):
		super(printBaglist, self).__init__("printBaglist", gdb.COMMAND_USER)

	def invoke(self, args, from_tty):
		gdb.execute("set $currentPtr = *bagHead->nextBag")

		for i in range(int(args[0])):
			print(f"printing bag {i}...")
			val = gdb.parse_and_eval("$currentPtr.bag->x")

printItemlist()
printBaglist()
```


# - hook

```python3
import gdb

def printPathTaken():
	for i in range(6):
		val = gdb.parse_and_eval("pathTaken["+str(i)+"]")
		print(val, end="\t")
	print()

gdb.events.before_prompt.connect(printPathTaken)

```
