1. create subprocess and wait for finish

```python3
ans = subprocess.call(["python", "--version"])
```


2. create subprocess without waiting for it to finish

```python3
ans = subprocess.Popen(["python", "--version"])
```


3. make subprocess die with parent

```python3
libc = ctypes.CDLL("libc.so.6")
def preexec_fn():
	libc.prctl(1, signal.SIGTERM)

preprocess_ans = subprocess.Popen(["python3", "--version"], preexec_fn = preexec_fn)
```


4. subprocess with stdin tied to pipeline

```python3
process = subprocess.Popen(ffmpeg_command, stdin=subprocess.PIPE)
process.stdin.close()
process.wait()
```


reference:
- GeeksForGeeks - python subprocess: <https://www.geeksforgeeks.org/python/python-subprocess-module/>