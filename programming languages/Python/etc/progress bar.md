
```python3
def progress_bar(iteration, total, length=150):
	# since indices start with 0
	iteration += 1
	percent = f"{100*(iteration/float(total)):.1f}"
	filled_length = int(length * iteration // total)
	bar = "[" + "="*filled_length + " " * (length - filled_length) + "]"
	sys.stdout.write(f'\r{bar}\t{percent}% ({iteration}/{total}) complete')
	if iteration == total:
		print()
	sys.stdout.flush()
```
